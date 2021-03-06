---
title: MSmerge_agents (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_agents
- MSmerge_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_agents system table
ms.assetid: 639d2ebb-2c37-4fe0-b14b-1637bc5fc221
author: stevestein
ms.author: sstein
ms.openlocfilehash: 980ecd00a07e1119a64552a3f4c903434fd09029
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106442"
---
# <a name="msmergeagents-transact-sql"></a>MSmerge_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_agents** -Tabelle enthält eine Zeile für jeden Merge-Agent auf dem Abonnenten ausgeführt wird. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Die ID des Merge-Agents|  
|**name**|**nvarchar(100)**|Der Name des Merge-Agents.|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**publication**|**sysname**|Der Name der Veröffentlichung.|  
|**subscriber_id**|**smallint**|Die ID des Abonnenten.|  
|**subscriber_db**|**sysname**|Der Name der Abonnementdatenbank.|  
|**local_job**|**bit**|Gibt an, ob sich ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Auftrag auf dem lokalen Verteiler befindet.|  
|**job_id**|**binary(16)**|Die Auftrags-ID|  
|**profile_id**|**int**|Der Konfigurations-ID aus der **MSagent_profiles** Tabelle.|  
|**anonymous_subid**|**uniqueidentifier**|Die ID eines anonymen Agents.|  
|**subscriber_name**|**sysname**|Den Namen des Abonnenten.|  
|**creation_date**|**datetime**|Das Datum und die Uhrzeit der Erstellung des Verteilungs- oder Merge-Agents.|  
|**offload_enabled**|**bit**|Gibt an, dass eine Remoteaktivierung der Momentaufnahme möglich ist.<br /><br /> **0** gibt an, der Agent nicht remote aktiviert werden.<br /><br /> **1** gibt an, die aktiviert wird, Remote und auf dem Remotecomputer, die in der Offload_server-Eigenschaft angegeben.|  
|**offload_server**|**sysname**|Gibt den Netzwerknamen des Servers an, auf dem die Remoteaktivierung der Momentaufnahme erfolgt.|  
|**sid**|**varbinary(85)**|Die Sicherheits-ID (SID) für den Verteilungs-Agent oder Merge-Agent, während er das erste Mal ausgeführt wird.|  
|**subscriber_security_mode**|**smallint**|Der Sicherheitsmodus, der vom Agent beim Herstellen einer Verbindung mit dem Abonnenten verwendet wird, wobei die folgenden Werte möglich sind:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung.|  
|**subscriber_login**|**sysname**|Der Anmeldename, der verwendet wird, um eine Verbindung mit dem Abonnenten herzustellen.|  
|**subscriber_password**|**nvarchar(524)**|Der verschlüsselte Wert des Kennworts, das verwendet wird, um eine Verbindung mit dem Abonnenten herzustellen.|  
|**publisher_security_mode**|**smallint**|Der Sicherheitsmodus, der vom Agent beim Herstellen einer Verbindung mit dem Verleger verwendet wird. Dies kann einer der folgenden Modi sein:<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung.|  
|**publisher_login**|**sysname**|Der Anmeldename, der beim Herstellen einer Verbindung mit dem Verleger verwendet wird|  
|**publisher_password**|**nvarchar(524)**|Der verschlüsselte Wert des Kennworts, das verwendet wird, um eine Verbindung mit dem Verleger herzustellen.|  
|**job_step_uid**|**uniqueidentifier**|Die eindeutige ID des Auftragsschritts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents, in dem der Agent gestartet wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
