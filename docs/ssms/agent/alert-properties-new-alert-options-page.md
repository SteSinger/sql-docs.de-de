---
title: Warnungseigenschaften – Neue Warnung (Seite „Optionen“)
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8f3196b227b630e446e4dfa2565469b9666e71fb
ms.sourcegitcommit: 949e55b32eff6610087819a93160a35af0c5f1c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2019
ms.locfileid: "70383471"
---
# <a name="alert-properties---new-alert-options-page"></a>Warnungseigenschaften – Neue Warnung (Seite „Optionen“)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Mithilfe dieser Seite können Sie die Optionen für Agentwarnungen in [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzeigen und ändern.  

## <a name="options"></a>enthalten  
**E-Mail**  
Schließt Fehlertext des Ereignisses ggf. in E-Mail-Benachrichtigungen ein.  
  
**Pager**  
Schließt Fehlertext des Ereignisses ggf. in Pagerbenachrichtigungen ein.  
  
**NET SEND**  
Schließt Fehlertext des Ereignisses ggf. in NET SEND-Benachrichtigungen ein.  
  
**Zusätzlich zu sendende Warnbenachrichtigung**  
Geben Sie hier zusätzlichen Text ein, der in die Benachrichtigungsmeldungen aufgenommen werden soll.  
  
**Antwortverzögerung**  
Geben Sie eine Verzögerung für das wiederholte Auftreten des Ereignisses an. Einige Ereignisse können innerhalb einer kurzen Zeitspanne häufig auftreten. In diesem Fall könnte es sinnvoll sein, zwar über das Auftreten des Ereignisses informiert zu werden, nicht aber für jedes Auftreten eine Meldung zu erhalten. Mithilfe dieser Option können Sie einen Timeoutwert angeben. Durch die Angabe einer Verzögerung nach der Warnungsantwort auf ein Ereignis wartet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent die angegebene Verzögerungszeit ab, bevor eine weitere Antwort zurückgegeben wird, unabhängig davon, ob das Ereignis in der Zwischenzeit wieder auftritt.  
  
**Minuten**  
Geben Sie eine Verzögerung in Minuten an. Wenn bei jedem Auftreten des Ereignisses geantwortet werden soll, geben Sie 0 Minuten und 0 Sekunden an.  
  
**Sekunden**  
Geben Sie eine Verzögerung in Sekunden an. Wenn bei jedem Auftreten des Ereignisses geantwortet werden soll, geben Sie 0 Minuten und 0 Sekunden an.  
  
## <a name="see-also"></a>Weitere Informationen  
[Warnungen](../../ssms/agent/alerts.md)  
  
