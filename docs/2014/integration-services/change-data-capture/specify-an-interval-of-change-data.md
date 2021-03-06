---
title: Angeben eines Intervalls von Änderungsdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],specifying interval
ms.assetid: 17899078-8ba3-4f40-8769-e9837dc3ec60
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2c5509699945db857bd0b763192c7aea21ac90da
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62771216"
---
# <a name="specify-an-interval-of-change-data"></a>Angeben eines Intervalls von Änderungsdaten
  In der Ablaufsteuerung eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakets, das ein inkrementelles Laden von Änderungsdaten ausführt, ist der erste Task die Berechnung der Endpunkte des Änderungsintervalls. Diese Endpunkte sind `datetime`-Werte und werden in Paketvariablen für die spätere Verwendung im Paket gespeichert.  
  
> [!NOTE]  
>  Eine Beschreibung des Gesamtprozesses zum Entwurf der Ablaufsteuerung finden Sie unter [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).  
  
## <a name="set-up-package-variables-for-the-endpoints"></a>Einrichten von Paketvariablen für die Endpunkte  
 Vor dem Konfigurieren des Tasks "SQL ausführen" zur Berechnung der Endpunkte müssen die Paketvariablen definiert werden, die die Endpunkte speichern.  
  
#### <a name="to-set-up-package-variables"></a>So richten Sie Paketvariablen ein  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]ein neues [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt.  
  
2.  Erstellen Sie im Fenster **Variablen** die folgenden Variablen:  
  
    1.  Erstellen Sie eine Variable mit dem `datetime`-Datentyp, um den Anfangspunkt für das Intervall zu speichern.  
  
         In diesem Beispiel wird der Variablenname "ExtractStartTime" verwendet.  
  
    2.  Erstellen Sie eine weitere Variable mit dem `datetime`-Datentyp, um den Endpunkt für das Intervall zu speichern.  
  
         In diesem Beispiel wird der Variablenname "ExtractEndTime" verwendet.  
  
 Wenn Sie die Endpunkte in einem Masterpaket berechnen, das mehrere untergeordnete Pakete ausführt, können Sie die Variablenkonfiguration für übergeordnete Pakete verwenden, um die Werte dieser Variablen an jedes untergeordnete Paket weiterzuleiten. Weitere Informationen finden Sie unter [Paket ausführen (Task)](../control-flow/execute-package-task.md) und [Verwenden der Werte von Variablen und Parametern in einem untergeordneten Paket](../use-the-values-of-variables-and-parameters-in-a-child-package.md).  
  
## <a name="calculate-a-starting-point-and-an-ending-point-for-change-data"></a>Berechnen eines Anfangspunkts und eines Endpunkts für Änderungsdaten  
 Nachdem Sie die Paketvariablen für die Intervallendpunkte eingerichtet haben, können Sie die Ist-Werte für diese Endpunkte berechnen und diese Werte den entsprechenden Paketvariablen zuordnen. Da diese Endpunkte `datetime`-Werte sind, müssen Sie Funktionen verwenden, die `datetime`-Werte berechnen oder mit diesen funktionieren können. Die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Ausdruckssprache und Transact-SQL verfügen über Funktionen, die mit `datetime`-Werten funktionieren:  
  
 Funktionen in der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Ausdruckssprache, die mit `datetime`-Werten funktionieren  
 -   [DATEADD &#40;SSIS-Ausdruck&#41;](../expressions/dateadd-ssis-expression.md)  
  
-   [DATEDIFF &#40;SSIS-Ausdruck&#41;](../expressions/datediff-ssis-expression.md)  
  
-   [DATEPART &#40;SSIS-Ausdruck&#41;](../expressions/datepart-ssis-expression.md)  
  
-   [DAY &#40;SSIS-Ausdruck&#41;](../expressions/day-ssis-expression.md)  
  
-   [GETDATE &#40;SSIS-Ausdruck&#41;](../expressions/getdate-ssis-expression.md)  
  
-   [GETUTCDATE &#40;SSIS-Ausdruck&#41;](../expressions/getutcdate-ssis-expression.md)  
  
-   [MONTH &#40;SSIS-Ausdruck&#41;](../expressions/month-ssis-expression.md)  
  
-   [YEAR &#40;SSIS-Ausdruck&#41;](../expressions/year-ssis-expression.md)  
  
 Funktionen in Transact-SQL, die mit `datetime`-Werten funktionieren  
 [Datums- und Uhrzeitdatentypen und zugehörige Funktionen &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).  
  
 Bevor Sie eine dieser `datetime`-Funktionen verwenden, um Endpunkte zu berechnen, müssen Sie bestimmen, ob das Intervall unveränderlich ist und regelmäßig auftritt. In der Regel möchten Sie regelmäßig in Quelltabellen aufgetretene Änderungen in Zieltabellen übernehmen. Beispielsweise möchten Sie diese Änderungen auf einer stündlichen, täglichen oder wöchentlichen Basis übernehmen.  
  
 Nachdem Sie sich darüber im Klaren sind, ob Ihr Änderungsintervall unveränderlich oder eher zufällig ist, können Sie die Endpunkte berechnen.  
  
-   **Berechnen des Startdatums und der Startzeit**. Sie verwenden das Enddatum und die Endzeit des vorherigen Ladens als aktuelles Startdatum und aktuelle Startzeit. Wenn Sie ein unveränderliches Intervall für das inkrementelle Laden verwenden, können Sie diesen Wert mit den `datetime`-Funktionen von Transact-SQL oder der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Ausdruckssprache berechnen. Andernfalls müssen Sie möglicherweise die Endpunkte zwischen den Ausführungen persistent speichern und einen Task "SQL ausführen" oder einen Skripttask verwenden, um den vorherigen Endpunkt zu laden.  
  
-   **Berechnen des Enddatums und der Endzeit**. Wenn Sie ein unveränderliches Intervall für das inkrementelle Laden verwenden, berechnen Sie das aktuelle Enddatum und die aktuelle Endzeit als Offset des Startdatums und der Startzeit. In diesem Fall können Sie diesen Wert berechnen, mit der `datetime` -Funktionen von Transact-SQL oder der die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Ausdruckssprache.  
  
 In der folgenden Prozedur verwendet das Änderungsintervall ein unveränderliches Intervall und setzt voraus, dass das Paket für inkrementelles Laden ohne Ausnahme täglich ausgeführt wird. Andernfalls würden Änderungsdaten für verpasste Intervalle verloren gehen. Der Startpunkt für das Intervall ist vorgestern Mitternacht, d. h. vor 24 bis 48 Stunden. Der Endpunkt für das Intervall ist gestern Mitternacht, d. h. in der vorherigen Nacht vor 0 bis 24 Stunden.  
  
#### <a name="to-calculate-the-starting-point-and-ending-point-for-the-capture-interval"></a>So berechnen Sie den Startpunkt und den Endpunkt für das Aufzeichnungsintervall  
  
1.  Fügen Sie auf der Registerkarte **Ablaufsteuerung** des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designers dem Paket einen Task "SQL ausführen" hinzu.  
  
2.  Öffnen Sie den **Editor für den Task 'SQL ausführen'** , und aktivieren Sie auf der Seite **Allgemein** des Editors die folgenden Optionen:  
  
    1.  Wählen Sie für **ResultSet**die Option **Einzelne Zeile**aus.  
  
    2.  Konfigurieren Sie zur Quelldatenbank eine gültige Verbindung.  
  
    3.  Wählen Sie für **SQLSourceType**die Option **Direkteingabe**aus.  
  
    4.  Geben Sie für **SQLStatement**die folgende SQL-Anweisung ein:  
  
        ```  
        SELECT DATEADD(dd,0, DATEDIFF(dd,0,GETDATE()-1)) AS ExtractStartTime,  
          DATEADD(dd,0, DATEDIFF(dd,0,GETDATE())) AS ExtractEndTime  
  
        ```  
  
3.  Ordnen Sie auf der Seite **Resultset** vom **Editor für den Task 'SQL ausführen'** der ExtractStartTime-Paketvariablen das ExtractStartTime-Ergebnis und der ExtractEndTime-Paketvariablen das ExtractEndTime-Ergebnis zu.  
  
    > [!NOTE]  
    >  Wenn Sie einen Ausdruck verwenden, um den Wert einer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Variablen festzulegen, wird der Ausdruck jedes Mal ausgewertet, wenn auf den Wert der Variablen zugegriffen wird.  
  
## <a name="next-step"></a>Nächster Schritt  
 Nachdem Sie den Startpunkt und den Endpunkt für eine Reihe von Änderungen berechnet haben, müssen Sie im nächsten Schritt bestimmen, ob die Änderungsdaten bereit sind.  
  
 **Nächstes Thema:** [Bestimmen, ob die Änderungsdaten bereit sind](determine-whether-the-change-data-is-ready.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Variablen in Paketen](../use-variables-in-packages.md)   
 [Integration Services-Ausdrücke &#40;SSIS&#41;](../expressions/integration-services-ssis-expressions.md)   
 [SQL ausführen (Task)](../control-flow/execute-sql-task.md)   
 [Skripttask](../control-flow/script-task.md)  
  
  
