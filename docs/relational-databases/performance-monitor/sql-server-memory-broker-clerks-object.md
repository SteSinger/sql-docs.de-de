---
title: SQL Server, Speicherbrokerclerks (Objekt) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: fff8aa7a2e37f66470798b2772ed00d0298708a3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093415"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQLServer, Speicherbrokerclerks (Objekt)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Das Leistungsobjekt **SQLServer: Speicherbrokerclerks** enthält Leistungsindikatoren für Statistiken zu Speicherbrokerclerks.

In der folgenden Tabelle werden die SQL Server-Leistungsobjekte für **Speicherbrokerclerks** beschrieben.

|**SQL Server-Speicherbrokerclerks (Leistungsindikatoren)**|und Beschreibung|  
|-------------|-----------------|  
|**Interner Nutzen**|Der interne Wert des Arbeitsspeichers für eine unzureichende Eintragsanzahl (in ms pro Seite pro ms) multipliziert mit 10 Milliarden und auf eine ganze Zahl gekürzt.|
|**Größe des Speicherbrokerclerks**|Die Clerkgröße in Seiten.|
|**Periodische Entfernungsvorgänge (Seiten)**|Die Anzahl der durch den letzten periodischen Entfernungsvorgang aus dem Brokerclerk entfernten Seiten.|
|**Überlastungsentfernungsvorgänge (Seiten/Sekunde)**|Die Anzahl der Seiten pro Sekunde, die aufgrund unzureichenden Arbeitsspeichers aus dem Brokerclerk entfernt wurden.|
|**Simulationsnutzen**|Der Wert des Arbeitsspeichers für den Clerk (in ms pro Seite pro ms) multipliziert mit 10 Milliarden und auf eine ganze Zahl gekürzt.|
|**Simulationsgröße**|Die aktuelle Größe der Clerksimulation in Seiten.|

Es gibt eine Instanz des Indikators für den Pufferpool und für den Objektpool des Spaltenspeichers.

## <a name="see-also"></a>Weitere Informationen  
[Überwachen der Ressourcenverwendung (Systemmonitor)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
