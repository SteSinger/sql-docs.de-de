---
title: sys. column_store_dictionaries (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.column_store_dictionaries_TSQL
- column_store_dictionaries
- column_store_dictionaries_TSQL
- sys.column_store_dictionaries
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_dictionaries catalog view
ms.assetid: 56efd563-2f72-4caf-94e3-8a182385c173
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2348633a2c357868e4688d7b37c5cf28aed6441a
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304757"
---
# <a name="syscolumn_store_dictionaries-transact-sql"></a>sys.column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes Wörterbuch, das in speicheroptimierten xVelocity-columnstore-Indizes verwendet wird. Wörterbücher werden zum Codieren bestimmter, aber nicht aller Datentypen verwendet. Daher verfügen nicht alle Spalten in einem columnstore-Index über Wörterbücher. Ein Wörterbuch kann als primäres Wörterbuch (für alle Segmente) und möglicherweise für weitere sekundäre Wörterbücher vorhanden sein, die für eine Teilmenge der Spaltensegmente verwendet werden.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|**hobt_id**|**bigint**|ID des Heap-oder B-Struktur Index ("hubt") für die Tabelle, die diesen columnstore--Index aufweist.|  
|**column_id**|**int**|ID der columnstore--Spalte, beginnend mit 1. Die erste Spalte hat die ID = 1, die zweite Spalte hat die ID = 2 usw.|  
|**dictionary_id**|**int**|Einem Spalten Segment können zwei Arten von Wörterbüchern (Global und local) zugeordnet sein. Der dictionary_id 0 steht für das globale Wörterbuch, das für alle Spalten Segmente (eines für jede Zeilen Gruppe) für diese Spalte freigegeben ist.|  
|**version**|**int**|Version des Wörterbuchformats.|  
|**Typ**|**int**|Wörterbuchtyp:<br /><br /> 1-Hash Wörterbuch mit **int** -Werten<br /><br /> 2-nicht verwendet<br /><br /> 3-Hash-Wörterbuch mit Zeichen folgen Werten<br /><br /> 4-Hash Wörterbuch mit **float** -Werten<br /><br /> Weitere Informationen zu Wörterbüchern finden Sie im [Leitfaden zu columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md).|  
|**last_id**|**int**|Die letzte Daten-ID im Wörterbuch.|  
|**entry_count**|**bigint**|Die Anzahl von Einträgen im Wörterbuch.|  
|**on_disc_size**|**bigint**|Größe des Wörterbuchs in Byte.|  
|**partition_id**|**bigint**|Gibt die Partitions-ID an. Ist innerhalb einer Datenbank eindeutig.|  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die `VIEW DEFINITION`-Berechtigung für die Tabelle. Die folgenden Spalten geben NULL zurück, es sei denn, der Benutzer verfügt auch über `SELECT` Berechtigung: last_id, ENTRY_COUNT data_ptr.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Abfragen der SQL Server-System Katalog-FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Beschreibung von Columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [Beschreibung von Columnstore-Indizes](~/relational-databases/indexes/columnstore-indexes-overview.md)   
 [sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)  
  
  

