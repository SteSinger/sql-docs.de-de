---
title: Tabellenwert Parameter, Werte im Arbeitsspeicher (ODBC)
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), sending data to a stored procedure with all values in memory
ms.assetid: 8b96282f-00d5-4e28-8111-0a87ae6d7781
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f6530c3b558f26e3f75f5cff63f33f2e58c119c6
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246387"
---
# <a name="sending-data-as-a-table-valued-parameter-with-all-values-in-memory-odbc"></a>Senden von Daten als Tabellenwertparameter mit allen Werten im Arbeitsspeicher (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In diesem Thema wird beschrieben, wie Daten als Tabellenwertparameter an eine gespeicherte Prozedur gesendet werden, wenn alle Werte im Speicher abgelegt sind. Ein weiteres Beispiel zur Veranschaulichung von Tabellenwert Parametern finden Sie unter [Verwenden von Tabellenwert Parametern &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/use-table-valued-parameters-odbc.md).  
  
## <a name="prerequisite"></a>Voraussetzung  
 In dieser Prozedur wird davon ausgegangen, dass der folgende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Befehl auf dem Server ausgeführt wurde:  
  
```sql
create type TVParam as table(ProdCode integer, Qty integer)  
create procedure TVPOrderEntry(@CustCode varchar(5), @Items TVPParam,   
            @OrdNo integer output, @OrdDate datetime output)  
         as   
         set @OrdDate = GETDATE();  
         insert into TVPOrd (OrdDate, CustCode)   
values (@OrdDate, @CustCode) output OrdNo);   
         select @OrdNo = SCOPE_IDENTITY();   
         insert into TVPItem (OrdNo, ProdCode, Qty)  
select @OrdNo, @Items.ProdCode, @Items.Qty   
from @Items  
```  
  
## <a name="to-send-the-data"></a>So senden Sie Daten  
  
1.  Deklarieren Sie Variablen für die SQL-Parameter. In diesem Fall ist der Tabellenwert vollständig im Speicher verfügbar. Daher werden Werte für die Spalten des Tabellenwerts als Arrays deklariert.  
  
    ```cpp
    SQLRETURN r;  
    // Variables for SQL parameters.  
    #define ITEM_ARRAY_SIZE 20  
  
    SQLCHAR CustCode[6];  
    SQLCHAR *TVP = (SQLCHAR *) "TVParam";  
    SQLINTEGER ProdCode[ITEM_ARRAY_SIZE], Qty[ITEM_ARRAY_SIZE];  
    SQLINTEGER OrdNo;  
    char OrdDate[23];  
  
    // Variables for indicator/length variables associated with parameters.  
    SQLLEN cbCustCode, cbTVP, cbProdCode[ITEM_ARRAY_SIZE], cbQty[ITEM_ARRAY_SIZE], cbOrdNo, cbOrdDate;  
    ```  
  
2.  Binden Sie die Parameter. Das Binden von Parametern ist ein Zweiphasenprozess, wenn Tabellenwertparameter verwendet werden. In der ersten Phase werden Schrittparameter für die gespeicherte Prozedur wie gewohnt gebunden:  
  
    ```cpp
    // Bind parameters for call to TVPOrderEntryDirect.  
    // 1 - Custcode input  
    r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT,SQL_VARCHAR, SQL_C_CHAR, 5, 0, CustCode, sizeof(CustCode), &cbCustCode);  
  
    // 2 - Items TVP  
    r = SQLBindParameter(hstmt,   
        2,// ParameterNumber  
        SQL_PARAM_INPUT,// InputOutputType  
        SQL_C_DEFAULT,// ValueType   
        SQL_SS_TABLE,// Parametertype  
        ITEM_ARRAY_SIZE,// ColumnSize: For a table-valued parameter this is the row array size.  
        0,// DecimalDigits: For a table-valued parameter this is always 0.   
        TVP,// ParameterValuePtr: For a table-valued parameter this is the type name of the   
    //table-valued parameter, and also a token returned by SQLParamData.  
        SQL_NTS,// BufferLength: For a table-valued parameter this is the length of the type name or SQL_NTS.  
        &cbTVP);// StrLen_or_IndPtr: For a table-valued parameter this is the number of rows actually used.  
  
    // 3 - OrdNo output  
    r = SQLBindParameter(hstmt, 3, SQL_PARAM_OUTPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, &OrdNo,  
       sizeof(SQLINTEGER), &cbOrdNo);  
    // 4 - OrdDate output  
    r = SQLBindParameter(hstmt, 4, SQL_PARAM_OUTPUT,SQL_TYPE_TIMESTAMP, SQL_C_CHAR, 23, 3, &OrdDate,   
       sizeof(OrdDate), &cbOrdDate);  
    ```  
  
3.  In der zweiten Phase der Parameterbindung erfolgt das Binden der Spalten für den Tabellenwertparameter. Der Parameterfokus wird zunächst auf die Ordnungszahl des Tabellenwertparameters festgelegt. Anschließend werden die Spalten des Tabellen Werts mit SQLBindParameter auf dieselbe Weise gebunden, wie Sie wären, wenn Sie Parameter der gespeicherten Prozedur sind, jedoch mit Spalten Ordnungen für ParameterNumber. Wenn es weitere Tabellenwertparameter gäbe, würden wir den Fokus abwechselnd auf jeden einzelnen festlegen und die jeweiligen Spalten binden. Schließlich wird der Parameterfokus auf 0 (null) zurückgesetzt.  
  
    ```cpp
    // Bind columns for the table-valued parameter (param 2).  
    // First set focus on param 2.  
    r = SQLSetStmtAttr(hstmt, SQL_SOPT_SS_PARAM_FOCUS, (SQLPOINTER) 2, SQL_IS_INTEGER);  
  
    // Col 1 - ProdCode  
    r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, ProdCode, sizeof(SQLINTEGER), cbProdCode);  
    // Col 2 - Qty  
    r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT,SQL_INTEGER, SQL_C_LONG, 0, 0, Qty, sizeof(SQLINTEGER), cbQty);  
  
    // Reset param focus.  
    r = SQLSetStmtAttr(hstmt, SQL_SOPT_SS_PARAM_FOCUS, (SQLPOINTER) 0, SQL_IS_INTEGER);  
    ```  
  
4.  Füllen Sie die Parameterpuffer auf. 
  `cbTVP` wird auf die Anzahl der an den Server zu sendenden Zeilen festgelegt.  
  
    ```cpp
    // Populate parameters.  
    cbTVP = 0; // Number of rows available for input.  
    strcpy_s((char *) CustCode, sizeof(CustCode), "CUST1"); cbCustCode = SQL_NTS;  
  
    ProdCode[cbTVP] = 1215;cbProdCode[cbTVP] = sizeof(SQLINTEGER);   
    Qty[cbTVP] = 5;cbQty[cbTVP] = sizeof(SQLINTEGER);   
    cbTVP++; // Number of rows available for input  
  
    ProdCode[cbTVP] = 1017;cbProdCode[cbTVP] = sizeof(SQLINTEGER);   
    Qty[cbTVP] = 2;cbQty[cbTVP] = sizeof(SQLINTEGER);   
    cbTVP++; // Number of rows available for input.  
    ```  
  
5.  Rufen Sie die Prozedur auf:  

    ```cpp
    // Call the procedure.  
    r = SQLExecDirect(hstmt, (SQLCHAR *) "{call TVPOrderEntry(?, ?, ?, ?)}",SQL_NTS);  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierbeispiele für ODBC-Tabellenwertparameter](https://msdn.microsoft.com/library/3f52b7a7-f2bd-4455-b79e-d015fb397726)  
  
  
