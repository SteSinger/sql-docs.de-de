---
title: Führen Sie im Dialogfeld Paket | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageexecute.f1
- sql12.ssis.ssms.executepackage.f1
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b4b920b17e960059e1212be7dd15c176c0b25a47
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66059186"
---
# <a name="execute-package-dialog-box"></a>Execute Package Dialog Box
  Mit dem Dialogfeld **Paket ausführen** können Sie ein Paket auszuführen, das auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server gespeichert ist.  
  
 Ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paket kann Parameter enthalten, die auf in Umgebungsvariablen gespeicherte Werte verweisen. Vor dem Ausführen eines solchen Pakets müssen Sie angeben, mit welcher Umgebung die Werte für die Umgebungsvariablen bereitgestellt werden sollen. Ein Projekt kann mehrere Umgebungen enthalten, aber nur eine Umgebung kann zum Binden von Umgebungsvariablenwerten bei der Ausführung verwendet werden. Wenn keine Umgebungsvariablen im Paket verwendet werden, ist auch keine Umgebung erforderlich.  
  
 Was möchten Sie tun?  
  
-   [Öffnen des Dialogfelds "Paket ausführen"](#open_dialog)  
  
-   [Festlegen der Optionen auf der Seite "Allgemein"](#general)  
  
-   [Festlegen der Optionen auf der Registerkarte "Parameter"](#parameters)  
  
-   [Festlegen der Optionen auf der Registerkarte "Verbindungs-Manager"](#connection)  
  
-   [Festlegen der Optionen auf der Registerkarte "Erweitert"](#advanced)  
  
-   [Erstellen der Optionen im Dialogfeld Paket ausführen](#script)  
  
##  <a name="open_dialog"></a> Öffnen des Dialogfelds "Paket ausführen"  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]eine Verbindung zum [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server her.  
  
     Sie stellen eine Verbindung mit der [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]-Instanz her, die die SSISDB-Datenbank hostet.  
  
2.  Erweitern Sie im Objekt-Explorer die Struktur, um den Knoten **Integration Services-Kataloge** anzuzeigen.  
  
3.  Erweitern Sie den **SSISDB** -Knoten.  
  
4.  Erweitern Sie den Ordner, der das auszuführende Paket enthält.  
  
5.  Klicken Sie mit der rechten Maustaste auf das Paket, und klicken Sie dann auf **Ausführen**.  
  
##  <a name="general"></a> Festlegen der Optionen auf der Seite "Allgemein"  
 Wählen Sie **Umgebung** aus, um die Umgebung anzugeben, die für das ausgeführte Paket angewendet wird.  
  
##  <a name="parameters"></a> Festlegen der Optionen auf der Registerkarte "Parameter"  
 Verwenden Sie die Registerkarte **Parameter** , um die Parameterwerte zu ändern, die bei der Ausführung des Pakets verwendet werden.  
  
##  <a name="connection"></a> Festlegen der Optionen auf der Registerkarte "Verbindungs-Manager"  
 Verwenden Sie die Registerkarte "Verbindungs-Manager", um die Eigenschaften des jeweiligen Paketverbindungs-Managers festzulegen.  
  
##  <a name="advanced"></a> Festlegen der Optionen auf der Registerkarte "Erweitert"  
 Verwenden Sie die Registerkarte "Erweitert", um Eigenschaften und andere Paketeinstellungen zu verwalten.  
  
 **Hinzufügen**, **Bearbeiten**, **Entfernen**  
 Klicken Sie auf die entsprechende Option, um eine Eigenschaft hinzuzufügen, zu bearbeiten oder zu entfernen.  
  
 **Protokolliergrad**  
 Wählen Sie den Protokolliergrad für die Paketausführung aus. Weitere Informationen finden Sie unter [catalog.set_execution_parameter_value &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database).  
  
 **Speichern bei Fehlern**  
 Geben Sie an, ob eine Dumpdatei erstellt wird, wenn Fehler während der Paketausführung auftreten. Weitere Informationen finden Sie unter [Generating Dump Files for Package Execution](troubleshooting/generating-dump-files-for-package-execution.md).  
  
 **32-Bit-Laufzeit**  
 Geben Sie an, dass das Paket auf einem 32-Bit-System ausgeführt wird.  
  
##  <a name="script"></a> Erstellen der Optionen im Dialogfeld Paket ausführen  
 Im Dialogfeld **Paket ausführen** können Sie auch die Schaltfläche **Skript** verwenden, um Code für [!INCLUDE[tsql](../includes/tsql-md.md)] zu erstellen. Mit dem generierten Skript werden die gespeicherten Prozeduren für [catalog.start_execution &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) mit den gleichen Optionen ausgeführt, die im Dialogfeld **Paket ausführen** ausgewählt wurden. Das Skript wird in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]in einem neuen Skriptfenster angezeigt.  
  
  
