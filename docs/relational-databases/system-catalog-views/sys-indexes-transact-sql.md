---
title: sys. Indexes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.indexes
- indexes
- sys.indexes_TSQL
- indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.indexes catalog view
ms.assetid: 066bd9ac-6554-4297-88fe-d740de1f94a8
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3d4d307ea18127586ac46b0f6afb973ef62cf6ba
ms.sourcegitcommit: ede04340adbf085e668a2536d4f7114abba14a0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761479"
---
# <a name="sysindexes-transact-sql"></a>sys.indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile pro Index oder Heap eines tabellarischen Objekts, wie z. B. einer Tabelle, Sicht oder Tabellenwertfunktion.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**object_id**|**wartenden**|ID des Objekts, zu dem dieser Index gehört.|  
|**Benennen**|**sysname**|Der Name des Indexes. der **Name** ist nur innerhalb des Objekts eindeutig.<br /><br /> NULL = Heap|  
|**index_id**|**wartenden**|Die ID des Index. **index_id** ist nur innerhalb des-Objekts eindeutig.<br /><br /> 0 = Heap<br /><br /> 1 = Gruppierter Index<br /><br /> > 1 = Nicht gruppierter Index|  
|**Sorte**|**tinyint**|Typ des Index:<br /><br /> 0 = Heap<br /><br /> 1 = In einem Cluster gruppiert<br /><br /> 2 = Nicht gruppiert<br /><br /> 3 = XML<br /><br /> 4 = Räumlich<br /><br /> 5 = gruppierter columnstore--Index. **Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> 6 = nicht gruppierter columnstore--Index. **Gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.<br /><br /> 7 = nicht gruppierter Hashindex. **Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.|  
|**type_desc**|**nvarchar (60)**|Beschreibung des Typs des Index:<br /><br /> HEAP<br /><br /> CLUSTERED<br /><br /> NONCLUSTERED<br /><br /> XML<br /><br /> SPATIAL<br /><br /> Gruppierter columnstore: **gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> Nonclustered columnstore: **gilt für**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.<br /><br /> Nonclustered-Hash: nicht gruppierte Hash Indizes werden nur für Speicher optimierte Tabellen unterstützt. Die sys.hash_indexes-Sicht zeigt die aktuellen Hashindizes und Hasheigenschaften an. Weitere Informationen finden Sie unter [sys. hash_indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-hash-indexes-transact-sql.md). **Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.|  
|**is_unique**|**bit**|1 = Der Index ist eindeutig.<br /><br /> 0 = Der Index ist nicht eindeutig.<br /><br /> Immer 0 für gruppierte columnstore-Indizes.|  
|**data_space_id**|**wartenden**|ID des Datenspeicherplatzes für diesen Index. Der Datenspeicherplatz ist entweder eine Dateigruppe oder ein Partitionsschema.<br /><br /> 0 = **object_id** ist eine Tabellenwert Funktion oder ein Index im Arbeitsspeicher.|  
|**ignore_dup_key**|**trate**|1 = IGNORE_DUP_KEY ist ON.<br /><br /> 0 = IGNORE_DUP_KEY ist OFF.|  
|**is_primary_key**|**bit**|1 = Der Index ist Teil einer PRIMARY KEY-Einschränkung.<br /><br /> Immer 0 für gruppierte columnstore-Indizes.|  
|**is_unique_constraint**|**bit**|1 = Der Index ist Teil einer UNIQUE-Einschränkung.<br /><br /> Immer 0 für gruppierte columnstore-Indizes.|  
|**fill_factor**|**tinyint**|> 0 = FILLFACTOR-Prozentsatz, der beim Erstellen oder erneuten Erstellen des Indexes verwendet wurde.<br /><br /> 0 = Standardwert<br /><br /> Immer 0 für gruppierte columnstore-Indizes.|  
|**is_padded**|**trate**|1 = PADINDEX ist ON.<br /><br /> 0 = PADINDEX ist OFF.<br /><br /> Immer 0 für gruppierte columnstore-Indizes.|  
|**is_disabled**|**trate**|1 = Der Index ist deaktiviert.<br /><br /> 0 = Der Index ist nicht deaktiviert.|  
|**is_hypothetical**|**trate**|1 = Der Index ist hypothetisch und kann nicht direkt als Datenzugriffspfad verwendet werden. Hypothetische Indizes enthalten Statistiken auf Spaltenebene.<br /><br /> 0 = Der Index ist nicht hypothetisch.|  
|**allow_row_locks**|**bit**|1 = Der Index lässt Zeilensperren zu.<br /><br /> 0 = Der Index lässt Zeilensperren nicht zu.<br /><br /> Immer 0 für gruppierte columnstore-Indizes.|  
|**allow_page_locks**|**trate**|1 = Der Index lässt Seitensperren zu.<br /><br /> 0 = Der Index lässt Seitensperren nicht zu.<br /><br /> Immer 0 für gruppierte columnstore-Indizes.|  
|**has_filter**|**bit**|1 = Index hat einen Filter und enthält nur Zeilen, die der Filterdefinition entsprechen.<br /><br /> 0 = Index hat keinen Filter.|  
|**filter_definition**|**nvarchar (max)**|Ausdruck für die Teilmenge von Zeilen, die im gefilterten Index enthalten sind.<br /><br /> NULL für Heap oder nicht gefilterten Index.|  
|**auto_created**|**bit**|1 = der Index wurde von der automatischen Optimierung erstellt.<br /><br />0 = der Index wurde vom Benutzer erstellt.
|**optimize_for_sequential_key**|**bit**|1 = der Index hat die letzte INSERT-Optimierung für die Seite aktiviert.<br><br>0 = Standardwert. Der Index hat die INSERT-Optimierung der letzten Seite deaktiviert.|

> [!NOTE]
> Das **optimize_for_sequential_key** Bit wird nur in Versionen SQL Server 2019 CTP 3,1 und höher unterstützt.
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Weitere Informationen finden Sie unter [Konfiguration der Metadatensichtbarkeit](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden alle Indizes für die- `Production.Product` Tabelle in [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] der-Datenbank zurückgegeben.  
  
```  
  
SELECT i.name AS index_name  
    ,i.type_desc  
    ,is_unique  
    ,ds.type_desc AS filegroup_or_partition_scheme  
    ,ds.name AS filegroup_or_partition_scheme_name  
    ,ignore_dup_key  
    ,is_primary_key  
    ,is_unique_constraint  
    ,fill_factor  
    ,is_padded  
    ,is_disabled  
    ,allow_row_locks  
    ,allow_page_locks  
FROM sys.indexes AS i  
INNER JOIN sys.data_spaces AS ds ON i.data_space_id = ds.data_space_id  
WHERE is_hypothetical = 0 AND i.index_id <> 0   
AND i.object_id = OBJECT_ID('Production.Product');  
GO  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. index_columns &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [sys. xml_indexes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-xml-indexes-transact-sql.md)   
 [sys. Objects &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys. key_constraints &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys. File Groups &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys. partition_schemes &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [Abfragen der SQL Server System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [In-Memory-OLTP &#40;in-Memory-Optimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
