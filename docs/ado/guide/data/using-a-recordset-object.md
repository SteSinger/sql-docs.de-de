---
title: Mit einem Recordset-Objekt | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 01c630d8-eb35-4bd0-a99f-7c0f85316cc1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dda89464598ddc4ecfee0078b36aadd01b4486f5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923631"
---
# <a name="using-a-recordset-object"></a>Verwenden eines Recordset-Objekts
Alternativ können Sie **Recordset.Open** , implizit eine Verbindung herzustellen, und geben Sie einen Befehl über diese Verbindung in einem einzigen Vorgang. Z. B. in Visual Basic:  
  
```  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
  
' Create and Open the Recordset object.  
Set oRs = New ADODB.Recordset  
oRs.CursorLocation = adUseClient  
oRs.Open sSQL, sConn, adOpenStatic, _  
               adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
oRs.Close          
Set oRs = Nothing  
```  
  
 Beachten Sie, dass **oRs.Open** nimmt eine Verbindungszeichenfolge (*sConn*), anstelle von einem **Verbindung** Objekt (*oConn*), als Wert für die  **ActiveConnection** Parameter. Auch der clientseitigen Cursor-Typ wird erzwungen, indem die **CursorLocation** Eigenschaft für die **Recordset** Objekt. Vergleichen Sie dies mit in diesem Fall die **HelloData** Beispiel.
