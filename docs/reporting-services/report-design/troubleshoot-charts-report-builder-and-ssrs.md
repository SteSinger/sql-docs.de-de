---
title: Problembehandlung bei Diagrammen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 365128fe0fd67f1b270481f827eef6871acccb5d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65573742"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Problembehandlung bei Diagrammen (Berichts-Generator und SSRS)
  Beim Arbeiten mit Diagrammen können diese Punkte hilfreich sein.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Warum zählt das Diagramm die Werte auf der Wertachse, statt sie zu addieren?  
 Die meisten Diagrammtypen erfordern numerische Werte an der Wertachse (normalerweise der y-Achse), damit sie ordnungsgemäß gezeichnet werden. Wenn der Datentyp des Wertfelds **String**lautet, kann das Diagramm keinen numerischen Wert anzeigen, selbst wenn sich in den Feldern Zahlen befinden. Stattdessen zeigt das Diagramm die Anzahl der Zeilen an, die in diesem Feld einen Wert enthalten. Zur Vermeidung dieses Verhaltens sollten Sie sicherstellen, dass die Felder, die Sie für Wertereihen verwenden, numerische Datentypen und keine Zeichenfolgen mit formatierten Zahlen aufweisen.  

## <a name="need-more-help"></a>Benötigen Sie weitere Hilfe?  
   
  Versuchen Sie Folgendes:  
 * [SQL Server Reporting Services](https://stackoverflow.com/questions/tagged/reporting-services) auf Stack Overflow  
 * Melden Sie ein Problem, oder machen Sie einen Vorschlag unter [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
