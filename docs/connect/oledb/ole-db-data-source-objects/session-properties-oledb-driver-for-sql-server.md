---
title: 'Sitzungseigenschaften: OLE DB-Treiber für SQL Server | Microsoft-Dokumentation'
description: 'Sitzungseigenschaften: OLE DB-Treiber für SQL Server'
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- OLE DB Driver for SQL Server, sessions
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7bc2ae9c6908bfcd0bf28b4f05be757d22c55f75
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015909"
---
# <a name="session-properties---ole-db-driver-for-sql-server"></a>Sitzungseigenschaften: OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB Treiber für SQL Server interpretiert OLE DB Sitzungs Eigenschaften wie folgt.  
  
|Eigenschafts-ID|und Beschreibung|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Der OLE DB-Treiber für SQL Server unterstützt alle Isolationsstufen von Transaktionen im Autocommit-Modus mit Ausnahme der Chaosstufe DBPROPVAL_TI_CHAOS.|  
  
 Im anbieterspezifischen Eigenschaftensatz DBPROPSET_SQLSERVERSESSION definiert der OLE DB-Treiber für SQL Server die folgende zusätzliche Sitzungseigenschaft.  
  
|Eigenschafts-ID|und Beschreibung|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Typ: VT_BOOL<br /><br /> R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: In CATALOG-Einschränkung zugelassene Bezeichner in Anführungszeichen.<br /><br /> VARIANT_TRUE: Bezeichner in Anführungszeichen werden für eine CATALOG-Einschränkung für die Schemarowsets erkannt, die Unterstützung für verteilte Abfragen bieten.<br /><br /> VARIANT_FALSE: Bezeichner in Anführungszeichen werden nicht für eine CATALOG-Einschränkung für die Schemarowsets erkannt, die Unterstützung für verteilte Abfragen bieten.<br /><br /> Weitere Informationen zu Schemarowsets, die Unterstützung für verteilte Abfragen bieten, finden Sie unter [Unterstützung von verteilten Abfragen in Schemarowsets](../../oledb/ole-db/schema-rowsets-distributed-query-support.md).|  
|SSPROP_ALLOWNATIVEVARIANT|Typ: VT_BOOL<br /><br /> R/W: Lesen/Schreiben<br /><br /> Standard: VARIANT_FALSE<br /><br /> Beschreibung: Bestimmt, ob die Daten als DBTYPE_VARIANT oder DBTYPE_SQLVARIANT abgerufen werden.<br /><br /> VARIANT_TRUE: Der Spaltentyp wird als DBTYPE_SQLVARIANT zurückgegeben. In diesem Fall enthält der Puffer die SSVARIANT-Struktur.<br /><br /> VARIANT_FALSE: Der Spaltentyp wird als DBTYPE_VARIANT zurückgegeben und der Puffer enthält die VARIANT-Struktur.|  
|SSPROP_ASYNCH_BULKCOPY|Zur Verwendung des asynchronen Modus legen Sie die anbieterspezifische Sitzungseigenschaft SSPROP_ASYNCH_BULKCOPY vor dem Aufrufen der BCPExec-Methode auf VARIANT_TRUE fest. Diese Eigenschaft ist im DBPROPSET_SQLSERVERSESSION-Eigenschaftensatz verfügbar.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB für Daten &#40;Quellen Objekte&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
