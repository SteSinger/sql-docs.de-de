---
title: Verbesserungen bei Datum und Uhrzeit | Microsoft-Dokumentation
description: Datums-und Uhrzeit Verbesserungen in OLE DB Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 170404a4f90be10c848c8f15b7663c330f67495a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989123"
---
# <a name="date-and-time-improvements"></a>Verbesserungen bei Datum und Uhrzeit
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In diesem Thema wird der OLE DB-Treiber für die SQL Server Unterstützung der in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]hinzugefügten Datums-und Uhrzeit Datentypen beschrieben.  
  
 Weitere Informationen zu Datum/Uhrzeit-Verbesserungen finden Sie unter [Verb &#40;esse&#41;rungen bei Datum und Uhrzeit OLE DB](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md).  
  
 Informationen zu Beispielanwendungen, die diese Funktion veranschaulichen, finden Sie unter [Programmierbeispiele für SQL Server-Daten](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="usage"></a>Verwendung  
 In den folgenden Abschnitten werden verschiedene Methoden zur Verwendung der neuen Datums- und Uhrzeittypen beschrieben.  
  
### <a name="use-date-as-a-distinct-data-type"></a>Verwenden von 'Date' als eindeutigen Datentyp  
 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]Ab macht die erweiterte Unterstützung für Datums-/Uhrzeittypen die Verwendung des DBTYPE_DBDATE-OLE DB Typs effizienter.  
  
### <a name="use-time-as-a-distinct-data-type"></a>Verwenden von 'Time' als eindeutigen Datentyp  
 OLE DB verfügt bereits über einen Datentyp, der nur die Zeit enthält: DBTYPE_DBTIME, der die Zeit mit einer Genauigkeit von 1 Sekunde angibt.
  
 Der neue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Zeitdatentyp verfügt über eine Genauigkeit in Sekundenbruchteilen von bis zu 100 Nanosekunden. Dies erfordert einen neuen Typ in OLE DB Treiber für SQL Server: DBTYPE_DBTIME2. Vorhandene Anwendungen, in denen Zeitdaten nicht in Sekundenbruchteilen angegeben werden, können time(0)-Spalten verwenden. Der vorhandene OLE DB DBTYPE_TIME-Typ und seine entsprechenden Strukturen sollten richtig funktionieren, sofern sich die Anwendungen nicht auf den in den Metadaten zurückgegebenen Typ verlassen.  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>Verwenden von 'Time' als eindeutigen Datentyp mit einer Genauigkeit in Sekundenbruchteilen  
 Einige Anwendungen, z. B. in der Fertigung und Prozesssteuerung, erfordern die Fähigkeit, Zeitdaten mit einer Genauigkeit von bis zu 100 Nanosekunden zu verarbeiten. Zu diesem Zweck wird in OLE DB ein neuer Typ ist DBTYPE_DBTIME2.  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>Verwenden von 'Datetime' mit einer Genauigkeit in Sekundenbruchteilen  
 OLE DB definiert bereits einen Typ mit einer Genauigkeit von bis zu 1 Nanosekunde. Dieser Typ wird jedoch bereits von vorhandenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anwendungen verwendet. Diese Anwendungen erwarten eine Genauigkeit von nur 1/300 Sekunde. Der neue **datetime2(3)** -Typ ist nicht direkt kompatibel mit dem vorhandenen datetime-Typ. Wenn das Risiko besteht, dass sich dies auf das Verhalten der Anwendung auswirkt, müssen Anwendungen das neue DBCOLUMN-Flag zur Bestimmung des tatsächlichen Servertyps verwenden.    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>Verwenden von 'Datetime' mit einer Genauigkeit in Sekundenbruchteilen und Zeitzoneninformationen  
 Einige Anwendungen erfordern datetime-Werte mit Zeitzoneninformationen. Dies wird vom neuen DBTYPE_DBTIMESTAMPOFFSET-Typ unterstützt.
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>Verwenden von 'Date'-/'Time'-/'Datetime'-/'Datetimeoffset'-Daten mit clientseitigen Konvertierungen in Übereinstimmung mit vorhandenen Konvertierungen  
 Die Konvertierungen wurden auf einheitliche Weise erweitert, um alle in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] eingeführte Konvertierungen zwischen Datums- und Zeittypen einzuschließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
