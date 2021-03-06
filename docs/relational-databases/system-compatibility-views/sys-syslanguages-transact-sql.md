---
title: sys. syslanguages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.syslanguages
- sys.syslanguages_TSQL
- syslanguages
- syslanguages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syslanguages system table
- sys.syslanguages compatibility view
ms.assetid: f216d1cd-997c-42f0-a737-abbdfcd88383
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc152b8241b775f9fd686f8a31363cb4fca39de4
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874869"
---
# <a name="syssyslanguages-transact-sql"></a>sys.syslanguages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Enthält eine Zeile für jede Sprache in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz.  
  
|Spaltenname|Datentyp|und Beschreibung|  
|-----------------|---------------|-----------------|  
|langid|**smallint**|Eindeutige Sprachen-ID.|  
|dateformat|**NCHAR (3)**|Reihenfolge in Datumsangaben, z. B. DMY.|  
|datefirst|**tinyint**|Erster Tag der Woche: 1 für Montag, 2 für Dienstag usw., bis 7 für Sonntag.|  
|upgrade|**int**|Ist für das System reserviert.|  
|name|**sysname**|Offizieller Sprachen Name, z. b. "Français".|  
|alias|**sysname**|Alternativer Sprachenname, z. B. Französisch.|  
|months|**nvarchar(372)**|Liste mit durch Trennzeichen getrennten Monatsnamen in voller Länge, in der Reihenfolge Januar bis Dezember. Jeder Name kann bis zu 20 Zeichen lang sein.|  
|shortmonths|**nvarchar(132)**|Liste mit durch Trennzeichen getrennten abgekürzten Monatsnamen, in der Reihenfolge Januar bis Dezember. Jeder Name kann bis zu 9 Zeichen lang sein.|  
|days|**nvarchar(217)**|Liste mit durch Trennzeichen getrennten Wochentagsnamen, in der Reihenfolge von Montag bis Sonntag. Jeder Name kann bis zu 30 Zeichen lang sein.|  
|lcid|**int**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Gebietsschema-ID für die Sprache.|  
|msglangid|**smallint**|ID der Meldungsgruppe von [!INCLUDE[ssDE](../../includes/ssde-md.md)]|  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] enthält die folgenden installierten Sprachen.  
  
|Name auf Deutsch|Windows-LCID|ID der Meldungsgruppe von [!INCLUDE[ssDE](../../includes/ssde-md.md)].|  
|---------------------|------------------|-----------------------------------------|  
|Englisch|1033|1033|  
|Deutsch|1031|1031|  
|Französisch|1036|1036|  
|Japanisch|1041|1041|  
|Dänisch|1030|1030|  
|Spanisch|3082|3082|  
|Italienisch|1040|1040|  
|Niederländisch|1043|1043|  
|Norwegisch|2068|2068|  
|Portugiesisch|2070|2070|  
|Finnisch|1035|1035|  
|Schwedisch|1053|1053|  
|Tschechisch|1029|1029|  
|Ungarisch|1038|1038|  
|Polnisch|1045|1045|  
|Rumänisch|1048|1048|  
|Kroatisch|1050|1050|  
|Slowakisch|1051|1051|  
|Schem|1060|1060|  
|Griechisch|1032|1032|  
|Bulgarisch|1026|1026|  
|Russisch|1049|1049|  
|Türkisch|1055|1055|  
|Englisch (britisch)|2057|1033|  
|Estnisch|1061|1061|  
|Lettisch|1062|1062|  
|Litauisch|1063|1063|  
|Portugiesisch (Brasilien)|1046|1046|  
|Chinesisch (traditionell)|1028|1028|  
|Koreanisch|1042|1042|  
|Chinesisch (vereinfacht)|2052|2052|  
|Arabisch|1025|1025|  
|Thai|1054|1054|  
  
## <a name="see-also"></a>Siehe auch  
 [Kompatibilitäts &#40;Sichten (Transact&#41; -SQL](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md) - )  
 [Mapping von Systemtabellen zu System &#40;Sichten Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
