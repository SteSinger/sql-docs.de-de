---
title: Filter generieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cae79be898c326b395e781db741c87578edfe7ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721279"
---
# <a name="generate-filters"></a>Filter generieren
  Mithilfe des Dialogfelds **Filter generieren** können Sie einen Zeilenfilter für eine Tabelle in einer Mergeveröffentlichung definieren. Die Replikation erweitert dann den Filter automatisch auf andere Tabellen, die durch Fremdschlüsselbeziehungen verbunden sind. Wenn Sie z. B. einen Filter für eine Kundentabelle so definieren, dass diese nur Daten zu französischen Kunden enthält, dann erweitert die Replikation den Filter derart, dass verknüpfte Tabellen mit Bestellungen und Bestellungsdetails nur Informationen enthalten, die sich auf französische Kunden beziehen.  
  
## <a name="options"></a>Optionen  
 Dieses Dialogfeld enthält einen dreistufigen Vorgang zum Erstellen eines Zeilenfilters für eine Tabelle. Der Filter wird dann auf die Tabellen erweitert, die mit der gefilterten Tabelle über Primärschlüssel- und Fremdschlüsselbeziehungen verknüpft sind. Wenn z. B. drei Tabellen gegeben sind, **Customer**, **SalesOrderHeader**und **SalesOrderDetail**, mit einer Beziehung zwischen **Customer** und **SalesOrderHeader**sowie einer Beziehung zwischen **SalesOrderHeader** und **SalesOrderDetail**, dann können Sie einen Zeilenfilter auf **Customer**anwenden, und die Replikation erweitert diesen Filter auf **SalesOrderHeader** und **SalesOrderDetail**.  
  
1.  **Wählen Sie die zu filternde Tabelle aus.**  
  
     Wählen Sie eine Tabelle aus dem Dropdownlistenfeld aus. Tabellen werden im Listenfeld nur dann angezeigt, wenn sie auf der Seite **Artikel** ausgewählt wurden.  
  
2.  **Vervollständigen Sie die Filteranweisung, um die von Abonnenten empfangenen Tabellenzeilen zu identifizieren.**  
  
     Definieren Sie eine neue Filteranweisung. Im Listenfeld **Spalten** werden alle Spalten aufgeführt, die Sie aus einer in **Wählen Sie die zu filternde Tabelle aus**ausgewählten Tabelle veröffentlichen. Der Textbereich **Filteranweisung** enthält den Standardtext im folgenden Format:  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     Der Text kann nicht geändert werden. Geben Sie die Filterklausel nach dem WHERE-Schlüsselwort mithilfe der standardmäßigen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Syntax ein.  
  
    > [!IMPORTANT]  
    >  Aus Leistungsgründen ist es empfehlenswert, keine Funktionen auf Spaltennamen in Klauseln für parametrisierte Zeilenfilter anzuwenden, wie z. B. `LEFT([MyColumn]) = SUSER_SNAME()`. Wenn Sie HOST_NAME in einer Filterklausel verwenden und den HOST_NAME-Wert überschreiben, müssen Datentypen eventuell mit CONVERT konvertiert werden. Weitere Informationen zu bewährten Methoden für diesen Fall finden Sie im Abschnitt über das Überschreiben des HOST_NAME()-Werts im Thema [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
3.  **Geben Sie an, wie viele Abonnements Daten aus dieser Tabelle empfangen.**  
  
     Nur in[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höheren Versionen. Mithilfe von Mergereplikationen können Sie den für Ihre Daten und Ihre Anwendung am besten geeigneten Partitionstyp angeben. Wenn Sie **Eine Zeile aus dieser Tabelle wird nur an ein Abonnement gesendet**auswählen, legt die Mergereplikation die Option für nicht überlappende Partitionen fest. Nicht überlappende Partitionen arbeiten zur Leistungsverbesserung mit vorausberechneten Partitionen zusammen, wobei nicht überlappende Partitionen die bei vorausberechneten Partitionen entstehenden Uploadkosten minimieren. Die Leistungsvorteile nicht überlappender Partitionen treten deutlicher hervor, wenn die verwendeten parametrisierten Filter und Joinfilter komplexer sind. Bei Auswahl dieser Option müssen Sie jedoch sicherstellen, dass die Daten so partitioniert werden, dass eine Zeile nicht für mehrere Abonnenten repliziert werden kann. Weitere Informationen finden Sie im Abschnitt zum Festlegen von Partitionsoptionen unter [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).  
  
 Nachdem Sie einen Filter hinzugefügt haben, klicken Sie auf **OK** , um das Dialogfeld zu schließen. Der von Ihnen angegebene Filter wird analysiert und für die Tabelle in der SELECT-Klausel ausgeführt. Wenn die Filteranweisung Syntaxfehler oder andere Probleme enthält, werden Sie benachrichtigt und können die Filteranweisung bearbeiten.  
  
 Nachdem die Anweisung analysiert ist, erstellt die Replikation die erforderlichen Joinfilter. Wenn Sie bis jetzt für den Verleger, für den der Assistent ausgeführt wird, den Verteiler nicht konfiguriert haben, werden Sie jetzt aufgefordert, ihn zu konfigurieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Create a Publication](publish/create-a-publication.md)   
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](publish/view-and-modify-publication-properties.md)   
 [Filtern von veröffentlichten Daten](publish/filter-published-data.md)   
 [Join Filters](merge/join-filters.md)   
 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish/publish-data-and-database-objects.md)  
  
  
