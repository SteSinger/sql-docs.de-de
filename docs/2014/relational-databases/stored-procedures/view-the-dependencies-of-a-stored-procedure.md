---
title: Anzeigen der Abhängigkeiten einer gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], dependencies
- displaying stored procedure dependencies
- viewing stored procedure dependencies
ms.assetid: 6ae0a369-1bc7-4ae4-be89-2b483697cd1f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 14f380f510070da1b8fa77f7f5440640ce37452b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62856503"
---
# <a name="view-the-dependencies-of-a-stored-procedure"></a>Anzeigen der Abhängigkeiten einer gespeicherten Prozedur
    
##  <a name="Top"></a> In diesem Thema wird beschrieben, wie zum Anzeigen der Abhängigkeiten von gespeicherten Prozeduren in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Vorbereitungen:**  [Sicherheit](#Security)  
  
-   **Anzeigen die Abhängigkeiten einer Prozedur mit:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Systemfunktion: `sys.dm_sql_referencing_entities`  
 Erfordert die CONTROL-Berechtigung für die Entität, auf die verwiesen wird, und die SELECT-Berechtigung für sys.dm_sql_referencing_entities. Wenn es sich bei der Entität, auf die verwiesen wird, um eine Partitionsfunktion handelt, ist die CONTROL-Berechtigung für die Datenbank erforderlich. Standardmäßig wird die SELECT-Berechtigung der public-Rolle erteilt.  
  
 Systemfunktion: `sys.dm_sql_referenced_entities`  
 Erfordert die SELECT-Berechtigung für sys.dm_sql_referenced_entities und die VIEW DEFINITION-Berechtigung für die verweisende Entität. Standardmäßig wird die SELECT-Berechtigung der public-Rolle erteilt. Erfordert die Berechtigung VIEW DEFINITION oder ALTER DATABASE DDL TRIGGER für die Datenbank, wenn es sich bei der verweisenden Entität um einen DDL-Trigger auf Datenbankebene handelt. Erfordert die VIEW ANY DEFINITION-Berechtigung für den Server, wenn es sich bei der verweisenden Entität um einen DDL-Trigger auf Serverebene handelt.  
  
 Objektkatalogsicht: `sys.sql_expression_dependencies`  
 Erfordert die VIEW DEFINITION-Berechtigung für die Datenbank und die SELECT-Berechtigung für sys.sql_expression_dependencies für die Datenbank. Standardmäßig wird die SELECT-Berechtigung nur Mitgliedern der festen Datenbankrolle db_owner gewährt. Wenn einem anderen Benutzer die SELECT-Berechtigung und die VIEW DEFINITION-Berechtigung erteilt werden, kann dieser Berechtigte alle Abhängigkeiten in der Datenbank anzeigen.  
  
##  <a name="Procedures"></a> So zeigen Sie die Abhängigkeiten einer gespeicherten Prozedur an  
 Sie können eine der folgenden Anwendungen verwenden:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
 **So zeigen Sie die Abhängigkeiten von einer Prozedur im Objekt-Explorer an**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, erweitern Sie die Datenbank, zu der die Prozedur gehört, und erweitern Sie dann **Programmierbarkeit**.  
  
3.  Erweitern Sie **Gespeicherte Prozeduren**, klicken Sie mit der rechten Maustaste auf die Prozedur, und klicken Sie dann auf **Abhängigkeiten anzeigen**.  
  
4.  Zeigen Sie die Liste der Objekte an, die von der Prozedur abhängig sind.  
  
5.  Zeigen Sie die Liste der Objekte an, von denen die Prozedur abhängig ist.  
  
6.  Klicken Sie auf **OK**.  
  
###  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So zeigen Sie die Abhängigkeiten einer Prozedur im Abfrage-Editor an**  
  
 Systemfunktion: `sys.dm_sql_referencing_entities`  
 Diese Funktion dient zum Anzeigen der Objekte, die von einer Prozedur abhängen.  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, der die Prozedur angehört.  
  
3.  Klicken Sie im Menü **Datei** auf **Neue Abfrage** .  
  
4.  Kopieren Sie die folgenden Beispiele, und fügen Sie sie in den Abfrage-Editor ein. Im ersten Beispiel wird die `uspVendorAllInfo` -Prozedur erstellt. Diese Prozedur gibt die Namen, die gelieferten Produkte, die Bonität und die Verfügbarkeit aller Hersteller in der [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] -Datenbank, die das Unternehmen beliefern, zurück.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  Nachdem die Prozedur erstellt wurde, wird im zweiten Beispiel die sys.dm_sql_referencing_entities-Funktion verwendet, um die Objekte anzuzeigen, die von der Prozedur abhängen.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referencing_schema_name, referencing_entity_name, referencing_id, referencing_class_desc, is_caller_dependent  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');   
    GO  
  
    ```  
  
 Systemfunktion: `sys.dm_sql_referenced_entities`  
 Diese Funktion dient zum Anzeigen der Objekte, von denen eine Prozedur abhängt.  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, der die Prozedur angehört.  
  
3.  Klicken Sie im Menü **Datei** auf **Neue Abfrage** .  
  
4.  Kopieren Sie die folgenden Beispiele, und fügen Sie sie in den Abfrage-Editor ein. Im ersten Beispiel wird die `uspVendorAllInfo` -Prozedur erstellt. Diese Prozedur gibt die Namen, die gelieferten Produkte, die Bonität und die Verfügbarkeit aller Hersteller in der [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] -Datenbank, die das Unternehmen beliefern, zurück.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  Nachdem die Prozedur erstellt wurde, wird im zweiten Beispiel die sys.dm_sql_referenced_entities-Funktion verwendet, um die Objekte anzuzeigen, von denen die Prozedur abhängt.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT referenced_schema_name, referenced_entity_name,  
    referenced_minor_name,referenced_minor_id, referenced_class_desc,  
    is_caller_dependent, is_ambiguous  
    FROM sys.dm_sql_referencing_entities ('Purchasing.uspVendorAllInfo', 'OBJECT');  
    GO  
    ```  
  
 Objektkatalogsicht: `sys.sql_expression_dependencies`  
 Diese Sicht kann verwendet werden, um die Objekte anzuzeigen, von denen eine Prozedur abhängt, bzw. um die von einer Prozedur abhängigen Objekte anzuzeigen.  
  
 Anzeigen der Objekte, die von einer Prozedur abhängen.  
 1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, der die Prozedur angehört.  
  
3.  Klicken Sie im Menü **Datei** auf **Neue Abfrage** .  
  
4.  Kopieren Sie die folgenden Beispiele, und fügen Sie sie in den Abfrage-Editor ein. Im ersten Beispiel wird die `uspVendorAllInfo` -Prozedur erstellt. Diese Prozedur gibt die Namen, die gelieferten Produkte, die Bonität und die Verfügbarkeit aller Hersteller in der [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] -Datenbank, die das Unternehmen beliefern, zurück.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  Nachdem die Prozedur erstellt wurde, wird im zweiten Beispiel die sys.sql_expression_dependencies-Sicht verwendet, um die Objekte anzuzeigen, die von der Prozedur abhängen.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_SCHEMA_NAME ( referencing_id ) AS referencing_schema_name,  
        OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referenced_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
 Anzeigen der Objekte, von denen eine Prozedur abhängt.  
 1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, der die Prozedur angehört.  
  
3.  Klicken Sie im Menü **Datei** auf **Neue Abfrage** .  
  
4.  Kopieren Sie die folgenden Beispiele, und fügen Sie sie in den Abfrage-Editor ein. Im ersten Beispiel wird die `uspVendorAllInfo` -Prozedur erstellt. Diese Prozedur gibt die Namen, die gelieferten Produkte, die Bonität und die Verfügbarkeit aller Hersteller in der [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] -Datenbank, die das Unternehmen beliefern, zurück.  
  
     [!code-sql[ProcedureDDL#CreateProc8](../../snippets/tsql/SQL14/tsql/procedureddl/transact-sql/createproc.sql#createproc8)]  
  
5.  Nachdem die Prozedur erstellt wurde, wird im zweiten Beispiel die sys.sql_expression_dependencies-Sicht verwendet, um die Objekte anzuzeigen, von denen die Prozedur abhängt.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_NAME(referencing_id) AS referencing_entity_name,   
        o.type_desc AS referencing_desciption,   
        COALESCE(COL_NAME(referencing_id, referencing_minor_id), '(n/a)') AS referencing_minor_id,   
        referencing_class_desc, referenced_class_desc,  
        referenced_server_name, referenced_database_name, referenced_schema_name,  
        referenced_entity_name,   
        COALESCE(COL_NAME(referenced_id, referenced_minor_id), '(n/a)') AS referenced_column_name,  
        is_caller_dependent, is_ambiguous  
    FROM sys.sql_expression_dependencies AS sed  
    INNER JOIN sys.objects AS o ON sed.referencing_id = o.object_id  
    WHERE referencing_id = OBJECT_ID(N'Purchasing.uspVendorAllInfo')  
    GO  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Umbenennen einer gespeicherten Prozedur](rename-a-stored-procedure.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
  
