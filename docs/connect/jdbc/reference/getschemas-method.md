---
title: GetSchemas-Methode () | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSchemas
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: adba0ee6-ff6d-4215-b646-62c735be3fe9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0a5f453e6300258cacffa6606259f85cdd25977
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980081"
---
# <a name="getschemas-method-"></a>getSchemas-Methode ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Schemanamen ab, die in der aktuellen Datenbank verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getSchemas()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getSchemas-Methode wird von der getSchemas-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das Resultset, das von der GetSchemas-Methode zurückgegeben wird, enthält die folgenden Informationen:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**String**|Der Name des Schemas.|  
|TABLE_CATALOG|**String**|Der Katalogname für das Schema.|  
  
 Die Ergebnisse werden nach "TABLE_CATALOG" und anschließend nach "TABLE_SCHEM" sortiert. In jeder Zeile bildet "TABLE_SCHEM" die erste Spalte und "TABLE_CATALOG" die zweite Spalte.  
  
> [!NOTE]  
>  Weitere Informationen zu den Daten, die von der getSchemas-Methode zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „sys.schemas (Transact-SQL)“.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der getSchemas-Methode Informationen zum Katalog und den ihm zugeordneten Schemanamen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben werden können, wenn die zu verwendende Datenbank durch das connection-Argument angegeben wird.  
  
```  
public static void executeGetSchemas(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getSchemas();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
