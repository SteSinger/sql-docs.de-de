---
title: sys. sysprocesses (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysprocesses_TSQL
- sys.sysprocesses_TSQL
- sys.sysprocesses
- sysprocesses
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysprocesses compatibility view
- sysprocesses system table
ms.assetid: 60a36d36-54b3-4bd6-9cac-702205a21b16
author: rothja
ms.author: jroth
ms.openlocfilehash: d9da0f09c2506e0d596a485aee112f9f188b6d12
ms.sourcegitcommit: ef830f565ee07dc7d4388925cc3c86c5d2cfb4c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74947152"
---
# <a name="syssysprocesses-transact-sql"></a>sys.sysprocesses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Informationen zu Prozessen, die in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden. Bei diesen Prozessen kann es sich um Clientprozesse oder Systemprozesse handeln. Für den Zugriff auf sysprocesses müssen Sie sich im Kontext der master-Datenbank befinden, oder Sie müssen den dreiteiligen Namen master.dbo.sysprocesses verwenden.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|spid|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sitzungs-ID.|  
|kpid|**smallint**|Windows-Thread-ID.|  
|blocked|**smallint**|ID der Sitzung, die die Anforderung blockiert. Wenn diese Spalte den Wert NULL aufweist, wird die Anforderung nicht blockiert, oder die Sitzungsinformationen der blockierenden Sitzung sind nicht verfügbar (bzw. können nicht identifiziert werden).<br /><br /> -2 = Der Besitzer der blockierenden Ressource ist eine verwaiste verteilte Transaktion.<br /><br /> -3 = Der Besitzer der blockierenden Ressource ist eine verzögerte Wiederherstellungstransaktion.<br /><br /> -4 = Die Sitzungs-ID des Besitzers des blockierenden Latches konnte aufgrund interner Latchstatusübergänge nicht bestimmt werden.|  
|waittype|**Binär (2)**|Reserviert.|  
|waittime|**bigint**|Aktuelle Wartezeit in Millisekunden.<br /><br /> 0 = Prozess wartet nicht.|  
|lastwaittype|**NCHAR (32)**|Eine Zeichenfolge, die den Namen des letzten oder aktuellen Wartetyps anzeigt.|  
|waitresource|**NCHAR (256)**|Textdarstellung einer Sperrressource.|  
|dbid|**smallint**|ID der derzeit vom Prozess verwendeten Datenbank.|  
|uid|**smallint**|Die ID des Benutzers, der den Befehl ausgeführt hat. Führt zu einem Überlauf oder gibt NULL zurück, wenn die Anzahl von Benutzern und Rollen 32.767 übersteigt.|  
|cpu|**wartenden**|Kumulierte CPU-Zeit des Prozesses. Der Eintrag wird unabhängig davon, ob die Option SET STATISTICS TIME auf ON oder OFF festgelegt ist, für alle Prozesse aktualisiert.|  
|physical_io|**bigint**|Kumulative Anzahl von Datenträgerschreib- und -lesezugriffen für den Prozess.|  
|memusage|**wartenden**|Anzahl der Seiten im Prozedur Cache, die diesem Prozess zurzeit zugeordnet sind. Eine negative Anzahl gibt an, dass der Prozess Arbeitsspeicher freigibt, der von einem anderen Prozess zugeordnet wurde.|  
|login_time|**DateTime**|Zeitpunkt, zu dem sich ein Clientprozess am Server angemeldet hat.|  
|last_batch|**DateTime**|Der Zeitpunkt, zu dem ein Clientprozess zuletzt einen RPC-Aufruf oder eine EXECUTE-Anweisung ausgeführt hat.|  
|ecid|**smallint**|Kontext-ID der Ausführung, die zur eindeutigen Bezeichnung der Subthreads verwendet wird, die für einen einzelnen Prozess ausgeführt werden.|  
|open_tran|**smallint**|Anzahl der offenen Transaktionen für den Prozess.|  
|status|**NCHAR (30)**|Der Prozess-ID-Status. Mögliche Werte:<br /><br /> **ruhende**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die Sitzung zurückgesetzt.<br /><br /> wird **ausgeführt** = die Sitzung führt einen oder mehrere Batches aus. Wenn MARS (Multiple Active Result Sets) aktiviert ist, kann eine Sitzung mehrere Batches ausführen. Weitere Informationen finden Sie unter [Verwenden von Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).<br /><br /> **Background** = die Sitzung führt einen Hintergrund Task aus, z. b. die Deadlockerkennung.<br /><br /> **Rollback** = für die Sitzung ist ein Transaktionsrollback in Verarbeitung.<br /><br /> **Pending** = die Sitzung wartet darauf, dass ein Arbeits Thread verfügbar wird.<br /><br /> **ausführbaren** = der Task in der Sitzung befindet sich in der ausführbaren Warteschlange eines Zeit Planungs Moduls, während er darauf wartet, ein Zeit Quantum zu erhalten.<br /><br /> **SPINLOOP** = der Task in der Sitzung wartet darauf, dass ein Spinlock frei wird.<br /><br /> angeh **alten = die** Sitzung wartet auf den Abschluss eines Ereignisses, z. b. der e/a-Vorgänge.|  
|sid|**Binary (86)**|Global eindeutiger Bezeichner (GUID, Globally Unique Identifier) für den Benutzer.|  
|hostname|**NCHAR (128)**|Name der Arbeitsstation.|  
|program_name|**NCHAR (128)**|Name des Anwendungsprogramms.|  
|hostprocess|**NCHAR (10)**|Prozess-ID der Arbeitsstation.|  
|cmd|**NCHAR (26)**|Derzeit ausgeführter Befehl.|  
|nt_domain|**NCHAR (128)**|Windows-Domäne für den Client, wenn die Windows-Authentifizierung oder eine vertrauenswürdige Verbindung verwendet wird.|  
|nt_username|**NCHAR (128)**|Der Windows-Benutzername für den Prozess beim Verwenden der Windows-Authentifizierung, oder eine vertrauenswürdige Verbindung.|  
|net_address|**NCHAR (12)**|Der zugewiesene eindeutige Bezeichner für die Netzwerkkarte auf der Arbeitsstation jedes einzelnen Benutzers. Bei der Anmeldung eines Benutzers wird dieser Bezeichner in die net_address-Spalte eingefügt.|  
|net_library|**NCHAR (12)**|Spalte, in der die Netzwerkbibliothek des Clients gespeichert wird. Jeder Clientprozess wird über eine Netzwerkverbindung übertragen. Netzwerkverbindungen ist eine Netzwerk Bibliothek zugeordnet, mit der Sie die Verbindung herstellen können.|  
|loginame|**NCHAR (128)**|Benutzername|  
|context_info|**Binary (128)**|Daten, die mithilfe der SET CONTEXT_INFO-Anweisung in einem Batch gespeichert werden.|  
|sql_handle|**Binär (20)**|Stellt den zurzeit ausgeführten Batch oder das zurzeit ausgeführte Objekt dar.<br /><br /> **Hinweis** Dieser Wert wird vom Batch oder der Speicheradresse des Objekts abgeleitet. Der Wert wird nicht mit dem hashbasierten Algorithmus von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] berechnet.|  
|stmt_start|**wartenden**|Der Startoffset der aktuellen SQL-Anweisung für den angegebenen sql_handle-Wert.|  
|stmt_end|**wartenden**|Der Endoffset der aktuellen SQL-Anweisung für den angegebenen sql_handle-Wert.<br /><br /> -1 = Die aktuelle Anweisung wird bis zum Ende der Ergebnisse ausgeführt, die von der fn_get_sql-Funktion für den angegebenen sql_handle-Wert zurückgegeben werden.|  
|request_id|**wartenden**|Die ID der Anforderung. Hiermit werden Anforderungen identifiziert, die in einer bestimmten Sitzung ausgeführt werden.|
|page_resource |**Binär (8)** |**Gilt für**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] <br /><br /> Eine 8-Byte-hexadezimale Darstellung der Seiten Ressource, `waitresource` wenn die Spalte eine Seite enthält. |  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Benutzer die VIEW SERVER STATE-Berechtigung auf dem Server besitzt, kann er alle zurzeit ausgeführten Sitzungen in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzeigen; andernfalls wird dem Benutzer nur die aktuelle Sitzung angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dynamische Verwaltungs Sichten und-Funktionen im Zusammenhang mit der Ausführung &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitäts Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
