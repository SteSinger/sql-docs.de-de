---
title: Umbenennen einer mehrdimensionalen Datenbank (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 192582ec7724e16b0c02d499fac89798c4c17cd6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312660"
---
# <a name="rename-a-multidimensional-database-analysis-services"></a>Umbenennen einer mehrdimensionalen Datenbank (Analysis Services)
  Wie der Name einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank geändert wird, hängt davon ab, wie Sie die Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank herstellen. Zum Ändern des Namens einer vorhandenen Datenbank müssen Sie die Verbindung im Onlinemodus herstellen. Zum Ändern des Namens der Datenbank, in die Objekte in einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt instanziiert werden, müssen Sie die Verbindung im Projektmodus herstellen.  
  
### <a name="to-change-the-database-name-in-online-mode"></a>So ändern Sie den Datenbanknamen im Onlinemodus  
  
1.  Stellen Sie mithilfe von [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]eine direkte Verbindung mit der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank her.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Datenbank, und klicken Sie anschließend auf **Datenbank bearbeiten**.  
  
3.  Ändern Sie im Textfeld **Datenbankname** den Namen der Datenbank.  
  
4.  Klicken Sie auf der Symbolleiste auf **Speichern** oder **Alle speichern** , klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** oder **Alle speichern** , oder schließen Sie den **Datenbank-Designer** , und klicken Sie bei entsprechender Aufforderung auf **Speichern** .  
  
     Der Datenbankname wird in der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz aktualisiert, und das Datenbankobjekt im Projektmappen-Explorer wird aktualisiert.  
  
### <a name="to-change-the-database-name-in-project-mode"></a>So ändern Sie den Datenbanknamen im Projektmodus  
  
1.  Öffnen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt.  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Klicken Sie im Dialogfeld **Eigenschaftenseiten** im Abschnitt **Konfigurationseigenschaften** auf **Bereitstellung** .  
  
4.  Ändern Sie die **Database** -Eigenschaft in den neuen Datenbanknamen.  
  
     Bei der nächsten Bereitstellung des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts wird es mit diesem neuen Datenbanknamen bereitgestellt. Wenn eine Datenbank mit diesem Namen bereits vorhanden ist, wird sie überschrieben.  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a>So ändern Sie den Datenbanknamen mithilfe von SQL Server Management Studio  
  
-   Klicken Sie mit der rechten Maustaste auf die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank, und bearbeiten Sie die Eigenschaft „Name“.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servereigenschaften in Analysis Services](../server-properties/server-properties-in-analysis-services.md)   
 [Legen Sie Eigenschaften für mehrdimensionale Datenbanken &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md)   
 [Konfigurieren von Analysis Services-Projekteigenschaften &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md)   
 [Bereitstellen von Analysis Services-Projekten &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)  
  
  