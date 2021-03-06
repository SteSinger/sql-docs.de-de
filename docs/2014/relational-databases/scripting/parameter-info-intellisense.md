---
title: Parameterinfo (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b842f35c2852ce6ed607e943199bb322823651b9
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75242008"
---
# <a name="parameter-info-intellisense"></a>Parameterinfo (IntelliSense)
  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Option **Parameter Info** von IntelliSense öffnet eine Parameterliste, die Informationen über die Anzahl, Namen und Typen der Parameter bereitstellt, die für eine Funktion oder gespeicherte Prozedur erforderlich sind. Der fett formatierte Parameter gibt den nächsten Parameter an, der beim Eingeben einer Funktion oder gespeicherten Prozedur erforderlich ist.  
  
 Die Parameterliste wird auch für geschachtelte Funktionen angezeigt. Wenn Sie eine Funktion als Parameter für eine andere Funktion eingeben, werden in der Parameterliste die Parameter für die innere Funktion angezeigt. Wenn die Parameterliste der inneren Funktion vollständig ist, werden in der Parameterliste anschließend die Parameter der äußeren Funktion angezeigt.  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a>So zeigen Sie Parameterinfo für Funktionen oder gespeicherte Prozeduren an  
  
1.  Geben Sie nach dem Namen einer Funktion wie gewohnt eine öffnende Klammer ein, um die Parameterliste zu öffnen. Wenn Sie den Namen einer gespeicherten Prozedur eingegeben haben, geben Sie wie gewohnt ein Leerzeichen ein, um Informationen zu den Prozedurparametern abzurufen.  
  
     IntelliSense zeigt die vollständige Deklaration für die Funktion oder die Parameter für eine gespeicherte Prozedur in einem Popupfenster direkt unter der Einfügemarke an. Der erste Parameter in der Liste wird fett formatiert angezeigt.  
  
2.  Beim Eingeben der Parameter ändert sich die Fettformatierung, um den nächsten Parameter anzugeben, den Sie eingeben müssen.  
  
3.  Drücken Sie zu einem beliebigen Zeitpunkt die ESC-TASTE, um die Liste zu schließen, oder fahren Sie mit der Eingabe fort, bis die Funktion abgeschlossen ist.  
  
     Wenn Sie für eine Funktion die schließende Klammer eingeben, schließen Sie auch die Parameterliste.  
  
#### <a name="to-manually-start-parameter-info"></a>So starten Sie Parameterinfo manuell  
  
1.  Wählen Sie im Menü **Bearbeiten****IntelliSense** und anschließend **Parameterinfo**aus.  
  
2.  Drücken Sie die Tastenkombination STRG+UMSCHALT+LEERZEICHEN.  
  
 Weitere Informationen finden Sie unter [Konfigurieren von IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).  
  
> [!NOTE]  
>  Die Option **Parameter Info** ist nur für den [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Abfrage-Editor und den XML-Abfrage-Editor verfügbar.  
  
  
