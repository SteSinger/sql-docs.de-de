---
title: Features deaktivieren, wird standardmäßig (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 59c27d5f34d6e5a3f33e0f153a9077995bd99650
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66080022"
---
# <a name="features-off-by-default-analysis-services"></a>Standardmäßig deaktivierte Funktionen (Analysis Services)
  Eine Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ist standardmäßig für Sicherheit ausgelegt. Aus diesem Grund sind in der Standardeinstellung alle Funktionen deaktiviert, die sich auf die Sicherheit auswirken können. Die folgenden Funktionen sind bei der Installation deaktiviert und müssen gesondert aktiviert werden, wenn sie verwendet werden sollen:  
  
## <a name="feature-list"></a>Funktionsliste  
 Wenn Sie die folgenden Funktionen aktivieren möchten, stellen Sie eine Verbindung zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] über [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]her. Klicken Sie mit der rechten Maustaste auf den Instanznamen, und wählen Sie **Facets**aus. Alternativ können Sie diese Funktionen auch über die Servereigenschaften aktivieren. Dies wird im nächsten Abschnitt beschrieben.  
  
-   Ad-Hoc-Data-Mining-Abfragen (OpenRowset)  
  
-   Verknüpfte Objekte (An)  
  
-   Verknüpfte Objekte (Von)  
  
-   Nur lokale Verbindungen überwachen  
  
-   Benutzerdefinierte Funktionen  
  
## <a name="server-properties"></a>Servereigenschaften  
 Zusätzliche standardmäßig deaktivierte Funktionen können Sie über die Servereigenschaften aktivieren. Stellen Sie eine Verbindung zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] über [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]her. Klicken Sie mit der rechten Maustaste auf den Instanznamen, und wählen Sie **Eigenschaften**aus. Klicken Sie auf **Allgemein**, und klicken Sie dann auf **Show Advanced** , um eine umfangreichere Liste mit Eigenschaften anzuzeigen.  
  
-   Ad-Hoc-Data-Mining-Abfragen (OpenRowset)  
  
-   Sitzungsminingmodelle zulassen (Data Mining)  
  
-   Verknüpfte Objekte (An)  
  
-   Verknüpfte Objekte (Von)  
  
-   COM-basierte benutzerdefinierte Funktionen  
  
-   Ablaufverfolgungsdefinitionen (Vorlagen).  
  
-   Abfrageprotokollierung  
  
-   Nur lokale Verbindungen überwachen  
  
-   Binäres XML  
  
-   Komprimierung  
  
-   Gruppenaffinität. Einzelheiten dazu finden Sie unter [Thread Pool Properties](../server-properties/thread-pool-properties.md) .  
  
  
