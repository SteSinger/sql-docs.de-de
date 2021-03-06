---
title: Informationen zu Treibern und Datenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e9b7229882b3b7f94e6b059e04c6496bde09641
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938044"
---
# <a name="about-drivers-and-data-sources"></a>Informationen zu Treibern und Datenquellen
*Treiber* sind die Komponenten, die ODBC-Anforderungen verarbeitet und Daten an die Anwendung zurück. Ggf. Ändern der Treiber die Anforderung einer Anwendung in ein Format, das von der Datenquelle erkannt wird. Sie müssen den Treiber des Setup-Programm verwenden, zum Hinzufügen oder Löschen einen Treiber auf Ihrem Computer.  
  
 *Datenquellen* sind die Datenbanken oder Dateien, die von einem Treiber zugegriffen und durch einen Datenquellennamen (DSN) identifiziert. Verwenden Sie den ODBC-Datenquellen-Administrator hinzufügen, konfigurieren und Löschen von Datenquellen aus dem System. Die Typen von Datenquellen, die verwendet werden können, werden in der folgenden Tabelle beschrieben.  
  
|Datenquelle|Beschreibung|  
|-----------------|-----------------|  
|Benutzer|Benutzer-DSNs werden lokal auf einem Computer und können nur durch den aktuellen Benutzer verwendet werden. Sie werden in der Teilstruktur der HKEY_CURRENT_USER-Registrierung registriert.|  
|System|System-DSNs werden lokal auf einem Computer statt für einen Benutzer bestimmt. Das System oder alle Benutzer mit Berechtigungen können eine Datenquelle mit einer System-DSN einrichten. System-DSNs werden in der HKEY_LOCAL_MACHINE-Registrierungsunterstruktur registriert.|  
|Datei|Datei-DSNs werden dateibasierte Datenquellen, die freigegeben werden können, von allen Benutzern, die die gleichen Treiber installiert haben und daher Zugriff auf die Datenbank. Diese Datenquellen müssen nicht ausschließlich für einen Benutzer noch lokal auf einem Computer sein. Datei-Datenquellennamen werden nicht durch dedizierte Registrierungseinträge bezeichnet. Stattdessen werden sie durch einen Dateinamen mit der Erweiterung ".DSN" identifiziert.|  
  
 Benutzer und System-Datenquellen werden zusammen als bezeichnet *Computer* -Datenquellen, da sie sich lokal auf einem Computer befinden.  
  
 Jede dieser Datenquellen verfügt über eine Registerkarte der **ODBC-Datenquellenadministrator** Dialogfeld. Weitere Informationen zu Datenquellen finden Sie unter [Datenquellen](../../odbc/reference/data-sources.md).
