---
title: Servereigenschaften (Ausführungsseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f0ec8725a0cec9e15cb6d8402f8d654320c38471
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66099602"
---
# <a name="server-properties-execution-page"></a>Servereigenschaften (Seite Ausführung)
  Verwenden Sie diese Seite zum Festlegen eines Timeoutwertes für die Berichtsausführung. Dieser Wert gilt für alle Berichte, die von der aktuellen Berichtsserverinstanz verarbeitet werden. Sie können diesen Wert für einzelne Berichte überschreiben. Der von Ihnen angegebene Wert muss die gesamte Berichtsverarbeitung auf dem Berichtsserver berücksichtigen, plus der Abfrageverarbeitung, die auf dem Datenbankserver durchgeführt wird, wenn der Berichtsserver die im Bericht verwendeten Daten abruft.  
  
 Öffnen Sie diese Seite, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten und eine Verbindung mit einer Berichtsserverinstanz herstellen. Klicken Sie mit der rechten Maustaste auf den Namen des Berichtsservers, und wählen Sie dann **Eigenschaften**aus. Klicken Sie auf **Ausführung** , um diese Seite zu öffnen.  
  
## <a name="options"></a>Optionen  
 **Kein Timeout für eine Berichtsausführung**  
 Stellt einem Berichtsserver eine uneingeschränkte Zeitspanne für die Berichtsverarbeitung zur Verfügung.  
  
 **Berichtsausführung auf die folgende Anzahl von Sekunden beschränken**  
 Legt eine Zeitbeschränkung für die Berichtsausführung fest. Diese Zeitspanne beginnt, wenn der Bericht angefordert wird. Wenn diese Zeitspanne endet, bevor der Bericht vollständig verarbeitet wurde, bricht der Berichtsserver den Vorgang und alle in Bearbeitung befindlichen Abfragen externer Datenquellen ab.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Festlegen von Berichtsverarbeitungseigenschaften](../report-server/set-report-processing-properties.md)   
 [Festlegen von Timeoutwerten für die Verarbeitung von Berichten und freigegebenen Datasets &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)  
  
  
