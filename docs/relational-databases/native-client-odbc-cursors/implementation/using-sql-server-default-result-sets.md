---
title: Verwenden SQL Server Standard Resultsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dfd3ef8ec56f458bb57b1898a1bf7212534b7af1
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73784487"
---
# <a name="using-sql-server-default-result-sets"></a>Verwenden von SQL Server-Standardresultsets
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Die standardmäßigen ODBC-Cursorattribute sind:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Wenn diese Attribute auf ihre Standardwerte festgelegt sind, verwendet der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standard Resultset. Standardresultsets können für beliebige, von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützte SQL-Anweisungen verwendet werden und stellen die effizienteste Methode für die Übertragung des gesamten Resultsets an den Client dar.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wurde die Unterstützung für Mars (Multiple Active Result Sets) eingeführt. Anwendungen können nun über mehr als ein aktives Standard Resultset pro Verbindung verfügen. MARS ist standardmäßig nicht aktiviert.  
  
 Vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] unterstützten Standardresultsets nicht mehrere aktive Anweisungen über die gleiche Verbindung. Nach der Ausführung einer SQL-Anweisung über eine Verbindung akzeptiert der Server keine Befehle vom Client für diese Verbindung (außer der Anforderung zum Abbrechen des restlichen Resultsets), bis alle Zeilen im Resultset verarbeitet wurden. Um den Rest eines teilweise verarbeiteten Resultsets abzubrechen, rufen Sie [SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md) oder [SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md) auf, wobei der *fOption* -Parameter auf SQL_CLOSE festgelegt ist. Um ein teilweise verarbeitetes Resultset abzuschließen und auf das vorhanden sein eines anderen Resultsets zu testen, müssen Sie [SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md)aufzurufen. Wenn eine ODBC-Anwendung versucht, einen Befehl für ein Verbindungs Handle durchzuführen, bevor ein Standardresultset vollständig verarbeitet wurde, generiert der-Befehl SQL_ERROR, und ein **SQLGetDiagRec** -Befehl gibt Folgendes zurück:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Cursorn](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
