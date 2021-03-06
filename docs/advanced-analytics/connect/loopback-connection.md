---
title: SQL-Loopbackverbindung
description: Hier erfahren Sie, wie Sie mit einer Loopbackverbindung über ODBC eine Verbindung zurück zu SQL Server herstellen können, um Daten in einem über „sp_execute_external_script“ ausgeführten Python- oder R-Skript lesen oder schreiben können. Sie können diese Methode verwenden, wenn nicht die Möglichkeit besteht, die Argumente „InputDataSet“ und „OutputDataSet“ von „sp_execute_external_script“ zu verwenden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2019
ms.topic: conceptual
author: Aniruddh25
ms.author: anmunde
ms.reviewer: dphansen
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c7fa36db48a7912951f0232136945798caf6f7f7
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727601"
---
# <a name="loopback-connection-to-sql-server-from-a-python-or-r-script"></a>Loopbackverbindung zu SQL Server über ein Python- oder R-Skript
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Hier erfahren Sie, wie Sie mit einer Loopbackverbindung über [ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md) eine Verbindung zurück zu SQL Server herstellen können, um Daten in einem über `sp_execute_external_script` ausgeführten Python- oder R-Skript lesen oder schreiben können. Sie können diese Methode verwenden, wenn nicht die Möglichkeit besteht, die Argumente **InputDataSet** und **OutputDataSet** von `sp_execute_external_script` zu verwenden.

## <a name="connection-string"></a>Verbindungszeichenfolge

Wenn Sie eine Loopbackverbindung herstellen möchten, müssen Sie eine entsprechende Verbindungszeichenfolge verwenden. Der Name des [ODBC-Treibers](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md), die Serveradresse und der Name der Datenbank sind in der Regel obligatorische Argumente.

### <a name="connection-string-on-windows"></a>Verbindungszeichenfolge unter Windows

Bei SQL Server unter Windows kann im Python- oder R-Skript das Verbindungszeichenfolgenattribut **Trusted_Connection** zur Authentifizierung als der Benutzer, der „sp_execute_external_script“ ausgeführt hat, verwendet werden.

Im Folgenden finden Sie ein Beispiel für die Zeichenfolge einer Loopbackverbindung unter Windows:

``` 
"Driver=SQL Server;Server=.;Database=nameOfDatabase;Trusted_Connection=Yes;"
```

### <a name="connection-string-on-linux"></a>Verbindungszeichenfolge unter Linux

Bei SQL Server unter Linux müssen im Python- bzw. R-Skript die Attribute **ClientCertificate** und **ClientKey** des ODBC-Treibers zur Authentifizierung als der Benutzer, der `sp_execute_external_script` ausgeführt hat, verwendet werden. Hierfür ist die Verwendung der [aktuellen ODBC-Treiberversion](../../connect/odbc/download-odbc-driver-for-sql-server.md) 17.4.1.1 erforderlich.

Im Folgenden finden Sie ein Beispiel für die Zeichenfolge einer Loopbackverbindung unter Linux:

```
"Driver=ODBC Driver 17 for SQL Server;Server=fe80::8012:3df5:0:5db1%eth0;Database=nameOfDatabase;ClientCertificate=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitecert.pem;ClientKey=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitekey.pem;TrustServerCertificate=Yes;Trusted_Connection=no;Encrypt=Yes"
```

Serveradresse, Speicherort der Clientzertifikatdatei und Speicherort der Clientschlüsseldatei sind für jedes `sp_execute_external_script` spezifisch und können mithilfe der API **rx_get_sql_loopback_connection_string()** für Python bzw. **rxGetSqlLoopbackConnectionString()** für R abgerufen werden.

Weitere Informationen zu den Verbindungszeichenfolgenattributen finden Sie unter [Schlüsselwörter und Attribute von DNS- und Verbindungszeichenfolgen](https://docs.microsoft.com/sql/connect/odbc/dsn-connection-string-attribute?view=sql-server-linux-ver15#new-connection-string-keywords-and-connection-attributes) für Microsoft ODBC Driver for SQL Server.

## <a name="generate-connection-string-with-revoscalepy-for-python"></a>Generieren einer Verbindungszeichenfolge mit revoscalepy für Python

Sie können die API **rx_get_sql_loopback_connection_string()** in [revoscalepy](../python/ref-py-revoscalepy.md) verwenden, um eine entsprechende Verbindungszeichenfolge für eine Loopbackverbindung in einem Python-Skript zu generieren.

Dabei werden die folgenden Argumente akzeptiert:

| Argument | und Beschreibung |
|-|-|
| name_of_database | Name der Datenbank, mit der die Verbindung hergestellt wird |
| odbc_driver | Name des ODBC-Treibers |

### <a name="examples"></a>Beispiele

Beispiel für SQL Server unter Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="SQL Server", name_of_database="DBName")
print("Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Beispiel für SQL Server unter Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="ODBC Driver 17 for SQL Server",
                                                                   name_of_database="DBName")
print("Loopback Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="generate-connection-string-with-revoscaler-for-r"></a>Generieren einer Verbindungszeichenfolge mit RevoScaleR für R

Sie können die API **rxGetSqlLoopbackConnectionString()** in [RevoScaleR](../r/ref-r-revoscaler.md) verwenden, um eine entsprechende Verbindungszeichenfolge für eine Loopbackverbindung in einem R-Skript zu generieren.

Dabei werden die folgenden Argumente akzeptiert:

| Argument | und Beschreibung |
|-|-|
| nameOfDatabase | Name der Datenbank, mit der die Verbindung hergestellt wird |
| odbcDriver | Name des ODBC-Treibers |

### <a name="examples"></a>Beispiele

Beispiel für SQL Server unter Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <- rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", odbcDriver ="SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName",
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Beispiel für SQL Server unter Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <-  rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", 
                                                                  odbcDriver ="ODBC Driver 17 for SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName", 
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="next-steps"></a>Nächste Schritte

+ [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)
+ [revoscalepy](../python/ref-py-revoscalepy.md)
+ [RevoScaleR](../r/ref-r-revoscaler.md)
