---
title: Abrufen gespeicherter Prozeduren (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a960df20b7b07bffab900589ae4d520541d720c1
ms.sourcegitcommit: 82a1ad732fb31d5fa4368c6270185c3f99827c97
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688663"
---
# <a name="call-stored-procedures-odbc"></a>Aufrufen von gespeicherten Prozeduren (ODBC)
  Wenn eine SQL-Anweisung eine gespeicherte Prozedur mithilfe der ODBC-Aufruf-Escape-Klausel aufruft, sendet der Microsoft SQL Server Treiber die Prozedur mit dem RPC-Mechanismus (remote gespeicherte Prozedur Aufruf) an SQL Server. RPC-Anforderungen umgehen größtenteils das Analysieren der Anwendungen und die Parameterverarbeitung in SQL Server und sind schneller als die Transact-SQL EXECUTE-Anweisung.  
  
 Eine Beispielanwendung, die diese Funktion veranschaulicht, finden Sie unter [Verarbeiten von Rückgabe Codes &#40;und Ausgabe&#41;Parametern (ODBC](running-stored-procedures-process-return-codes-and-output-parameters.md)).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>So führen Sie eine Prozedur als RPC aus  
  
1.  Erstellen Sie eine SQL-Anweisung, die die ODBC-Escapesequenz verwendet. Die Anweisung verwendet Parametermarkierungen für jeden Eingabe-, Eingabe/Ausgabe- und Ausgabeparameter sowie für den Prozedurrückgabewert (falls zutreffend):  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Rufen Sie [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) für jeden Eingabe-, Eingabe/Ausgabe- und Ausgabeparameter sowie für den Prozedurrückgabewert (sofern vorhanden) auf.  
  
3.  Führen Sie die Anweisung mit [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)aus.  
  
> [!NOTE]  
>  Wenn eine Anwendung eine Prozedur mit der Transact-SQL EXECUTE-Syntax (statt mit der ODBC CALL-Escapesequenz) übermittelt, gibt der SQL Server ODBC-Treiber den Prozeduraufruf an SQL Server als SQL-Anweisung statt als RPC weiter. Darüber hinaus werden Ausgabeparameter nicht zurückgegeben, wenn die Transact SQL EXECUTE-Anweisung verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 Gewusst [-wie-Themen &#40;zur Ausführung gespeicherter&#41; Prozeduren ODBC](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)   
 [Batch Verarbeitung von Aufrufen gespeicherter Prozeduren](../native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Ausführen gespeicherter Prozeduren](../native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Aufrufen einer gespeicherten Prozedur](../native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Vorgehensweisen](../native-client-odbc-queries/executing-statements/procedures.md)  
  
  
