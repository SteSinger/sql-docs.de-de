---
title: MSSQLSERVER_1203 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1203 (Database Engine error)
ms.assetid: 33a35f00-98c8-46c6-b432-544b326b6117
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 22fbf90a31514513555fd90fde421f81ba3eb499
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031112"
---
# <a name="mssqlserver1203"></a>MSSQLSERVER_1203
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1203|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LK_NOT|  
|Meldungstext|Der Prozess mit der ID %d versuchte, die Sperre für die %.*ls-Ressource, deren Besitzer er nicht ist, aufzuheben. Wiederholen Sie die Transaktion, da dieser Fehler möglicherweise auf einen zeitbedingten Fehler zurückzuführen ist. Falls das Problem weiterhin besteht, wenden Sie sich an den Datenbankadministrator.|  
  
## <a name="explanation"></a>Erklärung  
Dieser Fehler tritt auf, wenn in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] andere Aktivitäten als gewöhnliche Cleanups nach der Verarbeitung ausgeführt werden und wenn festgestellt wird, dass eine bestimmte Seite, für die die Sperre aufgehoben werden soll, bereits entsperrt ist.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
Die zugrunde liegende Ursache dieses Fehlers hängt möglicherweise mit Strukturproblemen in der betroffenen Datenbank zusammen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwaltet den Abruf und die Freigabe von Seiten zum Aufrechterhalten der Parallelitätssteuerung in der Mehrbenutzerumgebung. Dieser Mechanismus wird durch die Verwendung verschiedener interner Sperrstrukturen sichergestellt, mit denen die Seite und die Art der vorhandenen Sperre angegeben wird. Sperren werden für die Verarbeitung der betreffenden Seiten abgerufen, und sie werden freigegeben, wenn die Verarbeitung abgeschlossen ist.  
  
## <a name="user-action"></a>Benutzeraktion  
Führen Sie DBCC CHECKDB für die Datenbank aus, zu der das Objekt gehört. Wenn mithilfe von DBCC CHECKDB keine Fehler gemeldet werden, versuchen Sie, die Verbindung wiederherzustellen, und führen Sie den Befehl aus.  
  
> [!IMPORTANT]  
> Wenn durch das Ausführen von DBCC CHECKDB mit einer der REPAIR-Klauseln das Indexproblem nicht behoben wird oder wenn Sie sich nicht sicher sind, wie sich DBCC CHECKDB mit einer REPAIR-Klausel auf Ihre Daten auswirkt, wenden Sie sich an Ihren primären Anbieter für technischen Support.  
  
