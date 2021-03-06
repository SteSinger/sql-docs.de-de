---
title: Ändern von Ablaufverfolgungsvorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ebe8924f46de15a3a34c0f49304c87a904919bdb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63035041"
---
# <a name="modify-trace-templates"></a>Ändern von Ablaufverfolgungsvorlagen
  Sie können Vorlagen ändern, wenn diese in einer Datei auf dem lokalen Computer gespeichert sind und auf dem Computer [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ausgeführt wird. Sie können auch Vorlagen ändern, die aus diesen Dateien abgeleitet wurden. Beim Ändern vorhandener Vorlagen bearbeiten Sie die Eigenschaften der Vorlage, wie Ereignisklassen und Datenspalten, in derselben Reihenfolge, in der die Eigenschaften ursprünglich festgelegt wurden. Dies geschieht über die Registerkarte **Ereignisauswahl** im Dialogfeld **Ablaufverfolgungseigenschaften** . Ereignisklassen und Datenspalten können hinzugefügt oder entfernt werden, und Filter können geändert werden. Nach dem Ändern der Vorlage wird eine benutzerspezifische Vorlage erstellt, und die ursprüngliche Systemvorlage bleibt unverändert. Weitere Informationen finden Sie unter [Speichern von Ablaufverfolgungen und Ablaufverfolgungsvorlagen](save-traces-and-trace-templates.md).  
  
 Möglicherweise müssen Sie eine Vorlage von einer vorhandenen Ablaufverfolgungsdatei ableiten, z. B. falls Sie vergessen haben, welche Vorlage ursprünglich zum Erstellen der Ablaufverfolgung verwendet wurde (oder wenn diese Datei nicht gespeichert wurde) oder falls Sie eine Ablaufverfolgung später erneut ausführen möchten. Bei vorhandenen Ablaufverfolgungen können Sie die Eigenschaften zwar anzeigen, aber nicht ändern. Um die Eigenschaften zu ändern, müssen Sie die Ablaufverfolgung beenden oder anhalten. Weitere Informationen finden Sie unter [Ableiten einer Vorlage von einer Ablaufverfolgungsdatei oder Ablaufverfolgungstabelle &#40;SQL Server Profiler&#41;](sql-server-profiler.md) und [Ableiten einer Vorlage von einer zurzeit ausgeführten Ablaufverfolgung &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
 **So erstellen Sie eine Ablaufverfolgungsvorlage**  
  
 [Erstellen einer Ablaufverfolgungsvorlage &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md)  
  
 **So führen Sie eine Ablaufverfolgung mithilfe einer Ablaufverfolgungsvorlage aus**  
  
 [Erstellen einer Ablaufverfolgung &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)  
  
 **So ändern Sie eine Ablaufverfolgungsvorlage**  
  
 [Verwenden von SQL Server Profiler](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [Verwenden von Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 **So fügen Sie zu einer Ablaufverfolgungsvorlage oder -datei Ereignisse hinzu bzw. entfernen sie**  
  
 [Verwenden von SQL Server Profiler](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Verwenden von Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [Starten einer Ablaufverfolgung](start-a-trace.md)  
  
  
