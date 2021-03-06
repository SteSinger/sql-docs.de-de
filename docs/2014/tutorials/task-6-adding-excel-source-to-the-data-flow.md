---
title: 'Aufgabe 6: Hinzufügen der Excel-Quelle zum Datenfluss | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 92a4c3e650ce375a1e80079bbad83c5ab2b9bcd9
ms.sourcegitcommit: 63c6f3758aaacb8b72462c2002282d3582460e0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68495292"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a>Aufgabe 6: Hinzufügen der Excel-Quelle zum Datenfluss
  In dieser Aufgabe fügen Sie dem Datenfluss eine Excel-Quelle hinzu, um Lieferantendaten aus der Excel-Quelldatei zu lesen. Die Excel-Quelle extrahiert Daten aus Arbeitsblättern oder Bereichen in Microsoft Excel-Arbeitsmappen. Weitere Informationen finden Sie im Thema [Excel-Quelle](../integration-services/data-flow/excel-source.md) .  
  
1.  Ziehen Sie **Excel-Quelle** aus **anderen Quellen** in der **SSIS-Toolbox** auf die Registerkarte **Datenfluss** .  
  
2.  Klicken Sie in der Registerkarte **Datenfluss** mit der rechten Maustaste auf **Excel-Quelle** , und klicken Sie auf **Umbenennen**  
  
3.  Geben **Sie Lieferantendaten aus Excel-Datei lesen** ein, und drücken **Sie Eingabe**.  
  
4.  Doppelklicken Sie auf **Lieferantendaten aus Excel-Datei lesen** , um das Dialogfeld **Quellen-Editor für Excel** zu öffnen.  
  
5.  Klicken Sie im Dialogfeld **Quellen-Editor für Excel** auf **neu** , um eine Excel-Verbindung zu erstellen.  
  
6.  Klicken Sie im Dialogfeld **Excel-Verbindungs-Manager** auf **Durchsuchen**, und wählen Sie dann im Ordner **EIM Tutorial** die Datei **Suppliers. xls** aus. Vergewissern Sie sich, dass im Feld Excel- **Version** **Microsoft Excel 97-2003** ausgewählt ist, und klicken Sie dann auf **OK**.  
  
     ![Dialog Feld "Verbindungs-Manager für Excel](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Dialog Feld \"Verbindungs-Manager für Excel")  
  
7.  Wählen Sie im Dialogfeld **Quellen-Editor für Excel** im Listenfeld Name der Excel- **Tabelle** den Wert **incomingsuppliers $** aus.  
  
     ![Name der Excel-Tabelle-eingehende Lieferanten $](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Name der Excel-Tabelle-eingehende Lieferanten $")  
  
8.  Klicken Sie auf **Vorschau** , um die Daten in der Excel-Datei anzuzeigen.  
  
9. Klicken Sie auf **OK**, um das Dialogfeld zu schließen.  
  
10. Ziehen Sie die Transformation für die **DQS** -Bereinigung in **andere Transformationen** der **SSIS-Toolbox** auf die Registerkarte **Datenfluss** unter **Lieferantendaten aus Excel-Datei lesen**. Die DQS-Bereinigungstransformation verwendet Data Quality Services (DQS), um die Daten zu korrigieren, indem sie genehmigte Regeln in der Wissensdatenbank anwendet. Diese Transformation erstellt zur Laufzeit ein DQS-Bereinigungsprojekt auf dem DQS-Server. Weitere Informationen finden Sie im Thema zur [Transformation der DQS](https://msdn.microsoft.com/library/ee677619.aspx) -Bereinigung.  
  
## <a name="next-step"></a>Nächster Schritt

[Aufgabe 7: Hinzufügen der Transformation für die DQS-Bereinigung zum Datenfluss](task-7-adding-dqs-cleansing-transform-to-the-data-flow.md)  

### <a name="see-also"></a>Siehe auch

[Datenfluss](../integration-services/data-flow/data-flow.md)  
