---
title: Zugreifen auf speicheroptimierte Tabellen mit interpretiertem Transact-SQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 92a44d4d-0e53-4fb0-b890-de264c65c95a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c81ac6c0c8dcf7e24c80b426654164c668fcf3a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62468607"
---
# <a name="accessing-memory-optimized-tables-using-interpreted-transact-sql"></a>Zugreifen auf speicheroptimierte Tabellen mit interpretiertem Transact-SQL
  Mit nur wenigen Ausnahmen, erreichen Sie Speicheroptimierte Tabellen mit einer [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage- oder DML-Vorgang (SELECT, INSERT, UPDATE oder DELETE), ad-hoc-Batches und SQL-Module wie gespeicherte Prozeduren, Tabellenwertfunktionen, Trigger und Sichten.  
  
 Interpretiertes [!INCLUDE[tsql](../../includes/tsql-md.md)] bezieht sich auf [!INCLUDE[tsql](../../includes/tsql-md.md)] -Batches oder gespeicherte Prozeduren, die keine systemintern kompilierten gespeicherten Prozeduren sind. Der Zugriff auf speicheroptimierte Tabellen mittels interpretiertem [!INCLUDE[tsql](../../includes/tsql-md.md)] wird als Interopzugriff bezeichnet.  
  
 Auf speicheroptimierte Tabellen kann auch mithilfe einer systemintern kompilierten gespeicherten Prozedur zugegriffen werden. Für leistungskritische OLTP-Vorgänge werden systemintern kompilierte gespeicherte Prozeduren empfohlen.  
  
 Interpretierter [!INCLUDE[tsql](../../includes/tsql-md.md)] -Zugriff wird für die folgenden Szenarien empfohlen:  
  
-   Ad-hoc-Abfragen und Verwaltungsaufgaben  
  
-   Berichtsabfragen, die in der Regel Konstrukte verwenden, die in systemintern kompilierten gespeicherten Prozeduren nicht verfügbar sind (z. B. Fensterfunktionen).  
  
-   Zum Migrieren leistungskritischer Teile der Anwendung zu speicheroptimierten Tabellen mit minimalen (oder ohne) Änderungen am Anwendungscode. Durch das Migrieren von Tabellen können u. U. Leistungsverbesserungen erzielt werden. Durch die anschließende Migration gespeicherter Prozeduren zu systemintern kompilierten gespeicherten Prozeduren lässt sich die Leistung möglicherweise weiter optimieren.  
  
-   Wenn keine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung für systemintern kompilierte gespeicherte Prozeduren verfügbar ist.  
  
 Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Konstrukte werden in gespeicherten Prozeduren mit interpretiertem [!INCLUDE[tsql](../../includes/tsql-md.md)], die auf Daten in einer speicheroptimierten Tabelle zugreifen, nicht unterstützt.  
  
|Bereich|Nicht unterstützt|  
|----------|-----------------|  
|Zugriff auf Tabellen|TRUNCATE TABLE<br /><br /> MERGE (speicheroptimierte Tabelle als Ziel)<br /><br /> Dynamische und KEYSET-Cursor (diese werden automatisch auf "statisch" herabgestuft).<br /><br /> Zugriff aus CLR-Modulen mithilfe der Kontextverbindung.<br /><br /> Das Verweisen auf eine speicheroptimierte Tabelle aus einer indizierten Sicht.|  
|Datenbankübergreifend|Datenbankübergreifende Abfragen<br /><br /> Datenbankübergreifende Transaktionen<br /><br /> Verbindungsserver|  
  
## <a name="table-hints"></a>Tabellenhinweise  
 Weitere Informationen zu Tabellenhinweisen finden Sie unter [Tabellenhinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table). Zur Unterstützung von [!INCLUDE[hek_2](../../includes/hek-2-md.md)] wurde die SNAPSHOT-Isolation hinzugefügt.  
  
 Die folgenden Tabellenhinweise werden nicht unterstützt, wenn mit interpretiertem [!INCLUDE[tsql](../../includes/tsql-md.md)]auf eine speicheroptimierte Tabelle zugegriffen wird.  
  
|||||  
|-|-|-|-|  
|HOLDLOCK|IGNORE_CONSTRAINTS|IGNORE_TRIGGERS|NOWAIT|  
|PAGLOCK|READCOMMITTED|READCOMMITTEDLOCK|READPAST|  
|READUNCOMMITTED|ROWLOCK|SPATIAL_WINDOW_MAX_CELLS = *integer*|TABLOCK|  
|TABLOCKXX|UPDLOCK|XLOCK||  
  
 Wenn von einer expliziten oder impliziten Transaktion mittels interpretiertem [!INCLUDE[tsql](../../includes/tsql-md.md)] auf eine speicheroptimierte Tabelle zugegriffen wird, müssen Sie einen Tabellenhinweis auf die Isolationsstufe wie etwa SNAPSHOT, REPEATABLEREAD oder SERIALIZABLE einbinden. Alternativ können Sie MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT verwenden. Weitere Informationen finden Sie unter [Richtlinien für Transaktionsisolationsstufen mit speicheroptimierten Tabellen](memory-optimized-tables.md) und [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
> [!NOTE]  
>  Ein Tabellenhinweis auf die Isolationsstufe ist bei speicheroptimierten Tabellen, auf die der Zugriff mit Abfragen im Autocommit-Modus erfolgt, nicht erforderlich.  
  
## <a name="see-also"></a>Siehe auch  
 [Transact-SQL-Unterstützung für In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md)   
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
