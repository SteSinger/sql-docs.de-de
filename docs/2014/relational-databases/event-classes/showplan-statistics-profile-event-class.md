---
title: Showplan Statistics Profile-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Showplan Statistics Profile event class
ms.assetid: fa9e1330-a217-491c-ad7c-2c1c4015d1bb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0dc08151d47bee9190f199e187db25a3b5dd6de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62662062"
---
# <a name="showplan-statistics-profile-event-class"></a>Showplan Statistics Profile-Ereignisklasse
  Die Showplan Statistics Profile-Ereignisklasse tritt auf, wenn [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine SQL-Anweisung ausführt. Die enthaltenen Informationen sind eine Teilmenge der in der Showplan XML Statistics Profile-Ereignisklasse verfügbaren Informationen.  
  
 Die Showplan Statistics Profile-Ereignisklasse zeigt vollständige Kompilierzeitdaten an. Für Ablaufverfolgungen mit Showplan Statistics Profile kann es zu einem hohen Leistungsaufwand kommen. Um dieses Problem zu minimieren, beschränken Sie die Verwendung dieser Ereignisklasse auf Ablaufverfolgungen, die bestimmte Probleme nur für einen kurzen Zeitraum überwachen.  
  
 Wenn die Showplan Statistics Profile-Ereignisklasse in einer Ablaufverfolgung enthalten ist, muss die Datenspalte BinaryData ausgewählt sein. Ist dies nicht der Fall, werden Informationen zu dieser Ereignisklasse nicht in der Ablaufverfolgung angezeigt.  
  
## <a name="showplan-statistics-profile-event-class-data-columns"></a>Datenspalten der Showplan Statistics Profile-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|BinaryData|`image`|Die geschätzten Kosten der Abfrage.|2|Nein|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|EventClass|`int`|Ereignistyp = 98.|27|Nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IntegerData|`int`|Geschätzte Anzahl der zurückgegebenen Zeilen.|25|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|LineNumber|`int`|Zeigt die Nummer der Zeile an, die den Fehler enthält|5|Ja|  
|LoginName|`nvarchar`|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSID|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Nein|  
|NestLevel|`int`|Ganze Zahl, die die von @@NESTLEVEL zurückgegebenen Daten darstellt.|29|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|ObjectID|`int`|Vom System zugewiesene ID des Objekts.|22|Ja|  
|ObjectName|`nvarchar`|Name des Objekts, auf das verwiesen wird|34|Ja|  
|ObjectType|`int`|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Dieser Wert entspricht der type-Spalte in sys.objects. Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](objecttype-trace-event-column.md).|28|Ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|XactSequence|`bigint`|Token zur Beschreibung der aktuellen Transaktion.|50|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Referenz zu logischen und physischen Showplanoperatoren](../showplan-logical-and-physical-operators-reference.md)   
 [Showplan XML Statistics Profile-Ereignisklasse](showplan-xml-statistics-profile-event-class.md)  
  
  
