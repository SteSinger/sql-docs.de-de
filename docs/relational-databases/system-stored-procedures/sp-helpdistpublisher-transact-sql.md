---
title: sp_helpdistpublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
author: stevestein
ms.author: sstein
ms.openlocfilehash: a47a81b2b19ceccf76a031e298ab60cf4a6f8c9a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770952"
---
# <a name="sphelpdistpublisher-transact-sql"></a>sp_helpdistpublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt Eigenschaften der Verleger zurück, die einen Verteiler verwenden. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdistpublisher [ [ @publisher=] 'publisher']   
    [ , [ @check_user = ] check_user  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Verleger, für den Eigenschaften zurückgegeben werden. *Publisher* ist vom **Datentyp vom Datentyp sysname**. der **%** Standardwert ist.  
  
`[ @check_user = ] check_user` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name des Verlegers.|  
|**distribution_db**|**sysname**|Verteilungsdatenbank für den angegebenen Verleger.|  
|**security_mode**|**int**|Sicherheitsmodus, der von Replikations-Agents für die Verbindung mit dem Verleger für Abonnements mit verzögertem Update über eine Warteschlange oder für die Verbindung mit einem Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger verwendet wird.<br /><br /> 0 =  -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung<br /><br /> **1** = Windows-Authentifizierung|  
|**login**|**sysname**|Anmeldename, der von Replikations-Agents für die Verbindung mit dem Verleger für Abonnements mit verzögertem Update über eine Warteschlange oder für die Verbindung mit einem Nicht-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verleger verwendet wird.|  
|**password**|**nvarchar(524)**|Zurückgegebenes Kennwort (in einfacher verschlüsselter Form). Das Kennwort ist für andere Benutzer als **sysadmin**NULL.|  
|**enden**|**bit**|Gibt an, ob ein Remoteverleger den lokalen Server als Verteiler verwendet:<br /><br /> **0** = Nein<br /><br /> **1** = Ja|  
|**working_directory**|**nvarchar(255)**|Name des Arbeitsverzeichnisses.|  
|**würdiges**|**bit**|Gibt an, ob das Kennwort beim Herstellen der Verbindung des Verlegers mit dem Verteiler erforderlich ist. In und höheren Versionen sollte dies immer 0 (null) zurückgeben, was bedeutet, dass das Kennwort erforderlich ist. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**thirdparty_flag**|**bit**|Gibt an, ob die Veröffentlichung durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder eine Anwendung eines Drittanbieters aktiviert wurde:<br /><br /> **"0** = ","Oracle"oder"OracleGatewayPublisher".[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> **1** = der Verleger wurde in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe einer Drittanbieter Anwendung integriert.|  
|**publisher_type**|**sysname**|Typ des Verlegers; kann einer der folgenden sein:<br /><br /> **MSSQLSERVER**<br /><br /> **ORAKEL**<br /><br /> **ORACLE-GATEWAY**|  
|**publisher_data_source**|**nvarchar(4000)**|Name der OLE DB-Datenquelle auf dem Verleger.|  
|**storage_connection_string**|**nvarchar(4000)**|Speicherzugriffs Schlüssel für das Arbeitsverzeichnis, wenn der Verteiler oder Verleger in Azure SQL-Datenbank erstellt wird.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_helpdistpublisher** wird für alle Replikations Typen verwendet.  
  
 **sp_helpdistpublisher** zeigt die Verleger Anmeldung oder das Kennwort nicht im Resultset für nicht-**sysadmin** -Anmeldungen an.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der festen Server Rolle **sysadmin** können **sp_helpdistpublisher** für jeden Verleger ausführen, der den lokalen Server als Verteiler verwendet. Mitglieder der festen Daten Bank Rolle **db_owner** oder der **replmonitor** -Rolle in einer Verteilungs Datenbank können **sp_helpdistpublisher** für jeden Verleger ausführen, der diese Verteilungs Datenbank verwendet. Benutzer in der Veröffentlichungs Zugriffsliste für eine Veröffentlichung auf dem angegebenen *Verleger* können **sp_helpdistpublisher**ausführen. Wenn *Publisher* nicht angegeben wird, werden Informationen für alle Verleger zurückgegeben, für die der Benutzer Zugriffsberechtigung hat.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
