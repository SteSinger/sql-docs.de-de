---
title: Logische Architektur (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- logical architecture [Analysis Services Multidimensional Data]
ms.assetid: 1b9cae0a-8990-4194-af5f-a1ea5f2aff06
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 074659d42e1960c5f24cf4afa20668a3d8c823b0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62725484"
---
# <a name="logical-architecture-analysis-services---multidimensional-data"></a>Logische Architektur (Analysis Services – Mehrdimensionale Daten)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] verwendet sowohl Server- und Clientkomponenten, analytische onlineverarbeitung (OLAP) und Datamining-Funktionalität für Business Intelligence-Anwendungen:  
  
-   Die Serverkomponente von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wird als Microsoft Windows-Dienst implementiert. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt mehrere Instanzen auf demselben Computer, wobei jede Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] als eine separate Instanz des Windows-Diensts implementiert.  
  
-   Clients kommunizieren mit [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] mithilfe des öffentlichen Standards für XMLA (XML for Analysis). Hierbei handelt es sich um ein SOAP-basiertes Protokoll für die Ausgabe von Befehlen und den Empfang von Antworten in Form eines Webdiensts. Clientobjektmodelle werden ebenfalls über XMLA bereitgestellt. Auf diese Modelle kann sowohl ein verwalteter Anbieter (ADOMD.NET) als auch ein eigener OLE DB-Anbieter zugreifen.  
  
-   Abfragebefehle können mithilfe der folgenden Abfragesprachen ausgegeben werden: SQL; MDX (Multidimensional Expressions), eine Abfragesprache nach Industriestandard für Analysen; oder Data Mining Extensions (DMX), eine Abfragesprache nach Industriestandard am Datamining orientierte. ASSL (Analysis Services Scripting Language) kann außerdem zum Verwalten von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenbankobjekten verwendet werden.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] unterstützt darüber hinaus eine lokale Cube-Engine, mit deren Hilfe Anwendungen auf nicht verbundenen Clients lokal gespeicherte mehrdimensionale Daten suchen können. Weitere Informationen finden Sie unter [Anforderungen an die Clientarchitektur für Analysis Services-Entwicklung](../olap-physical/client-architecture-requirements-for-analysis-services-development.md)  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 **Übersicht über logische Architektur**  
 [Übersicht über logische Architektur &#40;Analysis Services – mehrdimensionale Daten&#41;](logical-architecture-overview-analysis-services-multidimensional-data.md)  
  
 **Serverobjekte**  
 [Serverobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](server-objects-analysis-services-multidimensional-data.md)  
  
 **Datenbankobjekte**  
 [Datenbankobjekte &#40;Analysis Services – Mehrdimensionale Daten&#41;](database-objects-analysis-services-multidimensional-data.md)  
  
 **Dimensionsobjekte**  
 [-Dimensionsobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimension-objects-analysis-services-multidimensional-data.md)  
  
 **Cubeobjekte**  
 [Cubeobjekte &#40;Analysis Services – mehrdimensionale Daten&#41;](../../multidimensional-models-olap-logical-cube-objects/cube-objects-analysis-services-multidimensional-data.md)  
  
 **Sicherheit für den Benutzerzugriff**  
 [Sicherheitsarchitektur für den Benutzerzugriff](understanding-microsoft-olap-logical-architecture.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zur Microsoft OLAP-Architektur](../olap-physical/understanding-microsoft-olap-architecture.md)   
 [Physische Architektur &#40;Analysis Services – mehrdimensionale Daten&#41;](../olap-physical/understanding-microsoft-olap-physical-architecture.md)  
  
  
