---
title: Vorbereiten des Massenimports von Daten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], about bulk importing
- BULK INSERT statement, guidelines
- BULK INSERT statement, restrictions
- bcp utility [SQL Server], guidelines
- bcp utility [SQL Server], restrictions
- hidden characters
- OPENROWSET function, BCP guidelines
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95deda34b673161bf63c29a912564f39425583a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011858"
---
# <a name="prepare-to-bulk-import-data-sql-server"></a>Vorbereiten des Massenimports von Daten (SQL Server)
  Sie können den Befehl **bcp** , die BULK INSERT-Anweisung oder die OPENROWSET(BULK)-Funktion nur für den Massenimport von Daten aus einer Datendatei verwenden.  
  
> [!NOTE]  
>  Es ist möglich, eine benutzerdefinierte Anwendung zu schreiben, die einen Massenimport von Daten von anderen Objekten als einer Textdatei durchführt. Für einen Massenimport von Daten aus Speicherpuffern verwenden Sie entweder die BCP-Erweiterungen in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC)-API (Application Programming Interface) oder der OLE DB-Schnittstelle **IRowsetFastLoad** .  Für den Massenimport von Daten aus einer C#-Datentabelle verwenden Sie die ADO.NET-API für Massenkopiervorgänge **SqlBulkCopy**.  
  
> [!NOTE]  
>  Der Massenimport von Daten in eine Remotetabelle wird nicht unterstützt.  
  
 Befolgen Sie beim Massenimport von Daten aus einer Datendatei in eine Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]diese Richtlinien:  
  
-   Erlangen Sie die erforderlichen Berechtigungen für Ihr Benutzerkonto.  
  
     Das Benutzerkonto, in dem Sie das Hilfsprogramm **bcp**, die BULK INSERT-Anweisung oder die INSERT ... SELECT * FROM OPENROWSET(BULK...)-Anweisung verwenden, muss über die erforderlichen Berechtigungen für die Tabelle verfügen (zugewiesen vom Tabellenbesitzer). Weitere Informationen zu den Berechtigungen, die von jeder Methode benötigt werden, finden Sie unter [bcp (Hilfsprogramm)](../../tools/bcp-utility.md), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) und [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
-   Verwenden Sie das massenprotokollierte Wiederherstellungsmodell.  
  
     Diese Richtlinie gilt für eine Datenbank, die das vollständige Wiederherstellungsmodell verwendet. Das massenprotokollierte Wiederherstellungsmodell ist beim Ausführen von Massenvorgängen in einer nicht indizierten Tabelle von Nutzen (in einem *Heap*). Mit der massenprotokollierten Wiederherstellung wird verhindert, dass der Speicherplatz des Transaktionsprotokolls vollständig belegt wird, weil Zeileneinfügungen im Protokoll von der massenprotokollierten Wiederherstellung nicht ausgeführt werden. Weitere Informationen zum massenprotokollierten Wiederherstellungsmodell finden Sie unter [Wiederherstellungsmodelle &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md).  
  
     Es wird empfohlen, für die Datenbank unmittelbar vor dem Massenimportvorgang die Verwendung des massenprotokollierten Wiederherstellungsmodells festzulegen. Unmittelbar danach sollten Sie die Datenbank wieder auf das vollständige Wiederherstellungsmodell zurücksetzen. Weitere Informationen finden Sie unter [Anzeigen oder Ändern des Wiederherstellungsmodells einer Datenbank &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
    > [!NOTE]  
    >  Weitere Informationen zur minimalen Protokollierung während Massenimportvorgängen finden Sie unter [Voraussetzungen für die minimale Protokollierung beim Massenimport](prerequisites-for-minimal-logging-in-bulk-import.md).  
  
-   Führen Sie nach dem Massenimport von Daten eine Sicherung aus.  
  
     Für eine Datenbank, die das einfache Wiederherstellungsmodell verwendet, sollten Sie eine vollständige oder eine differenzielle Sicherung ausführen, nachdem der Massenimportvorgang abgeschlossen ist. Weitere Informationen finden Sie unter [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) und [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md).  
  
     Für das massenprotokollierte Wiederherstellungsmodell oder das vollständige Wiederherstellungsmodell ist eine Protokollsicherung ausreichend. Weitere Informationen finden Sie unter [Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md).  
  
-   Löschen Sie Tabellenindizes, um die Leistung bei großen Massenimporten zu verbessern.  
  
     Diese Richtlinie gilt für Situationen, in denen Sie im Vergleich zu den bereits in der Tabelle enthaltenen Datenmengen eine sehr große Datenmenge importieren. In diesem Fall kann das Löschen der Indizes aus der Tabelle vor dem Ausführen des Massenimportvorgangs die Leistung erheblich steigern.  
  
    > [!NOTE]  
    >  Wenn Sie hingegen eine kleine Menge an Daten (im Vergleich zur Menge der bereits in der Tabelle enthaltenen Daten) laden möchten, ist das Löschen der Indizes kontraproduktiv. Das erneute Erstellen dieser Indizes könnte länger dauern als die Zeitersparnis durch den Massenimportvorgang.  
  
-   Suchen und entfernen Sie verborgene Zeichen in der Datendatei.  
  
     Viele Hilfsprogramme und Text-Editoren zeigen ausgeblendete Zeichen an, die sich in der Regel am Ende der Datendatei befinden. Ausgeblendete Zeichen in einer ASCII-Datendatei können während eines Massenimportvorgangs Probleme verursachen. Dies kann zu einer Fehlermeldung führen, in der das Auffinden einer unerwarteten Null gemeldet wird. Sie können das Problem normalerweise lösen, wenn Sie alle ausgeblendeten Zeichen suchen und entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Importieren und Exportieren von Massendaten mithilfe des bcp-Hilfsprogramms &#40;SQL Server&#41;](import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)   
 [Importieren von Massendaten mithilfe von BULK INSERT oder OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Datenformate für Massenimport oder Massenexport &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)  
  
  
