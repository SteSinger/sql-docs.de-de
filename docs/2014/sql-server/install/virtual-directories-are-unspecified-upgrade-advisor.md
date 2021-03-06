---
title: Virtuelle Verzeichnisse sind nicht angegeben (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 7d32b560-49d6-4558-b5d6-9127067f82d6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c9ee7f745fc683a9ed93f2ca09ac94e1bf580f71
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952380"
---
# <a name="virtual-directories-are-unspecified-upgrade-advisor"></a>Virtuelle Verzeichnisse sind nicht angegeben (Upgrade Advisor)
  Upgrade Advisor hat keine Einstellungen für virtuelle Verzeichnisse des Report Server-Webdiensts oder des Berichts-Managers erkannt. Nach dem Abschluss des Upgrades müssen Sie URL-Reservierungen für den Berichtsserver konfigurieren, indem Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager verwenden.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Beschreibung  
 Das Upgrade einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Installation beinhaltet das Reservieren neuer URLs für den Report Server-Webdienst und den Berichts-Manager. Der Upgrade Advisor hat für die zu aktualisierende Instanz keine virtuellen Verzeichnisse für den Berichtsserver oder den Berichts-Manager erkannt. Der Upgradeprozess verfügt somit nicht über ausreichende Informationen, um URL-Reservierungen für den aktualisierten Berichtsserver zu erstellen. Das Upgrade kann fortgesetzt werden, jedoch ist das virtuelle Verzeichnis des Berichtsservers oder Berichts-Managers erst nach der Upgradeinstallation definiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie nach Abschluss des Upgrades den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Konfigurations-Manager, um die URLs für den Berichtsserver und den Berichts-Manager festzulegen. Verwenden Sie den IIS-Manager, um ggf. alle virtuellen Verzeichnisse zu entfernen, die Sie nicht mehr benötigen.  
  
 Weitere Informationen finden Sie unter [Konfigurieren einer URL &#40;SSRS Configuration Manager&#41; ](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Online Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgrade Advisor für &#40;Reporting Services Upgradeprobleme&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
