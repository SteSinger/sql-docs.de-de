---
title: SQL Server-Agent, Auftragsschritte-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 323bf0c943d12a2d05e5fde80194d35d9ab733cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206563"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server-Agent, Auftragsschritte-Objekt
  Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent: **Auftragsschritte** -Leistungsobjekt enthält Leistungsindikatoren, die Informationen zu den Auftragsschritten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents angeben. In der nachfolgenden Tabelle sind die in diesem Objekt enthaltenen Indikatoren aufgelistet.  
  
 Die folgende Tabelle enthält die Leistungsindikatoren von **SQLAgent:Auftragsschritte** .  
  
|Name|Beschreibung|  
|----------|-----------------|  
|**Aktive Schritte**|Dieser Indikator gibt die Anzahl der aktuell ausgeführten Auftragsschritte an.|  
|**Schritte in Warteschlange**|Dieser Indikator gibt die Anzahl der Auftragsschritte an, die für das Ausführen durch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent bereitstehen, deren Ausführung jedoch noch nicht gestartet wurde.|  
|**Wiederholungen von Schritten gesamt**|Dieser Indikator gibt an, wie oft [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seit dem letzten Serverneustart insgesamt versucht hat, einen Auftragsschritt neu zu starten.|  
  
 Jeder Leistungsindikator in dem Objekt enthält die folgenden Instanzen:  
  
|Instanz|Beschreibung|  
|--------------|-----------------|  
|**_Total**|Informationen für alle Auftragsschritte.|  
|**ActiveScripting**|Informationen für Auftragsschritte, die das **ActiveScripting** -Subsystem verwenden.|  
|**ANALYSISCOMMAND**|Informationen für Auftragsschritte, die das ANALYSISCOMMAND-Subsystem verwenden.|  
|**ANALYSISQUERY**|Informationen für Auftragsschritte, die das ANALYSISQUERY-Subsystem verwenden.|  
|**CmdExec**|Informationen für Auftragsschritte, die das **CmdExec** -Subsystem verwenden.|  
|**Distribution**|Informationen für Auftragsschritte, die das **Distribution** -Subsystem verwenden.|  
|**Dts**|Informationen für Auftragsschritte, die das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Subsystem verwenden.|  
|**LogReader**|Informationen für Auftragsschritte, die das **LogReader** -Subsystem verwenden.|  
|**Merge**|Informationen für Auftragsschritte, die das **Merge** -Subsystem verwenden.|  
|**PowerShell**|Informationen für Auftragsschritte, die das **PowerShell** -Subsystem verwenden.|  
|**QueueReader**|Informationen für Auftragsschritte, die das **QueueReader** -Subsystem verwenden.|  
|**Momentaufnahme**|Informationen für Auftragsschritte, die das **Momentaufnahme** -Subsystem verwenden.|  
|**TSQL**|Informationen für Auftragsschritte, die [!INCLUDE[tsql](../../includes/tsql-md.md)]ausführen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Auftragsschritten](../../ssms/agent/manage-job-steps.md)   
 [Verwenden von Leistungsobjekten](../../ssms/agent/use-performance-objects.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](monitor-resource-usage-system-monitor.md)  
  
  
