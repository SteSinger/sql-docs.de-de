---
title: sys. dm_exec_requests (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/01/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: sstein
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_requests_TSQL
- sys.dm_exec_requests
- dm_exec_requests_TSQL
- dm_exec_requests
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_requests dynamic management view
ms.assetid: 4161dc57-f3e7-4492-8972-8cfb77b29643
author: pmasl
ms.author: pelopes
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 20257eb1a91b35dd45e1b4fc79f84533c64b2561
ms.sourcegitcommit: aaa42f26c68abc2de10eb58444fe6b490c174eab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74307997"
---
# <a name="sysdm_exec_requests-transact-sql"></a>sys.dm_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt Informationen zu jeder Anforderung zurück, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird. Weitere Informationen zu Anforderungen finden Sie im [Handbuch zur Thread-und Task Architektur](../../relational-databases/thread-and-task-architecture-guide.md).
   
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|ID der Sitzung, auf die sich diese Anforderung bezieht. Lässt keine NULL-Werte zu.|  
|request_id|**wartenden**|ID der Anforderung. Ist im Kontext der Sitzung eindeutig. Lässt keine NULL-Werte zu.|  
|start_time|**DateTime**|Der Zeitstempel, der angibt, wann die Anforderung eingetroffen ist. Lässt keine NULL-Werte zu.|  
|status|**nvarchar (30)**|Status der Anforderung. Mögliche Werte:<br /><br /> Hintergrund<br />Aktiv<br />Ausführbar<br />Ruhezustand<br />Suspended<br /><br /> Lässt keine NULL-Werte zu.|  
|command|**nvarchar (32)**|Identifiziert den aktuellen Typ des Befehls, der gerade verarbeitet wird. Als allgemeine Befehlstypen sind die folgenden möglich:<br /><br /> SELECT<br />INSERT<br />UPDATE<br />DELETE<br />BACKUP LOG<br />BACKUP DATABASE<br />DBCC<br />FOR<br /><br /> Der Text der Anforderung kann mithilfe von sys.dm_exec_sql_text und dem entsprechenden sql_handle-Wert für die Anforderung abgerufen werden. Interne Systemprozesse legen den Befehl je nach Typ des ausgeführten Tasks fest. Mögliche Tasks sind z. B. die folgenden:<br /><br /> LOCK MONITOR<br />CHECKPOINTLAZY<br />WRITER<br /><br /> Lässt keine NULL-Werte zu.|  
|sql_handle|**varbinary (64)**|Ein Token, das den Batch oder die gespeicherte Prozedur eindeutig identifiziert, zu der die Abfrage gehört. Lässt NULL-Werte zu.|  
|statement_start_offset|**wartenden**|Anzahl von Zeichen im derzeit ausgeführten Batch oder in der derzeit ausgeführten gespeicherten Prozedur, an der die derzeit ausgeführte Anweisung beginnt. Kann zusammen mit sql_handle, statement_end_offset und der dynamischen Verwaltungsfunktion sys.dm_exec_sql_text zum Abrufen der zurzeit ausgeführten Anweisung für die Anforderung verwendet werden. Lässt NULL-Werte zu.|  
|statement_end_offset|**wartenden**|Anzahl von Zeichen im derzeit ausgeführten Batch oder in der derzeit ausgeführten gespeicherten Prozedur, an der die derzeit ausgeführte Anweisung endet. Kann zusammen mit sql_handle, statement_end_offset und der dynamischen Verwaltungsfunktion sys.dm_exec_sql_text zum Abrufen der zurzeit ausgeführten Anweisung für die Anforderung verwendet werden. Lässt NULL-Werte zu.|  
|plan_handle|**varbinary (64)**|Ein Token, das einen Abfrage Ausführungsplan für einen momentan ausgeführten Batch eindeutig identifiziert. Lässt NULL-Werte zu.|  
|database_id|**smallint**|ID der Datenbank, für die die Anforderung ausgeführt wird. Lässt keine NULL-Werte zu.|  
|user_id|**wartenden**|ID des Benutzers, der die Anforderung gesendet hat. Lässt keine NULL-Werte zu.|  
|connection_id|**uniqueidentifier**|ID der Verbindung, über die die Anforderung eingetroffen ist. Lässt NULL-Werte zu.|  
|blocking_session_id|**smallint**|ID der Sitzung, die die Anforderung blockiert. Wenn diese Spalte NULL oder gleich 0 (null) ist, wird die Anforderung nicht blockiert, oder die Sitzungsinformationen der blockierenden Sitzung sind nicht verfügbar (oder können nicht identifiziert werden).<br /><br /> -2 = Der Besitzer der blockierenden Ressource ist eine verwaiste verteilte Transaktion.<br /><br /> -3 = Der Besitzer der blockierenden Ressource ist eine verzögerte Wiederherstellungstransaktion.<br /><br /> -4 = Die Sitzungs-ID des Besitzers des blockierenden Latches konnte zu diesem Zeitpunkt aufgrund von internen Latchstatusübergängen nicht bestimmt werden.|  
|wait_type|**nvarchar (60)**|Wenn die Anforderung zurzeit blockiert wird, gibt diese Spalte den Wartetyp zurück. Lässt NULL-Werte zu.<br /><br /> Weitere Informationen zu warte Typen finden Sie unter [sys. dm_os_wait_stats &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|  
|wait_time|**wartenden**|Wenn die Anforderung zurzeit blockiert wird, gibt diese Spalte die Dauer des aktuellen Wartevorgangs in Millisekunden an. Lässt keine NULL-Werte zu.|  
|last_wait_type|**nvarchar (60)**|Wenn diese Anforderung zuvor bereits blockiert war, gibt diese Spalte den Typ des letzten Wartevorgangs zurück. Lässt keine NULL-Werte zu.|  
|wait_resource|**nvarchar(256)**|Wenn die Anforderung zurzeit blockiert wird, gibt diese Spalte die Ressource zurück, auf die die Anforderung zurzeit wartet. Lässt keine NULL-Werte zu.|  
|open_transaction_count|**wartenden**|Anzahl der für die Anforderung offenen Transaktionen. Lässt keine NULL-Werte zu.|  
|open_resultset_count|**wartenden**|Anzahl der für die Anforderung offenen Resultsets. Lässt keine NULL-Werte zu.|  
|transaction_id|**bigint**|ID der Transaktion, in der diese Anforderung ausgeführt wird. Lässt keine NULL-Werte zu.|  
|context_info|**varbinary (128)**|CONTEXT_INFO-Wert der Sitzung. Lässt NULL-Werte zu.|  
|percent_complete|**wirkliche**|Prozentsatz der für die folgenden Befehle durchgeführten Arbeit:<br /><br /> ALTER INDEX REORGANIZE<br />AUTO_SHRINK-Option mit ALTER DATABASE<br />BACKUP DATABASE<br />DBCC CHECKDB<br />DBCC CHECKFILEGROUP<br />DBCC CHECKTABLE<br />DBCC INDEXDEFRAG<br />DBCC SHRINKDATABASE<br />DBCC SHRINKFILE<br />RECOVERY<br />RESTORE DATABASE<br />ROLLBACK<br />TDE ENCRYPTION<br /><br /> Lässt keine NULL-Werte zu.|  
|estimated_completion_time|**bigint**|Nur intern. Lässt keine NULL-Werte zu.|  
|cpu_time|**wartenden**|Von der Anforderung beanspruchte CPU-Zeit (in Millisekunden). Lässt keine NULL-Werte zu.|  
|total_elapsed_time|**wartenden**|Gesamtzeit seit dem Eintreffen der Anforderung (in Millisekunden). Lässt keine NULL-Werte zu.|  
|scheduler_id|**wartenden**|ID des Zeitplanungsmoduls, das diese Anforderung plant. Lässt keine NULL-Werte zu.|  
|task_address|**varbinary(8)**|Speicheradresse, die dem Task für diese Anforderung zugeordnet ist. Lässt NULL-Werte zu.|  
|reads|**bigint**|Anzahl der von dieser Anforderung ausgeführten Lesevorgänge. Lässt keine NULL-Werte zu.|  
|writes|**bigint**|Anzahl der von dieser Anforderung ausgeführten Schreibvorgänge. Lässt keine NULL-Werte zu.|  
|logical_reads|**bigint**|Anzahl der von dieser Anforderung ausgeführten logischen Lesevorgänge. Lässt keine NULL-Werte zu.|  
|text_size|**wartenden**|TEXTSIZE-Einstellung für diese Anforderung. Lässt keine NULL-Werte zu.|  
|language|**nvarchar(128)**|Spracheinstellung für die Anforderung. Lässt NULL-Werte zu.|  
|date_format|**nvarchar (3)**|DATEFORMAT-Einstellung für die Anforderung. Lässt NULL-Werte zu.|  
|date_first|**smallint**|DATEFIRST-Einstellung für die Anforderung. Lässt keine NULL-Werte zu.|  
|quoted_identifier|**trate**|1 = QUOTED_IDENTIFIER ist ON für die Anforderung. Andernfalls ist der Wert 0.<br /><br /> Lässt keine NULL-Werte zu.|  
|arithabort|**bit**|1 = ARITHABORT ist für die Anforderung auf ON festgelegt. Andernfalls ist der Wert 0.<br /><br /> Lässt keine NULL-Werte zu.|  
|ansi_null_dflt_on|**trate**|1 = ANSI_NULL_DFLT_ON ist für die Anforderung auf ON festgelegt. Andernfalls ist der Wert 0.<br /><br /> Lässt keine NULL-Werte zu.|  
|ansi_defaults|**bit**|1 = ANSI_DEFAULTS ist für die Anforderung auf ON festgelegt. Andernfalls ist der Wert 0.<br /><br /> Lässt keine NULL-Werte zu.|  
|ansi_warnings|**bit**|1 = ANSI_WARNINGS ist für die Anforderung auf ON festgelegt. Andernfalls ist der Wert 0.<br /><br /> Lässt keine NULL-Werte zu.|  
|ansi_padding|**bit**|1 = ANSI_PADDING ist für die Anforderung auf ON festgelegt.<br /><br /> Andernfalls ist der Wert 0.<br /><br /> Lässt keine NULL-Werte zu.|  
|ansi_nulls|**bit**|1 = ANSI_NULLS ist für die Anforderung auf ON festgelegt. Andernfalls ist der Wert 0.<br /><br /> Lässt keine NULL-Werte zu.|  
|concat_null_yields_null|**trate**|1 = CONCAT_NULL_YIELDS_NULL ist für die Anforderung auf ON festgelegt. Andernfalls ist der Wert 0.<br /><br /> Lässt keine NULL-Werte zu.|  
|transaction_isolation_level|**smallint**|Isolationsstufe, mit der die Transaktion für diese Anforderung erstellt wird. Lässt keine NULL-Werte zu.<br /> 0 = Unspecified<br /> 1 = ReadUncomitted<br /> 2 = ReadCommitted<br /> 3 = Repeatable<br /> 4 = Serializable<br /> 5 = Momentaufnahme|  
|lock_timeout|**wartenden**|Sperrtimeout für diese Anforderung (in Millisekunden). Lässt keine NULL-Werte zu.|  
|deadlock_priority|**wartenden**|DEADLOCK_PRIORITY-Einstellung für die Anforderung. Lässt keine NULL-Werte zu.|  
|row_count|**bigint**|Anzahl von Zeilen, die von dieser Anforderung an den Client zurückgegeben wurden. Lässt keine NULL-Werte zu.|  
|prev_error|**wartenden**|Letzter Fehler, der während der Ausführung der Anforderung aufgetreten ist. Lässt keine NULL-Werte zu.|  
|nest_level|**wartenden**|Aktuelle Schachtelungsebene von Code, der für die Anforderung ausgeführt wird. Lässt keine NULL-Werte zu.|  
|granted_query_memory|**wartenden**|Anzahl von Seiten, die der Ausführung einer Abfrage in der Anforderung zugeordnet sind. Lässt keine NULL-Werte zu.|  
|executing_managed_code|**trate**|Gibt an, ob eine bestimmte Anforderung zurzeit CLR-Objekte (Common Language Runtime) ausführt, z. B. Routinen, Typen und Trigger. Die Festlegung gilt für die gesamte Zeit, die sich ein CLR-Objekt im Stapel befindet, selbst wenn [!INCLUDE[tsql](../../includes/tsql-md.md)] aus CLR heraus ausgeführt wird. Lässt keine NULL-Werte zu.|  
|group_id|**wartenden**|ID der Arbeitsauslastungsgruppe, zu der diese Abfrage gehört. Lässt keine NULL-Werte zu.|  
|query_hash|**Binär (8)**|Binärer Hashwert, der in der Abfrage berechnet wird und zum Identifizieren von Abfragen mit ähnlicher Logik verwendet wird. Sie können den Abfragehash verwenden, um die aggregierte Ressourcennutzung für Abfragen zu ermitteln, die sich nur durch Literalwerte unterscheiden.|  
|query_plan_hash|**Binär (8)**|Binärer Hashwert, der im Abfrageausführungsplan wird und zum Identifizieren ähnlicher Abfrageausführungspläne verwendet wird. Sie können diesen Abfrageplan-Hashwert verwenden, um die kumulierten Kosten für Abfragen mit ähnlichen Ausführungsplänen zu suchen.|  
|statement_sql_handle|**varbinary (64)**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> SQL-Handle der einzelnen Abfrage.<br /><br />Diese Spalte ist NULL, wenn Abfragespeicher nicht für die Datenbank aktiviert ist. |  
|statement_context_id|**bigint**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> Der optionale Fremdschlüssel für sys. query_context_settings.<br /><br />Diese Spalte ist NULL, wenn Abfragespeicher nicht für die Datenbank aktiviert ist. |  
|dop |**wartenden** |**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.<br /><br /> Der Grad der Parallelität der Abfrage. |  
|parallel_worker_count |**wartenden** |**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.<br /><br /> Die Anzahl der reservierten parallelen worker, wenn dies eine parallele Abfrage ist.  |  
|external_script_request_id |**uniqueidentifier** |**Gilt für**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] und höher.<br /><br /> Die externe Skript Anforderungs-ID, die der aktuellen Anforderung zugeordnet ist. |  
|is_resumable |**bit** |**Gilt für**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] und höher.<br /><br /> Gibt an, ob die Anforderung ein fort Setz barer Index Vorgang ist. |  
|page_resource |**Binär (8)** |**Gilt für**:[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]<br /><br /> Eine 8-Byte-hexadezimale Darstellung der Seiten Ressource, `wait_resource` wenn die Spalte eine Seite enthält. Weitere Informationen finden Sie unter [sys. fn_PageResCracker](../../relational-databases/system-functions/sys-fn-pagerescracker-transact-sql.md). |  
|page_server_reads|**bigint**|**Gilt für**: hyperskalierung von Azure SQL-Datenbank<br /><br /> Anzahl von Seiten Server Lesevorgängen, die von dieser Anforderung ausgeführt werden. Lässt keine NULL-Werte zu.|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>Hinweise 
Für die Ausführung von Code außerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (z. B. erweiterte gespeicherte Prozeduren und verteilte Abfragen) muss ein Thread außerhalb der Steuerung des nicht präemptiven Zeitplanungsmoduls ausgeführt werden. Dazu wechselt ein Arbeitsthread in den präemptiven Modus. Zeitwerte, die von dieser dynamischen Verwaltungssicht zurückgegeben werden, schließen nicht die im präemptiven Modus verbrachte Zeit ein.

Beim Ausführen paralleler Anforderungen im [Zeilen Modus](../../relational-databases/query-processing-architecture-guide.md#row-mode-execution)weist einen Arbeits Thread zu, um die Arbeitsthreads zu koordinieren, die für das Abschließen der zugewiesenen Aufgaben zuständig sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In dieser DMV ist nur der koordinatorthread für die Anforderung sichtbar. Die Spalten **Lese**-, **Schreib**-, **logical_reads**-und **row_count** werden für den koordinatorthread **nicht aktualisiert** . Die Spalten **wait_type**, **wait_time**, **last_wait_type**, **wait_resource**und **granted_query_memory** werden nur für den koordinatorthread **aktualisiert** . Weitere Informationen finden Sie im [Handbuch zur Thread- und Taskarchitektur](../../relational-databases/thread-and-task-architecture-guide.md).

## <a name="permissions"></a>Berechtigungen
Wenn der Benutzer über `VIEW SERVER STATE` die-Berechtigung auf dem Server verfügt, werden dem Benutzer alle ausgeführten Sitzungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]der Instanz von angezeigt. Andernfalls wird dem Benutzer nur die aktuelle Sitzung angezeigt. `VIEW SERVER STATE`kann in Azure SQL-Datenbank nicht erteilt `sys.dm_exec_requests` werden, sodass immer auf die aktuelle Verbindung beschränkt ist.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-finding-the-query-text-for-a-running-batch"></a>A. Suchen des Abfragetexts für einen ausgeführten Batch

 Im folgenden Beispiel werden `sys.dm_exec_requests` abgefragt, um die entsprechende Abfrage zu suchen und den `sql_handle`-Wert aus der Ausgabe zu kopieren.  

```sql
SELECT * FROM sys.dm_exec_requests;  
GO  
```  

Verwenden Sie dann zum Abrufen des Anweisungstexts den kopierten `sql_handle`-Wert mit der Systemfunktion `sys.dm_exec_sql_text(sql_handle)`.  

```sql
SELECT * FROM sys.dm_exec_sql_text(< copied sql_handle >);  
GO  
```

### <a name="b-finding-all-locks-that-a-running-batch-is-holding"></a>B: Suchen aller Sperren, die ein ausgeführter Batch enthält

Im folgenden Beispiel wird **sys. dm_exec_requests** abgefragt, um den interessanten Batch zu `transaction_id` suchen und dessen aus der Ausgabe zu kopieren.

```sql
SELECT * FROM sys.dm_exec_requests;  
GO
```

Verwenden Sie anschließend zum Suchen von Sperrinformationen das mit `transaction_id` der Systemfunktion **sys. dm_tran_locks**kopierte.  

```sql
SELECT * FROM sys.dm_tran_locks
WHERE request_owner_type = N'TRANSACTION'
    AND request_owner_id = < copied transaction_id >;
GO  
```

### <a name="c-finding-all-currently-blocked-requests"></a>c. Suchen aller zurzeit blockierten Anforderungen

Im folgenden Beispiel wird **sys. dm_exec_requests** abgefragt, um Informationen zu blockierten Anforderungen zu finden.  

```sql
SELECT session_id ,status ,blocking_session_id  
    ,wait_type ,wait_time ,wait_resource
    ,transaction_id
FROM sys.dm_exec_requests
WHERE status = N'suspended';  
GO  
```  

### <a name="d-ordering-existing-requests-by-cpu"></a>D. Anordnen vorhandener Anforderungen nach CPU

```sql
SELECT 
   req.session_id
   , req.start_time
   , cpu_time 'cpu_time_ms'
   , object_name(st.objectid,st.dbid) 'ObjectName' 
   , substring
      (REPLACE
        (REPLACE
          (SUBSTRING
            (ST.text
            , (req.statement_start_offset/2) + 1
            , (
               (CASE statement_end_offset
                  WHEN -1
                  THEN DATALENGTH(ST.text)  
                  ELSE req.statement_end_offset
                  END
                    - req.statement_start_offset)/2) + 1)
       , CHAR(10), ' '), CHAR(13), ' '), 1, 512)  AS statement_text  
FROM sys.dm_exec_requests AS req  
   CROSS APPLY sys.dm_exec_sql_text(req.sql_handle) as ST
   ORDER BY cpu_time desc;
GO
```

## <a name="see-also"></a>Weitere Informationen
[Dynamische Verwaltungs Sichten und-Funktionen](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)     
[Dynamische Verwaltungs Sichten und-Funktionen im Zusammenhang mit der Ausführung](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)      
[sys. dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)     
[sys. dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)     
[sys. dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)    
[sys. dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys. dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)      
[SQL Server, SQL-Statistik-Objekt](../../relational-databases/performance-monitor/sql-server-sql-statistics-object.md)     
[Leitfaden zur Architektur der Abfrage Verarbeitung](../../relational-databases/query-processing-architecture-guide.md#DOP)       
[Handbuch zur Thread-und Task Architektur](../../relational-databases/thread-and-task-architecture-guide.md)    
