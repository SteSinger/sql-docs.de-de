---
title: Typzuordnung mit PolyBase | Microsoft-Dokumentation
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: ''
ms.openlocfilehash: 34f6b61160b687fa6864a2660b632524188b922c
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71710466"
---
# <a name="type-mapping-with-polybase"></a>Typzuordnung mit PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Zuordnung zwischen externen PolyBase-Datenquellen und SQL Server. Sie können diese Informationen verwenden, um externe Tabellen mit dem Transact-SQL-Befehl [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md) richtig zu definieren.

## <a name="overview"></a>Übersicht

Beim Erstellen einer externen Tabelle mit PolyBase müssen die Spaltendefinitionen, einschließlich der Datentypen und die Anzahl der Spalten mit den Daten in externen Dateien übereinstimmen. Wenn ein Konflikt besteht, werden die Zeilen der Datei beim Abfragen der tatsächlichen Daten zurückgewiesen.  
  
Für externe Tabellen, die auf Dateien in externen Datenquellen verweisen, müssen die Spalten- und Typdefinitionen dem genauen Schema der externen Datei zugeordnet werden. Beim Definieren von Datentypen, die auf Daten verweisen, die in Hadoop/Hive gespeichert sind, verwenden Sie die folgenden Zuordnungen zwischen Datentypen von SQL und Hive und wandeln Sie den Typ in einen SQL-Datentyp um, wenn Sie daraus auswählen. Die Typen umfassen alle Versionen von Hive, sofern nicht anders angegeben.

> [!NOTE]  
> SQL Server unterstützt den Datenwert *unendlich* von Hive nicht in beliebigen Konvertierungen. PolyBase schlägt mit einem Datentypkonvertierungsfehler fehl.

## <a name="hadoop-type-mapping-reference"></a>Hadoop-Typzuordnungsverweis

| SQL-Datentyp | .NET-Datentyp            | Hive-Datentyp | Hadoop/Java-Datentyp | Kommentare                       |
| ------------- | ------------------------- | -------------- | --------------------- | ------------------------------ |
| TINYINT       | Byte                      | TINYINT        | ByteWritable          | Nur für unsignierte Zahlen.     |
| SMALLINT      | Int16                     | SMALLINT       | ShortWritable         |
| INT           | Int32                     | INT            | IntWritable           |
| BIGINT        | Int64                     | BIGINT         | LongWritable          |
| bit           | Boolean                   | boolean        | BooleanWritable       |
| FLOAT         | Double                    | double         | DoubleWritable        |
| REAL          | Single                    | FLOAT          | FloatWritable         |
| money         | Decimal                   | double         | DoubleWritable        |
| SMALLMONEY    | Decimal                   | double         | DoubleWritable        |
| NCHAR         | Zeichenfolge<br /><br /> Char[] | Zeichenfolge         | Varchar               |
| NVARCHAR      | Zeichenfolge<br /><br /> Char[] | Zeichenfolge         | Varchar               |
| char          | Zeichenfolge<br /><br /> Char[] | Zeichenfolge         | Varchar               |
| varchar       | Zeichenfolge<br /><br /> Char[] | Zeichenfolge         | Varchar               |
| BINARY        | Byte[]                    | BINARY         | BytesWritable         | Gilt für Hive 0.8 und höher. |
| varbinary     | Byte[]                    | BINARY         | BytesWritable         | Gilt für Hive 0.8 und höher. |
| date          | datetime                  | timestamp      | TimestampWritable     |
| smalldatetime | datetime                  | timestamp      | TimestampWritable     |
| datetime2     | datetime                  | timestamp      | TimestampWritable     |
| DATETIME      | datetime                  | timestamp      | TimestampWritable     |
| time          | TimeSpan                  | timestamp      | TimestampWritable     |
| Decimal       | Decimal                   | Decimal        | BigDecimalWritable    | Gilt für Hive 0.11 und höher. |

<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

## <a name="oracle-type-mapping-reference"></a>Oracle-Typzuordnungsverweis

| Oracle-Datentyp | SQL Server-Typ | 
| -------------    | --------------- |
|float             |float            |
|NUMBER            |Decimal          |
|LONG              |nvarchar         |
|BINARY_FLOAT      |Real             | 
|BINARY_DOUBLE     |float            | 
|CHAR              |Char             |
|VARCHAR2          |Varchar          | 
|NVARCHAR2         |nvarchar         | 
|RAW               |Varbinary        |
|LONG RAW          |Varbinary        | 
|BLOB              |Varbinary        |
|CLOB              |Varchar          |
|NCLOB             | nvarchar        | 
|ROWID             |Varchar          |
|UROWID            |Varchar          | 
|DATE              |Datetime2        |
|timestamp         |Datetime2        | 

**Typenkonflikt:** 

**Gleitkomma:** Oracle unterstützt eine Gleitkommagenauigkeit von 126, was niedriger ist als die von SQL-Server (53). Daher kann **Float (1-53)** direkt zugeordnet werden, aber darüber hinaus kommt es zu Datenverlust durch Abschneidung.

**Zeitstempel:** „Timestamp“ und „Timestamp with local timezone“ in Oracle unterstützen eine Genauigkeit in Sekundenbruchteilen von 9, während SQL Server bei „DateTime2“ nur eine Genauigkeit in Sekundenbruchteilen von 7 unterstützt. 




## <a name="mongodb-type-mapping"></a>MongoDB-Typzuordnung

| BSON-Datentyp     | SQL Server-Typ |
| ------------------ | --------------- |
| Double             | float           |
| Zeichenfolge             | nvarchar        |
| Binärdaten        | nvarchar        |
| ObjectID          | nvarchar        |
| Boolean            | bit             |
| date               | Datetime2       |
| 32-bit integer     | int             |
| Timestamp          | nvarchar        |
| 64-bit integer     | BigInt          |
|Decimal 128         | Decimal         | 
| DBPointer          | nvarchar        |
| Javascript         | nvarchar        |
| Max Key            | nvarchar        |
| Min Key            | nvarchar        |
| Symbol             | nvarchar        |
| Regular Expression | nvarchar        |
| Undefined/NULL     | nvarchar        |


MongoDB verwendet BSON-Dokumente zur Speicherung von Datensätzen. Im Gegensatz zu den vorherigen Szenarios weist BSON kein Schema auf und unterstützt das Einbetten von Dokumenten und Arrays in andere Dokumente. Dadurch ist der Benutzer flexibler. 


## <a name="teradata-type-mapping-reference"></a>Teradata-Typzuordnungsverweis

| Teradata-Datentyp | SQL Server-Typ | 
| -------------      | -------------   |
|INTEGER             |int              |
|SMALLINT            |SmallInt         |
|bigint              |BigInt           |
|BYTEINT             |SmallInt         |
|DEZIMAL             |Decimal          |
|GLEITKOMMAZAHL               |Decimal          |
|BYTE                |Binär (Binary)           |
|VARBYTE             |Varbinary        |
|BLOB                |varbinary        |
|CHAR                |Nchar            |
|CLOB                |nvarchar         |
|VARCHAR             |nvarchar         |
|Graphic             |Nchar            |
|JSON                |nvarchar         |
|VARGRAPHIC          |nvarchar         |
|DATE                |date             |
|timestamp           |Datetime2        |
|TIME                |Uhrzeit             |
|TIME WITH TIME ZONE |Uhrzeit             |
|TIMESTAMP WITH TIME ZONE|Uhrzeit         |

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Verwendung finden Sie im Transact-SQL-Referenzartikel für [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
