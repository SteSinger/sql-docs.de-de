---
title: Arbeiten mit Resultsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44eac2fbcc156b3591bdf02fd00ff0d6bd19366b
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028241"
---
# <a name="working-with-result-sets"></a>Arbeiten mit Resultsets

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Bei der Verarbeitung von Daten in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank besteht eine Methode zum Bearbeiten der Daten darin, ein Resultset zu verwenden. [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] unterstützt die Verwendung von Resultsets über das [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt. Mithilfe des SQLServerResultSet-Objekts können Sie die von einer SQL-Anweisung oder gespeicherten Prozedur zurückgegebenen Daten abrufen, die Daten bei Bedarf aktualisieren und dann wieder in der Datenbank speichern.  
  
Das SQLServerResultSet-Objekt enthält darüber hinaus Methoden, um in den Datenzeilen zu navigieren, die enthaltenen Daten abzurufen oder festzulegen und die Sensitivität gegenüber Änderungen in der zugrunde liegenden Datenbank einzurichten.  
  
> [!NOTE]  
> Weitere Informationen zum Verwalten von Resultsets, einschließlich ihrer Vertraulichkeit von Änderungen, finden Sie unter [Verwalten von Resultsets mit dem JDBC-Treiber](../../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
Die Themen in diesem Abschnitt beschreiben verschiedene Möglichkeiten, wie Sie die in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank enthaltenen Daten mithilfe von Resultsets bearbeiten können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
| Thema                                                                                           | und Beschreibung                                                                                                                                                                                             |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Abrufen von Resultsetdaten – Beispiel](../../../connect/jdbc/code-samples/retrieving-result-set-data-sample.md) | Beschreibt die Verwendung eines Resultsets, um Daten aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank abzurufen und anzuzeigen.                                                         |
| [Ändern von Resultsetdaten – Beispiel](../../../connect/jdbc/code-samples/modifying-result-set-data-sample.md)   | Beschreibt die Verwendung eines Resultsets, um Daten in eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank einzufügen, daraus abzurufen bzw. darin zu ändern.                                                      |
| [Zwischenspeichern von Resultsetdaten – Beispiel](../../../connect/jdbc/code-samples/caching-result-set-data-sample.md)       | Beschreibt die Verwendung eines Resultsets, um umfangreiche Daten aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank abzurufen, sowie die Steuerung der Zwischenspeicherung dieser Daten im Client. |
  
## <a name="see-also"></a>Siehe auch  

[Beispiele für JDBC-Treiberanwendungen](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
  
