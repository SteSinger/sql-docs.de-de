---
title: Verteilerinformationen, Agents | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.commonjobs.f1
ms.assetid: 2346c00d-c269-45a1-af14-68e7fd7ebd7e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9094fcbbede4c9bb6bac283129ed20ea4e3e910b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261755"
---
# <a name="publisher-information-agents"></a>Verlegerinformationen, Agents
  Auf der Registerkarte **Agents** werden Informationen zu den Agents und Wartungsaufträgen angezeigt, die dem Verleger zugeordnet sind:  
  
-   Momentaufnahme-Agent, der für alle Veröffentlichungen angezeigt wird  
  
-   Protokolllese-Agent, der für alle Transaktionsveröffentlichungen angezeigt wird  
  
-   Warteschlangenlese-Agent, der für Transaktionsveröffentlichungen angezeigt wird, die für Abonnements mit verzögertem Update über eine Warteschlange aktiviert sind  
  
-   Für alle Veröffentlichungen angezeigte Wartungsaufträge:  
  
    -   Neuinitialisierung von Abonnements mit Datenüberprüfungsfehlern  
  
    -   Agentverlaufscleanup: Verteilung  
  
    -   Aktualisierung für die Replikationsüberwachung für die Verteilung  
  
    -   Überprüfung des Replikations-Agents  
  
    -   Verteilungscleanup: Verteilung  
  
    -   Cleanup abgelaufener Abonnements  
  
 Weitere Informationen zu diesen Aufträgen finden Sie unter [Replikations-Agent-Verwaltung](agents/replication-agent-administration.md).  
  
## <a name="options"></a>Optionen  
 Wählen Sie zum Anzeigen von Informationen zu einem Agent oder Auftrag eine Option im Dropdownmenü **Agent- und Auftragstypen** aus. Ausführliche Informationen und die Tasks für einen Agent oder Auftrag können Sie anzeigen, indem Sie mit der rechten Maustaste in die Zeile des jeweiligen Agents oder Auftrags klicken und eine Option im Kontextmenü auswählen. Wenn Sie die Anzeige der Daten im Raster ändern möchten, klicken Sie mit der rechten Maustaste auf das Raster, und klicken Sie anschließend auf eine der folgenden Optionen:  
  
-   **Sortieren:** Sortieren Sie nach einer oder mehreren Spalten im Dialogfeld **Spalten sortieren**.  
  
-   **Anzuzeigende Spalten auswählen:** Wählen Sie die anzuzeigenden Spalten sowie die Reihenfolge aus, in der diese im Dialogfeld **Spalten auswählen** angezeigt werden sollen.  
  
-   **Filtern:** Filtern Sie Zeilen im Raster auf Grundlage der Spaltenwerte im Dialogfeld **Filtereinstellungen**.  
  
-   **Filter löschen:** Löschen Sie alle Filtereinstellungen für das Raster.  
  
 Filtereinstellungen sind rasterspezifisch. Die Spaltenauswahl und -sortierung wird auf alle Raster desselben Typs angewendet, z. B. das Veröffentlichungsraster für jeden Verleger.  
  
 In den folgenden Abschnitten werden in den Daten beschrieben, die auf dieser Registerkarte für jeden Agent oder Auftrag angezeigt werden.  
  
### <a name="snapshot-agent"></a>Momentaufnahme-Agent  
 **Status**  
 Der Status des Agents. In der folgenden Liste sind die möglichen Statuswerte aufgeführt:  
  
-   Fehler  
  
-   Wiederholen  
  
-   Wird ausgeführt  
  
-   Abgeschlossen  
  
 **Veröffentlichung**  
 Der Name der Veröffentlichung, der der Agent zugeordnet ist.  
  
 **Letzte Startzeit**  
 Zeitpunkt, zu dem der Agent beim letzten Mal gestartet wurde.  
  
 **Dauer**  
 Zeitdauer, für die der Agent ausgeführt wurde. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit ausgeführten Agents oder die Gesamtzeit des zuvor ausgeführten Agents an.  
  
 **Letzte Aktion**  
 Die letzte Aktion, die bei der letzten Ausführung des Agents ausgeführt wurde.  
  
 **Übermittlungsrate**  
 Die Rate (in Befehlen pro Sekunde), mit der bei der letzten Ausführung des Agents für Initialisierungsbefehle ein Commit in der Verteilungsdatenbank ausgeführt wurde.  
  
 **#Trans**  
 Die Anzahl von Transaktionen, für die bei der letzten Ausführung des Agents ein Commit in der Verteilungsdatenbank ausgeführt wurde.  
  
 **#Cmds**  
 Die Anzahl von Befehlen, für die bei der letzten Ausführung des Agents ein Commit in der Verteilungsdatenbank ausgeführt wurde. Ein Befehl entspricht einer Datenänderung, z. B. einem Update.  
  
### <a name="log-reader-agent"></a>Protokolllese-Agent  
 **Status**  
 Der Status des Agents. In der folgenden Liste sind die möglichen Statuswerte aufgeführt:  
  
-   Fehler  
  
-   Wiederholen  
  
-   Wird ausgeführt  
  
-   Wird nicht ausgeführt  
  
 **Veröffentlichungsdatenbank**  
 Der Name der Veröffentlichung, der der Agent zugeordnet ist.  
  
 **Letzte Startzeit**  
 Zeitpunkt, zu dem der Agent beim letzten Mal gestartet wurde.  
  
 **Dauer**  
 Zeitdauer, für die der Agent ausgeführt wurde. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit ausgeführten Agents oder die Gesamtzeit des zuvor ausgeführten Agents an.  
  
 **Letzte Aktion**  
 Die letzte Aktion, die bei der letzten Ausführung des Agents ausgeführt wurde.  
  
 **Übermittlungsrate**  
 Die Rate (in Befehlen pro Sekunde), mit der für Änderungen ein Commit in der Verteilungsdatenbank ausgeführt wird.  
  
 **Latenzzeit**  
 Die verstrichene Zeit in Sekunden zwischen dem Commit der letzten Änderung in der Veröffentlichungsdatenbank und dem Commit des zugehörigen Befehls in der Verteilungsdatenbank.  
  
 **#Trans**  
 Die Anzahl von Transaktionen, für die bei der letzten Ausführung des Agents ein Commit in der Verteilungsdatenbank ausgeführt wurde.  
  
 **#Cmds**  
 Die Anzahl von Befehlen, für die bei der letzten Ausführung des Agents ein Commit in der Verteilungsdatenbank ausgeführt wurde. Ein Befehl entspricht einer Datenänderung, z. B. einem Update.  
  
 **Durchschn. Anzahl der Befehle**  
 Die durchschnittliche Anzahl von Befehlen pro Transaktion bei der letzten Ausführung des Agents.  
  
### <a name="queue-reader-agent"></a>Warteschlangenlese-Agent  
 **Status**  
 Der Status des Agents. In der folgenden Liste sind die möglichen Statuswerte aufgeführt:  
  
-   Fehler  
  
-   Wiederholen  
  
-   Wird ausgeführt  
  
-   Wird nicht ausgeführt  
  
 **Verteilungsdatenbank**  
 Der Name der Verteilungsdatenbank, der der Agent zugeordnet ist.  
  
 **Letzte Startzeit**  
 Zeitpunkt, zu dem der Agent beim letzten Mal gestartet wurde.  
  
 **Dauer**  
 Zeitdauer, für die der Agent ausgeführt wurde. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit ausgeführten Agents oder die Gesamtzeit des zuvor ausgeführten Agents an.  
  
 **Letzte Aktion**  
 Die letzte Aktion, die bei der letzten Ausführung des Agents ausgeführt wurde.  
  
 **Übermittlungsrate**  
 Die Rate (in Befehlen pro Sekunde), mit der für Änderungen ein Commit in der Verteilungsdatenbank ausgeführt wird.  
  
 **Latenzzeit**  
 Die verstrichene Zeit in Sekunden zwischen dem Commit der letzten Änderung in einer Abonnementdatenbank und dem Commit des zugehörigen Befehls in der Veröffentlichungsdatenbank.  
  
 **#Trans**  
 Die Anzahl von Transaktionen, für die bei der letzten Ausführung des Agents ein Commit in der Veröffentlichungsdatenbank ausgeführt wurde.  
  
 **#Cmds**  
 Die Anzahl von Befehlen, für die bei der letzten Ausführung des Agents ein Commit in der Veröffentlichungsdatenbank ausgeführt wurde. Ein Befehl entspricht einer Datenänderung, z. B. einem Update.  
  
 **Durchschn. Anzahl der Befehle**  
 Die durchschnittliche Anzahl von Befehlen pro Transaktion bei der letzten Ausführung des Agents.  
  
### <a name="maintenance-jobs"></a>Wartungsaufträge  
 **Status**  
 Status des jeweilige Auftrags. In der folgenden Liste sind die möglichen Statuswerte aufgeführt:  
  
-   Fehler  
  
-   Wiederholen  
  
-   Wird ausgeführt  
  
-   Wird nicht ausgeführt  
  
 **Auftrag**  
 Der Name des Auftrags.  
  
 **Letzte Startzeit**  
 Zeitpunkt, zu dem der Auftrag beim letzten Mal gestartet wurde.  
  
 **Dauer**  
 Dauer der Auftragsausführung. Dieser Wert gibt entweder die verstrichene Zeit eines zurzeit ausgeführten Auftrags oder die Gesamtzeit eines zuvor ausgeführten Auftrags an.  
  
 **Letzte Aktion**  
 Die letzte Aktion, die bei der letzten Ausführung des Auftrags ausgeführt wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten des Replikationsmonitors](monitor/start-the-replication-monitor.md)   
 [View information and perform tasks using Replication Monitor (Anzeigen von Informationen und Ausführen von Aufgaben mit dem Replikationsmonitor)](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Überwachen der Replikation](monitoring-replication.md)  
  
  
