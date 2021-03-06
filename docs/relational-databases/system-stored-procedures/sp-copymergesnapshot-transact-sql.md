---
title: sp_copymergesnapshot (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copymergesnapshot
- sp_copymergesnapshot_TSQL
helpviewer_keywords:
- sp_copymergesnapshot
ms.assetid: eaecd6e0-8486-4e5d-ace7-8ae75768c0a8
author: stevestein
ms.author: sstein
ms.openlocfilehash: d51f29399487ee156210e96fe598c38288755913
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381714"
---
# <a name="sp_copymergesnapshot-transact-sql"></a>sp_copymergesnapshot (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Kopiert den Momentaufnahme Ordner der angegebenen Veröffentlichung in den Ordner, der in der **\@destination_folder**aufgeführt ist. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_copymergesnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` ist der Name der Veröffentlichung, deren Momentaufnahme Inhalt kopiert werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @destination_folder = ] 'destination_folder'` ist der Name des Ordners, in den der Inhalt der Veröffentlichungs Momentaufnahme kopiert werden soll. *destination_folder*ist vom Datentyp **nvarchar (255)** und hat keinen Standardwert. Der *destination_folder* kann ein alternativer Speicherort sein, z. b. auf einem anderen Server, auf einem Netzlaufwerk oder auf einem Wechselmedium (z. b. CD-ROMs oder Wechsel Datenträger).  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Remarks  
 **sp_copymergesnapshot** wird bei der Mergereplikation verwendet. Abonnenten, die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7,0 und früher ausführen, können den alternativen Momentaufnahme Speicherort nicht verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_copymergesnapshot**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Alternative Speicherorte für Momentaufnahmeordner](../../relational-databases/replication/snapshot-options.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
