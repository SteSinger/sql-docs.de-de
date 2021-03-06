---
title: Referenz zur Benutzeroberfläche (SPI) der ODBC-Service-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 88053620fa413c50a8faff4cc47cbbe1457249f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073832"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>ODBC-Dienstanbieterschnittstelle – Referenz
ODBC definiert normalerweise eine Anwendungsprogrammierschnittstelle (API). Die Funktionen der API können von Anwendungen aufgerufen werden, und sie sollten in sowohl der Treiber-Manager als auch der Treiber implementiert werden.  
  
 Durch das Hinzufügen der Funktion treiberfähiges Verbindungspooling werden in ODBC die Service Provider Interface (SPI) eingeführt. Die Funktionen in der SPI werden für die Kommunikation zwischen dem Treiber-Manager und Treiber verwendet. SPI-Funktionen werden vom Treiber implementiert. der Treiber-Manager macht keine SPI-Funktionen für Anwendungen verfügbar. Anwendungen sollten diese Funktionen nicht direkt aufrufen.  
  
 Umfassen Sie sqlspi.h für die Entwicklung von ODBC-Treiber.  
  
 Dieser Abschnitt enthält die folgenden Themen  
  
-   [SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Verbindungspooling des Treiber-Managers](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
