---
title: Festlegen der Datenquellen Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0b3093b87557917655fcbfd6cf7c2ec37151ca44
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027729"
---
# <a name="setting-the-data-source-properties"></a>Festlegen der Datenquelleneigenschaften

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Datenquellen bilden den bevorzugten Mechanismus, mit dem in einer Umgebung der Java-Plattform, Enterprise Edition (Java EE) JDBC-Verbindungen erstellt werden. Datenquellen ermöglichen Verbindungen, Poolverbindungen und verteilte Verbindungen, ohne die Verbindungseigenschaften fest im Java-Code codieren zu müssen. Alle Datenquellen für [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] können alle Eigenschaften mit den entsprechenden Setter- oder Getter-Methoden abrufen bzw. festlegen.

Java EE-Produkte wie Anwendungsserver und Servlet-/JSP-Engines lassen normalerweise die Konfiguration von Datenquellen für den Datenbankzugriff zu. Alle im Artikel [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md) aufgeführten Eigenschaften können überall angegeben werden, wo die Konfiguration die Eingabe einer Eigenschaft als Eigenschaft-Wert-Paar zulässt.

Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquellen finden Sie unter der [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)-Klasse. Ein Beispiel für die Verwendung der SQLServerDataSource-Klasse, um eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank herzustellen, finden Sie unter [Datenquellen Beispiel](../../connect/jdbc/data-source-sample.md).

## <a name="see-also"></a>Siehe auch

[Verbinden mit SQL Server mit dem JDBC-Treiber](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
