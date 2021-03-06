---
title: Aktualisieren von Zeilen im Rowset mit SQLSetPos | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating rows
ms.assetid: d83a8c2a-5aa8-4f19-947c-79a817167ee1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0575c7ef7e380b1157640f9927e41192838c1ac0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091598"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>Aktualisieren von Zeilen im Rowset mit SQLSetPos
Der Updatevorgang des **SQLSetPos** macht die Datenquelle, die eine oder mehrere ausgewählte Zeilen einer Tabelle, und Verwenden von Daten in die Anwendungspuffer für jede gebundene Spalte (es sei denn, der Wert in den Längen-/Indikatorpuffer SQL_COLUMN_IGNORE ist) aktualisieren. Spalten, die nicht gebunden sind, werden nicht aktualisiert werden.  
  
 Zum Aktualisieren von Zeilen mit **SQLSetPos**, die Anwendung führt Folgendes:  
  
1.  Stellen Sie die neuen Datenwerte in den Puffern Rowset. Informationen zum Senden von long-Daten mit **SQLSetPos**, finden Sie unter [Long-Daten, SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Legt den Wert in den Längen-/Indikatorpuffer für jede Spalte, nach Bedarf. Dies ist die Bytelänge der Daten oder SQL_NTS für Spalten gebunden auf Zeichenfolgepuffer,-die Bytelänge der Daten für Spalten gebunden, binärer Puffer und SQL_NULL_DATA für alle Spalten auf NULL festgelegt werden.  
  
3.  Legt den Wert in den Längen-/Indikatorpuffer dieser Spalten, die nicht in SQL_COLUMN_IGNORE aktualisiert werden. Obwohl die Anwendung kann diesen Schritt überspringen und vorhandene Daten erneut zu senden, wird dies ist ineffizient und birgt das Risiko senden die Werte an die Datenquelle, die abgeschnitten wurden, beim Lesen.  
  
4.  Aufrufe **SQLSetPos** mit *Vorgang* SQL_UPDATE festgelegt und *RowNumber* auf die Anzahl der Zeilen festgelegt, um zu aktualisieren. Wenn *RowNumber* gleich 0 ist, alle Zeilen im Rowset aktualisiert werden.  
  
 Nach dem **SQLSetPos** zurückgegeben wird, um die aktualisierte Zeile die aktuelle Zeile festgelegt ist.  
  
 Wenn alle Zeilen im Rowset zu aktualisieren ( *' RowNumber '* gleich 0 ist), eine Anwendung kann das Update von bestimmten Zeilen deaktivieren, indem Sie die entsprechenden Elemente von der Zeile Operation-Array (verweist die SQL_ATTR_ROW_OPERATION_PTR Anweisungsattribut) zu SQL_ROW_IGNORE. Die Zeile Operation-Array entspricht in Größe und Anzahl von Elementen, die die zeilenstatusarray (das Anweisungsattribut SQL_ATTR_ROW_STATUS_PTR verweist). Um nur die Zeilen im Resultset zu aktualisieren, die erfolgreich abgerufen wurden und nicht aus dem Rowset gelöscht wurden, die Anwendung verwendet die zeilenstatusarray von der Funktion, die das Rowset als das Zeile Operation-Array, das abgerufen **SQLSetPos**.  
  
 Für jede Zeile, die mit der Datenquelle als Update gesendet wird, sollte die Anwendungspuffer gültigen Zeilendaten haben. Wenn die Anwendungspuffer durch Abrufen gefüllt wurden und ein zeilenstatusarray gewahrt wurde, sollte die Werte an jeder Zeilenposition nicht SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW sein.  
  
 Im folgende Code kann beispielsweise einen Benutzer einen Bildlauf durch die Customers-Tabelle und aktualisieren, löschen oder neue Zeilen hinzufügen. Es platziert die neuen Daten in den Puffern Rowsets vor dem Aufruf **SQLSetPos** zu aktualisieren oder neue Zeilen hinzufügen. Eine zusätzliche Zeile am Ende des Rowsets Puffer in neue Zeilen eingefügt werden sollen, wird reserviert. Dadurch wird verhindert, dass vorhandene Daten überschrieben werden, wenn die Daten für eine neue Zeile in den Puffer eingefügt werden.  
  
```  
#define UPDATE_ROW   100  
#define DELETE_ROW   101  
#define ADD_ROW      102  
  
SQLUINTEGER    CustIDArray[11];  
SQLCHAR        NameArray[11][51], AddressArray[11][51],   
               PhoneArray[11][11];  
SQLINTEGER     CustIDIndArray[11], NameLenOrIndArray[11],   
               AddressLenOrIndArray[11],  
               PhoneLenOrIndArray[11];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Set the SQL_ATTR_ROW_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]), NameLenOrIndArray);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
            AddressLenOrIndArray);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmt, "SELECT CustID, Name, Address, Phone FROM Customers", SQL_NTS);  
  
// Fetch and display the first 10 rows.  
rc = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray, AddressArray,  
            AddressLenOrIndArray, PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
  
// Call GetAction to get an action and a row number from the user.  
while (GetAction(&Action, &RowNum)) {  
   switch (Action) {  
  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmt, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray,  
                     NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray,  
                     PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case UPDATE_ROW:  
         // Place the new data in the rowset buffers and update the   
         // specified row.  
         GetNewData(&CustIDArray[RowNum - 1], &CustIDIndArray[RowNum - 1],  
                  NameArray[RowNum - 1], &NameLenOrIndArray[RowNum - 1],  
                  AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                  PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
         SQLSetPos(hstmt, RowNum, SQL_UPDATE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case DELETE_ROW:  
         // Delete the specified row.  
         SQLSetPos(hstmt, RowNum, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case ADD_ROW:  
         // Place the new data in the rowset buffers at index 10.   
         // This is an extra element for new rows so rowset data is   
         // not overwritten. Insert the new row. Row 11 corresponds   
         // to index 10.  
         GetNewData(&CustIDArray[10], &CustIDIndArray[10],  
                     NameArray[10], &NameLenOrIndArray[10],  
                     AddressArray[10], &AddressLenOrIndArray[10],  
                     PhoneArray[10], &PhoneLenOrIndArray[10]);  
         SQLSetPos(hstmt, 11, SQL_ADD, SQL_LOCK_NO_CHANGE);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
