---
title: Fenster 'Threads'
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d84c0ba15b036dfff8e6e2a69bb7702c771df1b
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243027"
---
# <a name="threads-window"></a>Fenster 'Threads'
  Im Fenster **Threads** werden Informationen zu dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] Thread angezeigt, der von der [!INCLUDE[ssDE](../../includes/ssde-md.md)] gerade gedebuggten Abfrage-Editor-Sitzung verwendet wird. Sie müssen sich im Debugmodus befinden, um die Threadinformationen anzuzeigen.  
  
## <a name="task-list"></a>Aufgabenliste  
 **So greifen Sie auf das Thread Fenster zu**  
  
-   Klicken Sie im Menü **Debuggen** auf **Fenster**und dann auf **Threads**.  
  
## <a name="columns"></a>Spalten  
 **Name**  
 Ist eine eindeutig kennzeichnende Zahl, die der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger dem Thread zuweist. Um weitere Informationen zum Thread anzuzeigen, wählen Sie in der dynamischen Verwaltungssicht sys.dm_os_threads eine Zeile aus.  
  
 Wenn die Ausführung nicht im Lightweightpooling-Modus erfolgt, wählen Sie die Zeile aus, in der der Wert in „os_thread_id“ mit dem Wert in der Spalte **ID** übereinstimmt. Wenn die Ausführung im Lightweightpooling-Modus erfolgt, wählen Sie die Zeile aus, in der der Wert in „fiber_context_address“ mit dem Wert in der Spalte **ID** übereinstimmt.  
  
 **Benennen**  
 Zeigt Informationen über die [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Sitzung im Format **ComputerName/InstanceName [SPID]** an.  
  
 **ComputerName**  
 Der Name des Computers, auf dem die Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] ausgeführt wird, mit der die Abfrage-Editor-Sitzung verbunden ist.  
  
 **InstanceName**  
 Der Name der Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] , mit der die Abfrage-Editor-Sitzung verbunden ist.  
  
 **SPID**  
 Die Prozess-ID der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sitzung, die diese Sitzung eindeutig kennzeichnet. Weitere Informationen über die Sitzung können Sie abrufen, indem Sie in der sys.sysprocesses-Sicht die Zeile auswählen, die in der Spalte spid denselben Wert enthält.  
  
 **Hotels**  
 Zeigt den Namen der Skriptdatei an, die von der gerade gedebuggten Abfrage-Editor-Sitzung verwendet wird.  
  
 **Haben**  
 Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger unterstützt diese Funktion nicht.  
  
 **Anhalten**  
 Der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Debugger unterstützt diese Funktion nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transact-SQL-Debugger](transact-sql-debugger.md)   
 [Informationen zum Transact-SQL-Debugger](transact-sql-debugger-information.md)   
 [sys. dm_os_threads &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql)   
 [sys. sysprocesses &#40;Transact-SQL-&#41;](/sql/relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql)  
