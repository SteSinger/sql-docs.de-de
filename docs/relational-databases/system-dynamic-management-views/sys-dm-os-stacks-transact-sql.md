---
title: dm_os_stacks (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_stacks
- dm_os_stacks_TSQL
- sys.dm_os_stacks
- sys.dm_os_stacks_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_stacks dynamic management view
ms.assetid: a69b06c4-28f0-4535-8fa1-9f132db4d916
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8f287c548a7ebb71b1ebf3e1bce30e43b412c755
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265721"
---
# <a name="sysdmosstacks-transact-sql"></a>sys.dm_os_stacks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Diese dynamische Verwaltungssicht wird intern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für Folgendes verwendet:  
  
-   Nachverfolgen von Debugdaten wie z. B. ausstehenden Zuordnungen.  
  
-   Voraussetzen oder Überprüfen von Logik, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten an Stellen verwendet wird, an denen von einer Komponente vorausgesetzt wird, dass ein bestimmter Aufruf erfolgt ist.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**stack_address**|**varbinary(8)**|Eindeutige Adresse für diese Stapelzuordnung. Lässt keine NULL-Werte zu.|  
|**frame_index**|**int**|Jede Zeile stellt einen Funktionsaufruf dar, der bei Sortierung in aufsteigender Reihenfolge nach Rahmenindex für einen bestimmten **stack_address**-Wert die vollständige Aufrufliste zurückgibt. Lässt keine NULL-Werte zu.|  
|**frame_address**|**varbinary(8)**|Adresse des Funktionsaufrufes. Lässt keine NULL-Werte zu.|  
  
## <a name="remarks"></a>Hinweise  
 **sys.dm_os_stacks** erfordert, dass die Symbole des Servers und anderer Komponenten auf dem Server vorhanden sein müssen, damit die Informationen richtig angezeigt werden.  
  
## <a name="permissions"></a>Berechtigungen

Auf [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], erfordert `VIEW SERVER STATE` Berechtigung.   
Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium-Tarife, erfordert die `VIEW DATABASE STATE` Berechtigung in der Datenbank. Auf [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard und Basic-Version, erfordert die **Serveradministrator** oder **Azure Active Directory-Administrator** Konto.   


## <a name="see-also"></a>Siehe auch  
  [Dynamische Verwaltungssichten in Verbindung mit SQL Server-Betriebssystem &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
