---
title: Verwenden des Hilfsprogramms sqlcmd
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- Transact-SQL statements, executing
- command prompt utilities [SQL Server], sqlcmd
- statements [SQL Server], executing
- sqlcmd utility, about sqlcmd utility
ms.assetid: 3ec89119-7314-43ef-9e91-12e72bb63d62
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb14d7809eba496ede8c8e0aa6e7133c2ad9c524
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75243183"
---
# <a name="use-the-sqlcmd-utility"></a>Verwenden des Hilfsprogramms sqlcmd
  Das Hilfsprogramm `sqlcmd` ist ein Befehlszeilen-Hilfsprogramm für die interaktive Ad-hoc-Ausführung von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen und -Skripts und die Automatisierung von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skripttasks. Damit Sie `sqlcmd` interaktiv verwenden oder Skriptdateien aufbauen können, die mithilfe von `sqlcmd` ausgeführt werden, müssen Sie mit den Grundlagen von [!INCLUDE[tsql](../../includes/tsql-md.md)] vertraut sein. Das Hilfsprogramm `sqlcmd` wird in der Regel wie folgt verwendet:  
  
-   Der Benutzer gibt [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen ähnlich wie bei der Arbeit an der Eingabeaufforderung interaktiv ein. Die Ergebnisse werden an der Eingabeaufforderung angezeigt. Klicken Sie auf **Start**, **Alle Programme**, zeigen Sie auf **Zubehör**, und klicken Sie dann auf **Eingabeaufforderung**, um das Eingabeaufforderungsfenster zu öffnen. Geben Sie an der Eingabeaufforderung `sqlcmd` ein, gefolgt von einer Liste der gewünschten Optionen. Eine umfassende Liste der Optionen, die von `sqlcmd`unterstützt werden, finden Sie unter [sqlcmd Utility](../../tools/sqlcmd-utility.md).  
  
-   Der Benutzer sendet einen `sqlcmd`-Auftrag entweder durch Angeben einer einzelnen auszuführenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung oder durch Verweisen auf eine Textdatei, in der die auszuführenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen enthalten sind. Die Ausgabe wird normalerweise in einer Textdatei gespeichert, sie kann jedoch auch an der Eingabeaufforderung angezeigt werden.  
  
-   [Sqlcmd](edit-sqlcmd-scripts-with-query-editor.md) -Modus [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] im Abfrage-Editor.  
  
-   SQL Server Management Objects (SMO)  
  
-   CmdExec-Aufträge des SQL Server-Agents.  
  
## <a name="typically-used-sqlcmd-options"></a>Normalerweise verwendete Optionen für sqlcmd  
 Die folgenden Optionen werden am häufigsten verwendet:  
  
-   Die Server Option (**-S**), mit der die Instanz [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von identifiziert `sqlcmd` wird, mit der eine Verbindung hergestellt wird.  
  
-   Authentifizierungs Optionen (**-E**, **-U**und **-P**), mit denen die Anmelde Informationen `sqlcmd` angegeben werden, die von verwendet werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], um eine Verbindung mit der Instanz von herzustellen.  
  
    > [!NOTE]  
    >  Die Option **-E** ist die Standardeinstellung und muss nicht angegeben werden.  
  
-   Eingabeoptionen (**-q**, **-q**und **-i**), mit denen der Speicherort der Eingabe für `sqlcmd`identifiziert wird.  
  
-   Die Ausgabe Option (**-o**), mit der die Datei angegeben `sqlcmd` wird, in der die Ausgabe abgelegt werden soll.  
  
## <a name="connecting-to-the-sqlcmd-utility"></a>Herstellen einer Verbindung mit dem Hilfsprogramm "sqlcmd"  
 Das Hilfsprogramm `sqlcmd` wird häufig für folgende Aufgaben verwendet:  
  
-   Herstellen einer Verbindung mit einer Standardinstanz mithilfe der Windows-Authentifizierung, um [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen interaktiv auszuführen:  
  
    ```  
    sqlcmd -S <ComputerName>  
    ```  
  
    > [!NOTE]  
    >  Im vorherigen Beispiel wurde **-E** nicht angegeben, da es sich hierbei um den Standard `sqlcmd` Wert handelt und mithilfe der Windows-Authentifizierung eine Verbindung mit der Standard Instanz hergestellt wird.  
  
-   Herstellen einer Verbindung mit einer benannten Instanz mithilfe der Windows-Authentifizierung, um [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen interaktiv auszuführen:  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName>  
    ```  
  
     oder  
  
    ```  
    sqlcmd -S .\<InstanceName>  
    ```  
  
-   Herstellen einer Verbindung mit einer benannten Instanz mithilfe der Windows-Authentifizierung und Angeben von Eingabe- und Ausgabedateien:  
  
    ```  
    sqlcmd -S <ComputerName>\<InstanceName> -i <MyScript.sql> -o <MyOutput.rpt>  
    ```  
  
-   Herstellen einer Verbindung mit der Standardinstanz auf dem lokalen Computer mithilfe der Windows-Authentifizierung, wobei eine Abfrage ausgeführt wird und `sqlcmd` nach Abschluss der Abfrage weiterhin ausgeführt wird:  
  
    ```  
    sqlcmd -q "SELECT * FROM AdventureWorks2012.Person.Person"  
    ```  
  
-   Herstellen einer Verbindung mit der Standardinstanz auf dem lokalen Computer mithilfe der Windows-Authentifizierung, wobei eine Abfrage ausgeführt, die Ausgabe an eine Datei weitergeleitet und `sqlcmd` nach Abschluss der Abfrage beendet wird:  
  
    ```  
    sqlcmd -Q "SELECT * FROM AdventureWorks2012.Person.Person" -o MyOutput.txt  
    ```  
  
-   Herstellen einer Verbindung mit einer benannten Instanz mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung, um [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen interaktiv auszuführen, wobei von `sqlcmd` eine Aufforderung zur Kennworteingabe erfolgt:  
  
    ```  
    sqlcmd -U MyLogin -S <ComputerName>\<InstanceName>  
    ```  
  
    > [!NOTE]  
    >  Eine vollständige Liste der von `sqlcmd` unterstützten Optionen erhalten Sie, indem Sie folgenden Befehl ausführen: `sqlcmd -?`.  
  
## <a name="running-transact-sql-statements-interactively-by-using-sqlcmd"></a>Interaktives Ausführen von Transact-SQL-Anweisungen mithilfe von "sqlcmd"  
 Sie können das Hilfsprogramm `sqlcmd` interaktiv verwenden, um [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen in einem Eingabeaufforderungsfenster auszuführen. Um-Anweisungen [!INCLUDE[tsql](../../includes/tsql-md.md)] interaktiv mithilfe `sqlcmd`von auszuführen, führen Sie das Hilfsprogramm ohne die Optionen **-q**, **-q**, **-Z**, oder **-i** aus, um Eingabedateien oder Abfragen anzugeben. Beispiel:  
  
 `sqlcmd -S <ComputerName>\<InstanceName>`  
  
 Wenn der Befehl ohne Eingabedateien oder Abfragen ausgeführt wird, wird von `sqlcmd` eine Verbindung mit der angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt und anschließend eine neue Zeile mit einer `1>` gefolgt von einem blinkenden Unterstrich angezeigt. Dies wird als `sqlcmd`-Aufforderung bezeichnet. 
  `1` bedeutet, dass es sich um die erste Zeile einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung handelt, und die `sqlcmd`-Aufforderung ist die Stelle, an der die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung beginnt, wenn Sie sie eingeben.  
  
 An der `sqlcmd` Eingabeaufforderung können Sie sowohl [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen als auch `sqlcmd`-Befehle (z. B. `GO` und `EXIT`) eingeben. Die einzelnen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen werden in einen Puffer geladen, den sogenannten Anweisungscache. Diese Anweisungen werden an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gesendet, nachdem Sie den Befehl `GO` eingegeben haben und die EINGABETASTE drücken. Um den `sqlcmd`Vorgang zu `EXIT` beenden `QUIT` , geben Sie oder am Anfang einer neuen Zeile ein.  
  
 Den Anweisungscache können Sie löschen, indem Sie `:RESET` eingeben. Die `^C` Eingabe `sqlcmd` bewirkt, dass beendet wird. 
  `^C` kann auch dazu verwendet werden, die Ausführung des Anweisungscaches zu beenden, nachdem ein `GO`-Befehl ausgegeben wurde.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]Anweisungen, die in einer interaktiven Sitzung eingegeben werden, können bearbeitet werden, indem der Befehl " `sqlcmd` **: Ed** " und die Eingabeaufforderung eingegeben werden. Der Editor wird geöffnet. Nachdem Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung bearbeitet und den Editor geschlossen haben, wird die überarbeitete [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung im Eingabeaufforderungsfenster angezeigt. Geben `GO` Sie ein, um die [!INCLUDE[tsql](../../includes/tsql-md.md)] resultierende Anweisung auszuführen.  
  
## <a name="quoted-strings"></a>Zeichenfolgen in Anführungszeichen  
 Zeichen, die in Anführungszeichen eingeschlossen sind, werden ohne weitere Vorverarbeitung verwendet. Die einzige Ausnahme besteht darin, dass Anführungszeichen durch das Eingeben von zwei aufeinander folgenden Anführungszeichen in eine Zeichenfolge eingefügt werden können. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In wird diese Zeichenfolgensequenz als ein Anführungszeichen behandelt. (Die Übersetzung erfolgt jedoch auf dem Server.) Skriptvariablen werden nicht erweitert, wenn sie innerhalb einer Zeichenfolge auftreten.  
  
 Beispiel:  
  
 `sqlcmd`  
  
 `PRINT "Length: 5"" 7'";`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Length: 5" 7'`  
  
## <a name="strings-that-span-multiple-lines"></a>Mehrere Zeilen umfassende Zeichenfolgen  
 Bei `sqlcmd` werden Skripts mit Zeichenfolgen, die mehrere Zeilen umfassen, unterstützt. Beispielsweise umfasst die folgende `SELECT` -Anweisung mehrere Zeilen; es handelt sich jedoch um eine einzelne Zeichenfolge, die ausgeführt wird, wenn Sie `GO`eingeben und anschließend die EINGABETASTE drücken.  
  
 `SELECT First line`  
  
 `FROM Second line`  
  
 `WHERE Third line;`  
  
 `GO`  
  
## <a name="interactive-sqlcmd-example"></a>Beispiel für die interaktive Verwendung von "sqlcmd"  
 In diesem Beispiel wird veranschaulicht, was bei der interaktiven Ausführung von `sqlcmd` angezeigt wird.  
  
 Wenn Sie ein Eingabeaufforderungsfenster öffnen, wird nur eine Zeile ähnlich der Folgenden angezeigt:  
  
 `C:\> _`  
  
 Dies bedeutet, dass der Ordner `C:\` der aktuelle Ordner ist. Wenn Sie einen Dateinamen angeben, wird in Windows in diesem Ordner nach der Datei gesucht.  
  
 Geben Sie `sqlcmd` ein, um eine Verbindung mit der Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem lokalen Computer herzustellen. In diesem Fall lautet der Inhalt des Eingabeaufforderungsfensters folgendermaßen:  
  
 `C:\>sqlcmd`  
  
 `1> _`  
  
 Dies bedeutet, dass Sie eine Verbindung mit dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt haben und von `sqlcmd` ab sofort [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen und `sqlcmd` -Befehle akzeptiert werden. Der blinkende Unterstrich hinter der `1>` ist die `sqlcmd` -Aufforderung. Damit wird die Stelle gekennzeichnet, an der die von Ihnen eingegebenen Anweisungen und Befehle angezeigt werden. Geben Sie nun `USE AdventureWorks2012` ein, und drücken Sie die Eingabe `GO` Taste, und geben Sie ein. Im Eingabeaufforderungsfensters wird der folgende Text angezeigt:  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `1> _`  
  
 Durch das Drücken der EINGABETASTE nach dem Eingeben von `USE AdventureWorks2012` wurde `sqlcmd` angewiesen, eine neue Zeile zu beginnen. Durch das Drücken der EINGABETASTE nach dem Eingeben von `GO,` wurde `sqlcmd` angewiesen, die `USE AdventureWorks2012` -Anweisung an die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu senden. 
  `sqlcmd` Anschließend wurde von sqlcmd die Meldung zurückgegeben, dass die `USE` -Anweisung erfolgreich ausgeführt wurde, und es wurde eine neue `1>` -Eingabeaufforderung als Hinweis zum Eingeben einer neuen Anweisung oder eines neuen Befehls angezeigt.  
  
 Im folgenden Beispiel wird gezeigt, was im Eingabeaufforderungsfenster angezeigt wird, wenn Sie eine `SELECT` -Anweisung, eine `GO` -Anweisung zum Ausführen von `SELECT`und anschließend `EXIT` eingeben, um `sqlcmd`zu beenden:  
  
 `sqlcmd`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `BusinessEntityID   FirstName                 LastName`  
  
 `----------- -------------------------------- -----------`  
  
 `1           Syed                             Abbas`  
  
 `2           Catherine                        Abel`  
  
 `3           Kim                              Abercrombie`  
  
 `(3 rows affected)`  
  
 `1> EXIT`  
  
 `C:\>`  
  
 Bei den Zeilen im Anschluss an die Zeile `3> GO` handelt es sich um die Ausgabe einer `SELECT` -Anweisung. Nach dem Generieren einer Ausgabe wird die `sqlcmd` -Eingabeaufforderung durch `sqlcmd` zurückgesetzt, und es wird `1>`angezeigt. Nach der Eingabe von `EXIT` in der Zeile `1>`wird im Eingabeaufforderungsfenster dieselbe Zeile wie beim ersten Öffnen der Eingabeaufforderung angezeigt. Dies bedeutet, dass die Sitzung von `sqlcmd` beendet ist. Sie können das Eingabeaufforderungsfenster nun schließen, indem Sie einen weiteren `EXIT` -Befehl eingeben.  
  
## <a name="running-transact-sql-script-files-by-using-sqlcmd"></a>Ausführen von Transact-SQL-Skriptdateien mithilfe von "sqlcmd"  
 Sie können `sqlcmd` zum Ausführen von Datenbankskriptdateien verwenden. Skriptdateien sind Textdateien, die eine Mischung aus [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisungen, `sqlcmd` Befehlen und Skript Variablen enthalten. Weitere Informationen zum Definieren von Skriptvariablen finden Sie unter [Verwenden von sqlcmd mit Skriptvariablen](sqlcmd-use-with-scripting-variables.md). In `sqlcmd` werden Anweisungen, Befehle und Skriptvariablen in einer Skriptdatei verwendet, ähnlich wie bei der Verwendung interaktiv eingegebener Anweisungen und Befehle. Der Hauptunterschied besteht darin, dass die Eingabedatei von `sqlcmd` ohne Pause durchgelesen wird, anstatt darauf zu warten, dass ein Benutzer die Anweisungen, Befehle und Skriptvariablen eingibt.  
  
 Es gibt verschiedene Möglichkeiten, um Datenbankskriptdateien zu erstellen:  
  
-   Sie können eine Reihe von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen interaktiv in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erstellen und debuggen und anschließend den Inhalt des Abfragefensters als Skriptdatei speichern.  
  
-   Sie können eine Textdatei mit [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen mithilfe eines Text-Editors (z. B. Editor) erstellen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-running-a-script-by-using-sqlcmd"></a>A. Ausführen eines Skripts mithilfe von "sqlcmd"  
 Starten Sie Editor, und geben Sie die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen ein:  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 `SELECT TOP (3) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 Erstellen Sie einen neuen Ordner mit dem Namen `MyFolder` , und speichern Sie das Skript als Datei `MyScript.sql` im Ordner `C:\MyFolder`. Geben Sie die folgende Eingabeaufforderung ein, um das Skript auszuführen, und speichern Sie die Ausgabe in `MyOutput.txt` im Ordner `MyFolder`:  
  
 `sqlcmd -i C:\MyFolder\MyScript.sql -o C:\MyFolder\MyOutput.txt`  
  
 Wenn Sie den Inhalt von `MyOutput.txt` in Editor anzeigen, sehen Sie Folgendes:  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `BusinessEntityID FirstName   LastName`  
  
 `---------------- ----------- -----------`  
  
 `1                Syed        Abbas`  
  
 `2                Catherine   Abel`  
  
 `3                Kim         Abercrombie`  
  
 `(3 rows affected)`  
  
### <a name="b-using-sqlcmd-with-a-dedicated-administrative-connection"></a>B: Verwenden von "sqlcmd" mit einer dedizierten Verwaltungsverbindung  
 Im folgenden Beispiel wird mithilfe von `sqlcmd` eine Verbindung mit einem Server hergestellt, der Blockierungsprobleme aufweist. Dies erfolgt mithilfe einer dedizierten Administratorverbindung (Dedicated Administrator Connection, DAC).  
  
 `C:\>sqlcmd -S ServerName -A`  
  
 `1> SELECT blocked FROM sys.dm_exec_requests WHERE blocked <> 0;`  
  
 `2> GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `spid   blocked`  
  
 `------ -------`  
  
 `62       64`  
  
 `(1 rows affected)`  
  
 Beenden Sie den Blockierungsprozess mithilfe von `sqlcmd` .  
  
 `1> KILL 64;`  
  
 `2> GO`  
  
### <a name="c-using-sqlcmd-to-execute-a-stored-procedure"></a>c. Verwenden von "sqlcmd" zum Ausführen einer gespeicherten Prozedur  
 Im folgenden Beispiel wird veranschaulicht, wie eine gespeicherte Prozedur mithilfe von `sqlcmd`ausgeführt wird. Erstellen Sie die folgende gespeicherte Prozedur.  
  
 `USE AdventureWorks2012;`  
  
 `IF OBJECT_ID ( ' dbo.ContactEmailAddress, 'P' ) IS NOT NULL`  
  
 `DROP PROCEDURE dbo.ContactEmailAddress;`  
  
 `GO`  
  
 `CREATE PROCEDURE dbo.ContactEmailAddress`  
  
 `(`  
  
 `@FirstName nvarchar(50)`  
  
 `,@LastName nvarchar(50)`  
  
 `)`  
  
 `AS`  
  
 `SET NOCOUNT ON`  
  
 `SELECT EmailAddress`  
  
 `FROM Person.Person`  
  
 `WHERE FirstName = @FirstName`  
  
 `AND LastName = @LastName;`  
  
 `SET NOCOUNT OFF`  
  
 Geben Sie an der `sqlcmd` -Eingabeaufforderung Folgendes ein:  
  
 `C:\sqlcmd`  
  
 `1> :Setvar FirstName Gustavo`  
  
 `1> :Setvar LastName Achong`  
  
 `1> EXEC dbo.ContactEmailAddress $(Gustavo),$(Achong)`  
  
 `2> GO`  
  
 `EmailAddress`  
  
 `-----------------------------`  
  
 `gustavo0@adventure-works.com`  
  
### <a name="d-using-sqlcmd-for-database-maintenance"></a>D. Verwenden von "sqlcmd" für die Datenbankwartung  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe von `sqlcmd` Datenbankwartungstasks ausgeführt werden können. Erstellen Sie `C:\BackupTemplate.sql` mit dem folgenden Code.  
  
 `USE master;`  
  
 `BACKUP DATABASE [$(db)] TO DISK='$(bakfile)';`  
  
 Geben Sie an der `sqlcmd` -Eingabeaufforderung Folgendes ein:  
  
 `C:\ >sqlcmd`  
  
 `1> :connect <server>`  
  
 `Sqlcmd: Successfully connected to server <server>.`  
  
 `1> :setvar db msdb`  
  
 `1> :setvar bakfile c:\msdb.bak`  
  
 `1> :r c:\BackupTemplate.sql`  
  
 `2> GO`  
  
 `Changed database context to 'master'.`  
  
 `Processed 688 pages for database 'msdb', file 'MSDBData' on file 2.`  
  
 `Processed 5 pages for database 'msdb', file 'MSDBLog' on file 2.`  
  
 `BACKUP DATABASE successfully processed 693 pages in 0.725 seconds (7.830 MB/sec)`  
  
### <a name="e-using-sqlcmd-to-execute-code-on-multiple-instances"></a>E. Verwenden von "sqlcmd" zum Ausführen von Code auf mehreren Instanzen  
 Mit dem folgenden Code wird in einer Datei ein Skript angezeigt, mit dem eine Verbindung mit zwei Instanzen hergestellt wird. Beachten Sie die `GO` -Anweisung vom dem Herstellen einer Verbindung mit der zweiten Instanz.  
  
 `:CONNECT <server>\,<instance1>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
 `:CONNECT <server>\,<instance2>`  
  
 `EXEC dbo.SomeProcedure`  
  
 `GO`  
  
### <a name="e-returning-xml-output"></a>E. Zurückgeben einer XML-Ausgabe  
 Im folgenden Beispiel wird gezeigt, wie eine XML-Ausgabe unformatiert in einem fortlaufenden Datenstrom zurückgegeben wird.  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> :XML ON`  
  
 `1> SELECT TOP 3 FirstName + ' ' + LastName + ', '`  
  
 `2> FROM Person.Person`  
  
 `3> GO`  
  
 `Syed Abbas, Catherine Abel, Kim Abercrombie,`  
  
### <a name="f-using-sqlcmd-in-a-windows-script-file"></a>F. Verwenden von "sqlcmd" in einer Windows-Skriptdatei  
 Ein `sqlcmd`Befehl wie `sqlcmd -i C:\InputFile.txt -o C:\OutputFile.txt,` kann in einer bat-Datei in Verbindung mit VBScript ausgeführt werden. In diesem Fall werden keine interaktiven Optionen verwendet. 
  `sqlcmd` muss auf dem Computer installiert sein, auf dem die BAT-Datei ausgeführt wird.  
  
 Erstellen Sie zunächst die folgenden vier Dateien:  
  
-   C:\badscript.sql  
  
    ```  
    SELECT batch_1_this_is_an_error  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   C:\goodscript.sql  
  
    ```  
    SELECT 'batch #1'  
    GO  
    SELECT 'batch #2'  
    GO  
    ```  
  
-   C:\returnvalue.sql  
  
    ```  
    :exit(select 100)  
    @echo off  
    C:\windowsscript.bat  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
-   C:\windowsscript.bat  
  
    ```  
    @echo off  
  
    echo Running badscript.sql  
    sqlcmd -i badscript.sql -b -o out.log  
    if not errorlevel 1 goto next1  
    echo == An error occurred   
  
    :next1  
  
    echo Running goodscript.sql  
    sqlcmd -i goodscript.sql -b -o out.log  
    if not errorlevel 1 goto next2  
    echo == An error occurred   
  
    :next2  
    echo Running returnvalue.sql  
    sqlcmd -i returnvalue.sql -o out.log  
    echo SQLCMD returned %errorlevel% to the command shell  
  
    :exit  
    ```  
  
 Führen Sie anschließend an der Eingabeaufforderung `C:\windowsscript.bat`aus:  
  
 `C:\>windowsscript.bat`  
  
 `Running badscript.sql`  
  
 `== An error occurred`  
  
 `Running goodscript.sql`  
  
 `Running returnvalue.sql`  
  
 `SQLCMD returned 100 to the command shell`  
  
### <a name="g-using-sqlcmd-to-set-encryption-on-azure-sql-database"></a>G. Verwenden von „sqlcmd“ zum Festlegen der Verschlüsselung für eine Azure SQL-Datenbank  
 Eine `sqlcmd`kann für eine Verbindung mit [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Daten ausgeführt werden, um die Verschlüsselung und Zertifikats Vertrauensstellung anzugeben. Zwei ' sqlcmd ' ' '-Optionen sind verfügbar:  
  
-   Der Schalter "-N" wird vom Client verwendet, um eine verschlüsselte Verbindung anzufordern. Diese Option entspricht der ADO.NET-Option `ENCRYPT = true`.  
  
-   Der Switch „–C“ wird vom Client verwendet, um ihn so zu konfigurieren, dass dem Serverzertifikat implizit vertraut wird, ohne es zu überprüfen. Diese Option entspricht der ADO.NET-Option `TRUSTSERVERCERTIFICATE = true`.  
  
 Der [!INCLUDE[ssSDS](../../includes/sssds-md.md)] -Dienst unterstützt nicht alle `SET` -Optionen, die für eine SQL Server-Instanz verfügbar sind. Die folgenden Optionen lösen einen Fehler aus, wenn die entsprechende `SET` -Option auf `ON` oder `OFF`festgelegt wird:  
  
-   SET ANSI_DEFAULTS  
  
-   SET ANSI_NULLS  
  
-   SET REMOTE_PROC_TRANSACTIONS  
  
-   SET ANSI_NULL_DEFAULT  
  
 Die folgenden SET-Optionen lösen zwar keine Ausnahmen aus, können jedoch nicht verwendet werden. Sie sind veraltet:  
  
-   SET CONCAT_NULL_YIELDS_NULL  
  
-   SET ANSI_PADDING  
  
-   SET QUERY_GOVERNOR_COST_LIMIT  
  
#### <a name="syntax"></a>Syntax  
 Die folgenden Beispiele beziehen sich auf Fälle,in denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anbieter-Einstellungen Folgendes umfasst: `ForceProtocolEncryption = False`, `Trust Server Certificate = No`  
  
 Verbindung mit Windows-Anmeldeinformationen herstellen und Kommunikation verschlüsseln:  
  
```  
SQLCMD -E -N  
  
```  
  
 Verbindung mit Windows-Anmeldeinformationen herstellen und Serverzertifikat vertrauen:  
  
```  
SQLCMD -E -C  
  
```  
  
 Verbindung mit Windows-Anmeldeinformationen herstellen, Kommunikation verschlüsseln und Serverzertifikat vertrauen:  
  
```  
SQLCMD -E -N -C  
  
```  
  
 Die folgenden Beispiele beziehen sich auf zwei Fälle, in denen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anbieter-Einstellungen wie folgt lauten: `ForceProtocolEncryption = True`, `TrustServerCertificate = Yes`.  
  
 Verbindung mit Windows-Anmeldeinformationen herstellen, Kommunikation verschlüsseln und Serverzertifikat vertrauen:  
  
```  
SQLCMD -E  
  
```  
  
 Verbindung mit Windows-Anmeldeinformationen herstellen, Kommunikation verschlüsseln und Serverzertifikat vertrauen:  
  
```  
SQLCMD -E -N  
  
```  
  
 Verbindung mit Windows-Anmeldeinformationen herstellen, Kommunikation verschlüsseln und Serverzertifikat vertrauen:  
  
```  
SQLCMD -E -T  
  
```  
  
 Verbindung mit Windows-Anmeldeinformationen herstellen, Kommunikation verschlüsseln und Serverzertifikat vertrauen:  
  
```  
SQLCMD -E -N -C  
  
```  
  
 Wenn der Anbieter `ForceProtocolEncryption = True` angibt, wird die Verschlüsselung aktiviert, auch wenn die Verbindungszeichenfolge `Encrypt=No` enthält.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sqlcmd-Hilfsprogramm](../../tools/sqlcmd-utility.md)   
 [Verwenden von sqlcmd mit Skript Variablen](sqlcmd-use-with-scripting-variables.md)   
 [Bearbeiten von sqlcmd-Skripts mit dem Abfrage-Editor](edit-sqlcmd-scripts-with-query-editor.md)   
 [Verwalten von Auftrags Schritten](../../ssms/agent/manage-job-steps.md)   
 [Erstellen eines CmdExec-Auftrags Schritts](../../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
