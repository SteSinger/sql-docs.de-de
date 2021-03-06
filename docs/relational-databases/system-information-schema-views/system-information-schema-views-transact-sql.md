---
title: System Informations Schema-Sichten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/30/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- information schema views
- schemas [SQL Server], information schema views
- metadata [SQL Server], views
- views [SQL Server], information schema
- system views [SQL Server], information schema
ms.assetid: 7e9f1dfe-27e9-40e7-8fc7-bfc5cae6be10
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9767c68f80c133a31c5ca33053731a399f1048db
ms.sourcegitcommit: c70a0e2c053c2583311fcfede6ab5f25df364de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670565"
---
# <a name="system-information-schema-views-transact-sql"></a>System Informations Schema-Sichten (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Eine Informationsschemasicht ist eine der Methoden, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Abrufen von Metadaten bereitstellt. Informationsschemasichten stellen eine interne, von den Systemtabellen unabhängige Darstellung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Metadaten bereit. Informationsschemasichten ermöglichen die einwandfreie Ausführung von Anwendungen, auch wenn an den zugrunde liegenden Systemtabellen erhebliche Änderungen vorgenommen wurden. Die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthaltenen Informationsschemasichten entsprechen der Definition des ISO-Standards für INFORMATION_SCHEMA.

> [!IMPORTANT]
> An Informationsschemasichten wurden einige Änderungen vorgenommen, wodurch die Abwärtskompatibilität nicht mehr gegeben ist. Diese Änderungen werden in den betreffenden Themen für die jeweiligen Sichten beschrieben.

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt eine dreiteilige Benennungskonvention beim Verweis auf den aktuellen Server. Der ISO-Standard unterstützt ebenfalls eine dreiteilige Benennungskonvention. Die Namen, die in den beiden Konventionen verwendet werden, sind jedoch unterschiedlich. Die Informationsschemasichten sind in einem speziellen Schema namens INFORMATION_SCHEMA definiert. Dieses Schema ist in jeder Datenbank enthalten. Jede Informationsschemasicht enthält die Metadaten für alle in der jeweiligen Datenbank gespeicherten Datenobjekte. In der folgenden Tabelle werden die Beziehungen zwischen den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Namen und den SQL-Standardnamen aufgeführt.

|SQL Server-Name|Entsprechender SQL-Standardname|
|---------------------|-----------------------------------------------|
|Datenbank|Katalog|
|Schema|Schema|
|Objekt|Objekt|
|benutzerdefinierter Datentyp|Domain|

Diese Namenzuordnungskonvention betrifft die folgenden ISO-kompatiblen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sichten.

|||
|-|-|
|[CHECK_CONSTRAINTS](../../relational-databases/system-information-schema-views/check-constraints-transact-sql.md)|[REFERENTIAL_CONSTRAINTS](../../relational-databases/system-information-schema-views/referential-constraints-transact-sql.md)|
|[COLUMN_DOMAIN_USAGE](../../relational-databases/system-information-schema-views/column-domain-usage-transact-sql.md)|[ROUTINES](../../relational-databases/system-information-schema-views/routines-transact-sql.md)|
|[COLUMN_PRIVILEGES](../../relational-databases/system-information-schema-views/column-privileges-transact-sql.md)|[ROUTINE_COLUMNS](../../relational-databases/system-information-schema-views/routine-columns-transact-sql.md)|
|[COLUMNS](../../relational-databases/system-information-schema-views/columns-transact-sql.md)|[SCHEMATA](../../relational-databases/system-information-schema-views/schemata-transact-sql.md)|
|[CONSTRAINT_COLUMN_USAGE](../../relational-databases/system-information-schema-views/constraint-column-usage-transact-sql.md)|[TABLE_CONSTRAINTS](../../relational-databases/system-information-schema-views/table-constraints-transact-sql.md)|
|[CONSTRAINT_TABLE_USAGE](../../relational-databases/system-information-schema-views/constraint-table-usage-transact-sql.md)|[TABLE_PRIVILEGES](../../relational-databases/system-information-schema-views/table-privileges-transact-sql.md)|
|[DOMAIN_CONSTRAINTS](../../relational-databases/system-information-schema-views/domain-constraints-transact-sql.md)|[TABLES](../../relational-databases/system-information-schema-views/tables-transact-sql.md)|
|[DOMAINS](../../relational-databases/system-information-schema-views/domains-transact-sql.md)|[VIEW_COLUMN_USAGE](../../relational-databases/system-information-schema-views/view-column-usage-transact-sql.md)|
|[KEY_COLUMN_USAGE](../../relational-databases/system-information-schema-views/key-column-usage-transact-sql.md)|[VIEW_TABLE_USAGE](../../relational-databases/system-information-schema-views/view-table-usage-transact-sql.md)|
|[PARAMETERS](../../relational-databases/system-information-schema-views/parameters-transact-sql.md)|[VIEWS](../../relational-databases/system-information-schema-views/views-transact-sql.md)|

Darüber hinaus enthalten einige Sichten Verweise auf verschiedene Klassen von Daten, z. B. Zeichendaten oder binäre Daten.

Wenn Sie auf die Informationsschemasichten verweisen, müssen Sie einen qualifizierten Namen verwenden, der den Namen des `INFORMATION_SCHEMA`-Schemas enthält. Zum Beispiel:

```sql
SELECT TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, COLUMN_DEFAULT
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = N'Product';
```

## <a name="see-also"></a>Siehe auch

- [System Sichten &#40;(Transact-SQL)&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)
- [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
- [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) 
