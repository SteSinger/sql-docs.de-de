---
title: getTime-Methode (java.lang.String, java.util.Calendar) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTime (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 13b51f77-cec9-45fc-862e-3d2bb2d718d7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b66a142789e855eaf0e4524554892ea85c7b9cbe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979072"
---
# <a name="gettime-method-javalangstring-javautilcalendar-sqlserverresultset"></a>getTime-Methode (java.lang.String, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft unter Verwendung des Calendar-Objekts den Wert des angegebenen Spaltennamens in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.sql.Time-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Time getTime(java.lang.String colName,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *colName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
 *cal*  
  
 Ein Kalender Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Zeit Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getTime-Methode wird von der getTime-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode wird ein gültiger Uhrzeitteil eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-datetime- oder smalldatetime-Datentyps zurückgegeben. Der Datumsteil ist dabei in der im Kalender angegebenen Zeitzone auf die Java-Datumsbaseline 1.1.1970 festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getTime-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
