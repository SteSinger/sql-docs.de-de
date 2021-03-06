---
title: ALTER LOGIN (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/06/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER_LOGIN_TSQL
- ALTER LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER LOGIN statement
- change password
- mapping logins [SQL Server]
- logins [SQL Server], modifying
- passwords [SQL Server], modifying
- names [SQL Server], logins
- modifying login accounts
ms.assetid: e247b84e-c99e-4af8-8b50-57586e1cb1c5
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2eeec689116946d99b348cadf0b41bca829848b1
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "73982093"
---
# <a name="alter-login-transact-sql"></a>ALTER LOGIN (Transact-SQL)

Ändert die Eigenschaften eines [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldekontos.

![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="click-a-product"></a>Wählen Sie ein Produkt.

Klicken Sie in der folgenden Zeile auf den Namen des Produkts, das Sie am meisten interessiert. Mit nur einem Klick erhalten Sie auf dieser Webseite unterschiedliche Inhalte, die zu dem Produkt passen, das Sie ausgewählt haben.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

||||||
|-|-|-|-|-|
|**\* _SQL Server \*_** &nbsp;|[SQL-Datenbank<br />Singleton/Pool für elastische Datenbanken](alter-login-transact-sql.md?view=azuresqldb-current)|[SQL-Datenbank<br />verwaltete Instanz](alter-login-transact-sql.md?view=azuresqldb-mi-current)|[SQL Data<br />Warehouse](alter-login-transact-sql.md?view=azure-sqldw-latest)|[Analytics Platform<br />System (PDW)](alter-login-transact-sql.md?view=aps-pdw-2016)
||||||

&nbsp;

## <a name="sql-server"></a>SQL Server

## <a name="syntax"></a>Syntax

```
-- Syntax for SQL Server

ALTER LOGIN login_name
    {
    <status_option>
    | WITH <set_option> [ ,... ]
    | <cryptographic_credential_option>
    }
[;]

<status_option> ::=
        ENABLE | DISABLE

<set_option> ::=
    PASSWORD = 'password' | hashed_password HASHED
    [
      OLD_PASSWORD = 'oldpassword'
      | <password_option> [<password_option> ]
    ]
    | DEFAULT_DATABASE = database
    | DEFAULT_LANGUAGE = language
    | NAME = login_name
    | CHECK_POLICY = { ON | OFF }
    | CHECK_EXPIRATION = { ON | OFF }
    | CREDENTIAL = credential_name
    | NO CREDENTIAL

<password_option> ::=
    MUST_CHANGE | UNLOCK
  
<cryptographic_credentials_option> ::=
    ADD CREDENTIAL credential_name
  | DROP CREDENTIAL credential_name
```

## <a name="arguments"></a>Argumente

*login_name* Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung an, die geändert wird. Domänenanmeldungen müssen in Klammern eingeschlossen werden: [Domäne\Benutzer].

ENABLE | DISABLE Aktiviert oder deaktiviert diese Anmeldung. Das Deaktivieren einer Anmeldung wirkt sich nicht auf das Verhalten der bereits verbundenen Anmeldungen aus. (Verwenden Sie die `KILL`-Anweisung, um eine vorhandene Verbindung zu beenden.) Deaktivierte Anmeldungen behalten ihre Berechtigungen bei und sind weiterhin für den Identitätswechsel verfügbar.

PASSWORD **='** _password_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt das Kennwort für die Anmeldung an, die geändert wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

PASSWORD **=** _hashed\_password_ Gilt nur für das HASHED-Schlüsselwort. Gibt den Hashwert des Kennworts für den Anmeldenamen an, der erstellt wird.

> [!IMPORTANT]
> Wenn für eine Anmeldung (oder den Benutzer einer eigenständigen Datenbank) eine Verbindung hergestellt und diese authentifiziert wird, werden von der Verbindung Identitätsinformationen zur Anmeldung zwischengespeichert. Bei einer Anmeldung unter Verwendung der Windows-Authentifizierung umfassen die Informationen Angaben zur Mitgliedschaft in Windows-Gruppen. Die Identität der Anmeldung bleibt für die Dauer der Verbindung authentifiziert. Um Identitätsänderungen zu erzwingen, z. B. das Zurücksetzen eines Kennworts oder eine Änderung der Windows-Gruppenmitgliedschaft, muss die Anmeldung von der Authentifizierungsstelle (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) abgemeldet und erneut angemeldet werden. Ein Mitglied der festen Serverrolle **sysadmin** oder eine beliebige Anmeldung mit der **ALTER ANY CONNECTION** -Berechtigung kann den **KILL** -Befehl verwenden, um eine Verbindung zu beenden und zu erzwingen, dass für eine Anmeldung eine erneute Verbindung hergestellt wird. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ist in der Lage, Verbindungsinformationen wiederzuverwenden, wenn mehrere Verbindungen mit dem Fenster Objekt-Explorer und Abfrage-Editor hergestellt werden. Schließen Sie alle Verbindungen, um eine erneute Verbindung zu erzwingen.

HASHED Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen. Gibt an, dass das nach dem PASSWORD-Argument eingegebene Kennwort bereits einen Hashwert darstellt. Wenn diese Option nicht ausgewählt wird, wird aus dem Kennwort vor dem Speichern in der Datenbank ein Hashwert erstellt. Diese Option sollte nur für die Anmeldungssynchronisierung zwischen zwei Servern verwendet werden. Verwenden Sie die HASHED-Option nicht, um Kennwörter routinemäßig zu ändern.

OLD_PASSWORD **='** _oldpassword_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Das aktuelle Kennwort der Anmeldung, der ein neues Kennwort zugewiesen wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

MUST_CHANGE Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Falls diese Option angegeben wird, fordert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Eingabe eines aktualisierten Kennworts auf, wenn die geänderte Anmeldung zum ersten Mal verwendet wird.

DEFAULT_DATABASE **=** _database_ Gibt eine Standarddatenbank an, die der Anmeldung zugewiesen werden soll.

DEFAULT_LANGUAGE **=** _language_ Gibt eine Standardsprache an, die der Anmeldung zugewiesen werden soll. Die Standardsprache für alle SQL-Datenbank-Anmeldungen ist Englisch und kann nicht geändert werden. Die Standardsprache der `sa`-Anmeldung bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter Linux ist Englisch. Diese kann jedoch geändert werden.

NAME = *login_name* Der neue Name der Anmeldung, die umbenannt wird. Falls es sich dabei um eine Windows-Anmeldung handelt, muss die SID des entsprechenden Windows-Prinzipals für den neuen Namen mit der SID übereinstimmen, die der Anmeldung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist. Der neue Name einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung darf keinen umgekehrten Schrägstrich (\\) enthalten.

CHECK_EXPIRATION = { ON | **OFF** } Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, ob die Richtlinie für das Ablaufen von Kennwörtern für diesen Anmeldenamen erzwungen werden soll. Der Standardwert ist OFF.

CHECK_POLICY **=** { **ON** | OFF } Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, dass die Windows-Kennwortrichtlinien des Computers, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, für diesen Anmeldenamen erzwungen werden sollen. Der Standardwert ist ON.

CREDENTIAL = *credential_name* Die Anmeldeinformationen, die einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung zugeordnet werden sollen. Die Anmeldeinformationen müssen bereits auf dem Server vorhanden sein. Weitere Informationen finden Sie unter [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md). Der sa-Anmeldung können keine Anmeldeinformationen zugeordnet werden.

NO CREDENTIAL Entfernt vorhandene Zuordnungen der Anmeldung zu Serveranmeldeinformationen. Weitere Informationen finden Sie unter [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md).

UNLOCK Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, dass die Sperre einer Anmeldung aufgehoben wird.

ADD CREDENTIAL Fügt der Anmeldung Anmeldeinformationen eines EKM-Anbieters (Extensible Key Management, erweiterbare Schlüsselverwaltung) hinzu. Weitere Informationen finden Sie unter [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md).

DROP CREDENTIAL Entfernt Anmeldeinformationen eines EKM-Anbieters (Extensible Key Management, erweiterbare Schlüsselverwaltung) aus der Anmeldung. Weitere Informationen finden Sie unter [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)] (../.. /relational-databases/security/encryption/extensible-key-management-ekm.md).

## <a name="remarks"></a>Remarks

Wenn CHECK_POLICY auf ON festgelegt ist, kann das HASHED-Argument nicht verwendet werden.

Wenn CHECK_POLICY in ON geändert wird, passiert Folgendes:

- Der Kennwortverlauf wird mit dem Wert des aktuellen Kennworthashes initialisiert.

  Wenn CHECK_POLICY in OFF geändert wird, passiert Folgendes:

- CHECK_EXPIRATION wird ebenfalls auf OFF festgelegt.
- Der Kennwortverlauf wird gelöscht.
- Der Wert von *lockout_time* wird zurückgesetzt.

Falls MUST_CHANGE angegeben wird, müssen CHECK_EXPIRATION und CHECK_POLICY auf ON festgelegt werden. Andernfalls erzeugt die Anweisung einen Fehler.

Falls CHECK_POLICY auf OFF festgelegt ist, kann CHECK_EXPIRATION nicht auf ON festgelegt werden. Eine ALTER LOGIN-Anweisung mit dieser Kombination von Optionen erzeugt einen Fehler.

Sie können ALTER_LOGIN mit dem DISABLE-Argument nicht dazu verwenden, den Zugriff auf eine Windows-Gruppe zu verweigern. ALTER_LOGIN [*domain\group*] DISABLE gibt zum Beispiel die folgende Fehlermeldung zurück:

    `"Msg 15151, Level 16, State 1, Line 1
    "Cannot alter the login '*Domain\Group*', because it does not exist or you do not have permission."`

    This is by design.
  
In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] werden Anmeldedaten, die für die Authentifizierung einer Verbindung und Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um eine Aktualisierung des Authentifizierungscache zu erzwingen und sicherzustellen, dass eine Datenbank über die aktuelle Version der Tabelle mit Anmeldenamen verfügt.

## <a name="permissions"></a>Berechtigungen

Erfordert die ALTER ANY LOGIN-Berechtigung.

Falls die CREDENTIAL-Option verwendet wird, ist auch die ALTER ANY CREDENTIAL-Berechtigung erforderlich.

Wenn die zu ändernde Anmeldung Mitglied der festen Serverrolle **sysadmin** oder Empfänger der CONTROL SERVER-Berechtigung ist, ist auch die CONTROL SERVER-Berechtigung für die folgenden Änderungen erforderlich:

- Zurücksetzen des Kennworts ohne Eingabe des alten Kennworts.
- Aktivieren von MUST_CHANGE, CHECK_POLICY oder CHECK_EXPIRATION.
- Ändern des Anmeldenamens.
- Aktivieren oder Deaktivieren der Anmeldung.
- Zuordnen der Anmeldung zu anderen Anmeldeinformationen.

Ein Prinzipal kann das Kennwort, die Standardsprache und die Standarddatenbank für seine eigene Anmeldung ändern.

## <a name="examples"></a>Beispiele

### <a name="a-enabling-a-disabled-login"></a>A. Aktivieren einer deaktivierten Anmeldung

Im folgenden Beispiel wird die Anmeldung `Mary5` aktiviert.

```sql
ALTER LOGIN Mary5 ENABLE;
```

### <a name="b-changing-the-password-of-a-login"></a>B. Ändern des Kennworts einer Anmeldung

Im folgenden Beispiel wird das Kennwort der Anmeldung `Mary5` in ein sicheres Kennwort geändert.

```sql
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';
```

### <a name="c-changing-the-password-of-a-login-when-logged-in-as-the-login"></a>C. Ändern des Kennworts einer Anmeldung, wenn Sie mit dieser angemeldet sind

Wenn Sie versuchen, das Kennwort der Anmeldung zu ändern, mit der Sie derzeit angemeldet sind, und wenn Sie nicht die `ALTER ANY LOGIN`-Berechtigung haben, müssen Sie die Option `OLD_PASSWORD` angeben.

```sql
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>' OLD_PASSWORD = '<oldWeakPasswordHere>';
```

### <a name="d-changing-the-name-of-a-login"></a>D. Ändern des Namens einer Anmeldung

Im folgenden Beispiel wird der Name der Anmeldung `Mary5` in `John2` geändert.

```sql
ALTER LOGIN Mary5 WITH NAME = John2;
```

### <a name="e-mapping-a-login-to-a-credential"></a>E. Zuordnen einer Anmeldung zu Anmeldeinformationen

Im folgenden Beispiel wird die Anmeldung `John2` den Anmeldeinformationen `Custodian04` zugeordnet.

```sql
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;
```

### <a name="f-mapping-a-login-to-an-extensible-key-management-credential"></a>F. Zuordnen einer Anmeldung zu Anmeldeinformationen der erweiterbaren Schlüsselverwaltung

Im folgenden Beispiel wird die Anmeldung `Mary5` den EKM-Anmeldeinformationen `EKMProvider1` zugeordnet.

```sql
ALTER LOGIN Mary5
ADD CREDENTIAL EKMProvider1;
GO
```

### <a name="f-unlocking-a-login"></a>F. Entsperren einer Anmeldung

Um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung zu entsperren, führen Sie die folgende Anweisung aus und ersetzen \*\*\*\* durch das gewünschte Kontokennwort.

```sql
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;

GO
```

Um eine Anmeldung zu entsperren, ohne das Kennwort zu ändern, deaktivieren Sie die Überprüfungsrichtlinie, und aktivieren Sie diese dann erneut.

```sql
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;
GO
```

### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. Ändern des Kennworts für eine Anmeldung mit HASHED

Im folgenden Beispiel wird das Kennwort für die `TestUser`-Anmeldung in einen bereits vorhandenen Hashwert geändert.

```sql
ALTER LOGIN TestUser WITH
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;
GO
```

## <a name="see-also"></a>Weitere Informationen

- [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md)
- [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [CREATE CREDENTIAL](../../t-sql/statements/create-credential-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)

::: moniker-end
::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

> ||||||
> |-|-|-|-|-|
> |[SQL Server](alter-login-transact-sql.md?view=sql-server-2017)|**_\* SQL-Datenbank<br />Singleton/Pool für elastische Datenbanken\*_**|[SQL-Datenbank<br />verwaltete Instanz](alter-login-transact-sql.md?view=azuresqldb-mi-current)|[SQL Data<br />Warehouse](alter-login-transact-sql.md?view=azure-sqldw-latest)|[Analytics Platform<br />System (PDW)](alter-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-database-single-databaseelastic-pool"></a>Azure SQL-Datenbank Singleton/Pool für elastische Datenbanken

## <a name="sql-server"></a>SQL Server

## <a name="syntax"></a>Syntax

```
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse

ALTER LOGIN login_name
  {
      <status_option>
    | WITH <set_option> [ ,.. .n ]
  }
[;]

<status_option> ::=
    ENABLE | DISABLE

<set_option> ::=
    PASSWORD ='password'
    [
      OLD_PASSWORD ='oldpassword'
    ]
    | NAME = login_name
```

## <a name="arguments"></a>Argumente

*login_name* Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung an, die geändert wird. Domänenanmeldungen müssen in Klammern eingeschlossen werden: [Domäne\Benutzer].

ENABLE | DISABLE Aktiviert oder deaktiviert diese Anmeldung. Das Deaktivieren einer Anmeldung wirkt sich nicht auf das Verhalten der bereits verbundenen Anmeldungen aus. (Verwenden Sie die `KILL`-Anweisung, um eine vorhandene Verbindung zu beenden.) Deaktivierte Anmeldungen behalten ihre Berechtigungen bei und sind weiterhin für den Identitätswechsel verfügbar.

PASSWORD **='** _password_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt das Kennwort für die Anmeldung an, die geändert wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

Ständig aktive Verbindungen mit SQL-Datenbank erfordern alle 10 Stunden eine erneute Authentifizierung, die von der Datenbank-Engine durchgeführt. Die Datenbank-Engine versucht, eine erneute Authentifizierung mit dem ursprünglich übermittelten Kennwort durchzuführen. Dabei ist keine Eingabe des Benutzers erforderlich. Aus Leistungsgründen wird die Verbindung nicht erneut authentifiziert, wenn ein Kennwort in SQL-Datenbank zurückgesetzt wird. Dies ist auch nicht der Fall, wenn die Verbindung aufgrund von Verbindungspooling zurückgesetzt wird. Dies unterscheidet sich von dem Verhalten von SQL Server (lokal). Wenn das Kennwort nach der ersten Authentifizierung der Verbindung geändert wurde, muss diese Verbindung beendet und eine neue unter Verwendung des neuen Kennworts hergestellt werden. Ein Benutzer mit der KILL DATABASE CONNECTION-Berechtigung kann eine Verbindung mit SQL-Datenbank mit dem Befehl KILL explizit beenden. Weitere Informationen finden Sie unter [KILL](../../t-sql/language-elements/kill-transact-sql.md).

> [!IMPORTANT]
> Wenn für eine Anmeldung (oder den Benutzer einer eigenständigen Datenbank) eine Verbindung hergestellt und diese authentifiziert wird, werden von der Verbindung Identitätsinformationen zur Anmeldung zwischengespeichert. Bei einer Anmeldung unter Verwendung der Windows-Authentifizierung umfassen die Informationen Angaben zur Mitgliedschaft in Windows-Gruppen. Die Identität der Anmeldung bleibt für die Dauer der Verbindung authentifiziert. Um Identitätsänderungen zu erzwingen, z. B. das Zurücksetzen eines Kennworts oder eine Änderung der Windows-Gruppenmitgliedschaft, muss die Anmeldung von der Authentifizierungsstelle (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) abgemeldet und erneut angemeldet werden. Ein Mitglied der festen Serverrolle **sysadmin** oder eine beliebige Anmeldung mit der **ALTER ANY CONNECTION** -Berechtigung kann den **KILL** -Befehl verwenden, um eine Verbindung zu beenden und zu erzwingen, dass für eine Anmeldung eine erneute Verbindung hergestellt wird. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ist in der Lage, Verbindungsinformationen wiederzuverwenden, wenn mehrere Verbindungen mit dem Fenster Objekt-Explorer und Abfrage-Editor hergestellt werden. Schließen Sie alle Verbindungen, um eine erneute Verbindung zu erzwingen.

OLD_PASSWORD **='** _oldpassword_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Das aktuelle Kennwort der Anmeldung, der ein neues Kennwort zugewiesen wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

NAME = *login_name* Der neue Name der Anmeldung, die umbenannt wird. Falls es sich dabei um eine Windows-Anmeldung handelt, muss die SID des entsprechenden Windows-Prinzipals für den neuen Namen mit der SID übereinstimmen, die der Anmeldung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist. Der neue Name einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung darf keinen umgekehrten Schrägstrich (\\) enthalten.

## <a name="remarks"></a>Remarks

In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] werden Anmeldedaten, die für die Authentifizierung einer Verbindung und Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um eine Aktualisierung des Authentifizierungscache zu erzwingen und sicherzustellen, dass eine Datenbank über die aktuelle Version der Tabelle mit Anmeldenamen verfügt.

## <a name="permissions"></a>Berechtigungen

Erfordert die ALTER ANY LOGIN-Berechtigung.

Wenn die zu ändernde Anmeldung Mitglied der festen Serverrolle **sysadmin** oder Empfänger der CONTROL SERVER-Berechtigung ist, ist auch die CONTROL SERVER-Berechtigung für die folgenden Änderungen erforderlich:

- Zurücksetzen des Kennworts ohne Eingabe des alten Kennworts.
- Ändern des Anmeldenamens.
- Aktivieren oder Deaktivieren der Anmeldung.
- Zuordnen der Anmeldung zu anderen Anmeldeinformationen.

Ein Prinzipal kann das Kennwort seiner eigenen Anmeldung ändern.

## <a name="examples"></a>Beispiele

Zu diesen Beispielen gehören auch Beispiele zur Verwendung anderer SQL-Produkte. Oben sehen Sie, welche Argumente unterstützt werden.

### <a name="a-enabling-a-disabled-login"></a>A. Aktivieren einer deaktivierten Anmeldung

Im folgenden Beispiel wird die Anmeldung `Mary5` aktiviert.

```sql
ALTER LOGIN Mary5 ENABLE;
```

### <a name="b-changing-the-password-of-a-login"></a>B. Ändern des Kennworts einer Anmeldung

Im folgenden Beispiel wird das Kennwort der Anmeldung `Mary5` in ein sicheres Kennwort geändert.

```sql
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';
```

### <a name="c-changing-the-name-of-a-login"></a>C. Ändern des Namens einer Anmeldung

Im folgenden Beispiel wird der Name der Anmeldung `Mary5` in `John2` geändert.

```sql
ALTER LOGIN Mary5 WITH NAME = John2;
```

### <a name="d-mapping-a-login-to-a-credential"></a>D. Zuordnen einer Anmeldung zu Anmeldeinformationen

Im folgenden Beispiel wird die Anmeldung `John2` den Anmeldeinformationen `Custodian04` zugeordnet.

```sql
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;
```

### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>E. Zuordnen einer Anmeldung zu Anmeldeinformationen der erweiterbaren Schlüsselverwaltung

Im folgenden Beispiel wird die Anmeldung `Mary5` den EKM-Anmeldeinformationen `EKMProvider1` zugeordnet.


**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.

```sql
ALTER LOGIN Mary5
ADD CREDENTIAL EKMProvider1;
GO
```

### <a name="f-unlocking-a-login"></a>F. Entsperren einer Anmeldung

Um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung zu entsperren, führen Sie die folgende Anweisung aus und ersetzen \*\*\*\* durch das gewünschte Kontokennwort.

```sql
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;

GO
```

Um eine Anmeldung zu entsperren, ohne das Kennwort zu ändern, deaktivieren Sie die Überprüfungsrichtlinie, und aktivieren Sie diese dann erneut.

```sql
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;
GO
```

### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. Ändern des Kennworts für eine Anmeldung mit HASHED

Im folgenden Beispiel wird das Kennwort für die `TestUser`-Anmeldung in einen bereits vorhandenen Hashwert geändert.

**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.

```sql
ALTER LOGIN TestUser WITH
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;
GO
```

## <a name="see-also"></a>Weitere Informationen

- [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md)
- [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [CREATE CREDENTIAL](../../t-sql/statements/create-credential-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)

::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

> ||||||
> |-|-|-|-|-|
> |[SQL Server](alter-login-transact-sql.md?view=sql-server-2017)|[SQL-Datenbank<br />Singleton/Pool für elastische Datenbanken](alter-login-transact-sql.md?view=azuresqldb-current)|**_\* SQL-Datenbank<br />verwaltete Instanz \*_**|[SQL Data<br />Warehouse](alter-login-transact-sql.md?view=azure-sqldw-latest)|[Analytics Platform<br />System (PDW)](alter-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-database-managed-instance"></a>Verwaltete Azure SQL-Datenbank-Instanz

## <a name="syntax"></a>Syntax

```
-- Syntax for SQL Server and Azure SQL Database managed instance

ALTER LOGIN login_name
    {
    <status_option>
    | WITH <set_option> [ ,... ]
    | <cryptographic_credential_option>
    }
[;]

<status_option> ::=
        ENABLE | DISABLE
  
<set_option> ::=
    PASSWORD = 'password' | hashed_password HASHED
    [
      OLD_PASSWORD = 'oldpassword'
      | <password_option> [<password_option> ]
    ]
    | DEFAULT_DATABASE = database
    | DEFAULT_LANGUAGE = language
    | NAME = login_name
    | CHECK_POLICY = { ON | OFF }
    | CHECK_EXPIRATION = { ON | OFF }
    | CREDENTIAL = credential_name
    | NO CREDENTIAL

<password_option> ::=
    MUST_CHANGE | UNLOCK

<cryptographic_credentials_option> ::=
    ADD CREDENTIAL credential_name
  | DROP CREDENTIAL credential_name
```

> [!NOTE]
> Die Azure AD-Administratorfunktion für verwaltete Instanzen nach der Erstellung wurde geändert. Weitere Informationen finden Sie unter [Neue Azure AD-Administratorfunktion für verwaltete Instanzen](/azure/sql-database/sql-database-aad-authentication-configure#new-azure-ad-admin-functionality-for-mi).

```
-- Syntax for Azure SQL Database managed instance using Azure AD logins

ALTER LOGIN login_name
  {
      <status_option>
    | WITH <set_option> [ ,.. .n ]
  }
[;]

<status_option> ::=
    ENABLE | DISABLE

<set_option> ::=
     DEFAULT_DATABASE = database
   | DEFAULT_LANGUAGE = language
```

## <a name="arguments"></a>Argumente

### <a name="arguments-applicable-to-sql-and-azure-ad-logins"></a>Argumente für SQL- und Azure AD-Anmeldeinformationen

*login_name* Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung an, die geändert wird. Azure AD-Anmeldeinformationen müssen im folgenden Format angegeben werden: user@domain. Zum Beispiel john.smith@contoso.com, oder als Azure AD-Gruppenname oder Anwendungsname. Bei Azure AD-Anmeldeinformationen muss *login_name* einem vorhandenen Azure AD-Konto entsprechen, das in der Masterdatenbank erstellt wurde.

ENABLE | DISABLE Aktiviert oder deaktiviert diese Anmeldung. Das Deaktivieren einer Anmeldung wirkt sich nicht auf das Verhalten der bereits verbundenen Anmeldungen aus. (Verwenden Sie die `KILL`-Anweisung, um eine vorhandene Verbindung zu beenden.) Deaktivierte Anmeldungen behalten ihre Berechtigungen bei und sind weiterhin für den Identitätswechsel verfügbar.

DEFAULT_DATABASE **=** _database_ Gibt eine Standarddatenbank an, die der Anmeldung zugewiesen werden soll.

DEFAULT_LANGUAGE **=** _language_ Gibt eine Standardsprache an, die der Anmeldung zugewiesen werden soll. Die Standardsprache für alle SQL-Datenbank-Anmeldungen ist Englisch und kann nicht geändert werden. Die Standardsprache der `sa`-Anmeldung bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter Linux ist Englisch. Diese kann jedoch geändert werden.

### <a name="arguments-applicable-only-to-sql-logins"></a>Argumente für SQL-Anmeldeinformationen

PASSWORD **='** _password_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt das Kennwort für die Anmeldung an, die geändert wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Kennwörter gelten außerdem nicht, wenn sie mit externen Anmeldeinformationen wie Azure AD-Anmeldeinformationen verwendet werden.

Ständig aktive Verbindungen mit SQL-Datenbank erfordern alle 10 Stunden eine erneute Authentifizierung, die von der Datenbank-Engine durchgeführt. Die Datenbank-Engine versucht, eine erneute Authentifizierung mit dem ursprünglich übermittelten Kennwort durchzuführen. Dabei ist keine Eingabe des Benutzers erforderlich. Aus Leistungsgründen wird die Verbindung nicht erneut authentifiziert, wenn ein Kennwort in SQL-Datenbank zurückgesetzt wird. Dies ist auch nicht der Fall, wenn die Verbindung aufgrund von Verbindungspooling zurückgesetzt wird. Dies unterscheidet sich von dem Verhalten von SQL Server (lokal). Wenn das Kennwort nach der ersten Authentifizierung der Verbindung geändert wurde, muss diese Verbindung beendet und eine neue unter Verwendung des neuen Kennworts hergestellt werden. Ein Benutzer mit der KILL DATABASE CONNECTION-Berechtigung kann eine Verbindung mit SQL-Datenbank mit dem Befehl KILL explizit beenden. Weitere Informationen finden Sie unter [KILL](../../t-sql/language-elements/kill-transact-sql.md).

PASSWORD **=** _hashed\_password_ Gilt nur für das HASHED-Schlüsselwort. Gibt den Hashwert des Kennworts für den Anmeldenamen an, der erstellt wird.

HASHED Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen. Gibt an, dass das nach dem PASSWORD-Argument eingegebene Kennwort bereits einen Hashwert darstellt. Wenn diese Option nicht ausgewählt wird, wird aus dem Kennwort vor dem Speichern in der Datenbank ein Hashwert erstellt. Diese Option sollte nur für die Anmeldungssynchronisierung zwischen zwei Servern verwendet werden. Verwenden Sie die HASHED-Option nicht, um Kennwörter routinemäßig zu ändern.

OLD_PASSWORD **='** _oldpassword_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Das aktuelle Kennwort der Anmeldung, der ein neues Kennwort zugewiesen wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

MUST_CHANGE<br>
Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Falls diese Option angegeben wird, fordert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Eingabe eines aktualisierten Kennworts auf, wenn die geänderte Anmeldung zum ersten Mal verwendet wird.

NAME = *login_name* Der neue Name der Anmeldung, die umbenannt wird. Falls es sich bei den Anmeldeinformationen um Windows-Anmeldeinformationen handelt, muss die SID des entsprechenden Windows-Prinzipals für den neuen Namen mit der SID übereinstimmen, die den Anmeldeinformationen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist. Der neue Name einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung darf keinen umgekehrten Schrägstrich (\\) enthalten.

CHECK_EXPIRATION = { ON | **OFF** } Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, ob die Richtlinie für das Ablaufen von Kennwörtern für diesen Anmeldenamen erzwungen werden soll. Der Standardwert ist OFF.

CHECK_POLICY **=** { **ON** | OFF } Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, dass die Windows-Kennwortrichtlinien des Computers, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, für diesen Anmeldenamen erzwungen werden sollen. Der Standardwert ist ON.

CREDENTIAL = *credential_name* Die Anmeldeinformationen, die einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung zugeordnet werden sollen. Die Anmeldeinformationen müssen bereits auf dem Server vorhanden sein. Weitere Informationen finden Sie unter [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md). Der sa-Anmeldung können keine Anmeldeinformationen zugeordnet werden.

NO CREDENTIAL Entfernt vorhandene Zuordnungen der Anmeldung zu Serveranmeldeinformationen. Weitere Informationen finden Sie unter [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md).

UNLOCK Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, dass die Sperre einer Anmeldung aufgehoben wird.

ADD CREDENTIAL Fügt der Anmeldung Anmeldeinformationen eines EKM-Anbieters (Extensible Key Management, erweiterbare Schlüsselverwaltung) hinzu. Weitere Informationen finden Sie unter [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md).

DROP CREDENTIAL Entfernt Anmeldeinformationen eines EKM-Anbieters (Extensible Key Management, erweiterbare Schlüsselverwaltung) aus der Anmeldung. Weitere Informationen finden Sie unter [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md).

## <a name="remarks"></a>Remarks

Wenn CHECK_POLICY auf ON festgelegt ist, kann das HASHED-Argument nicht verwendet werden.

Wenn CHECK_POLICY in ON geändert wird, passiert Folgendes:

- Der Kennwortverlauf wird mit dem Wert des aktuellen Kennworthashes initialisiert.

  Wenn CHECK_POLICY in OFF geändert wird, passiert Folgendes:

- CHECK_EXPIRATION wird ebenfalls auf OFF festgelegt.
- Der Kennwortverlauf wird gelöscht.
- Der Wert von *lockout_time* wird zurückgesetzt.

Falls MUST_CHANGE angegeben wird, müssen CHECK_EXPIRATION und CHECK_POLICY auf ON festgelegt werden. Andernfalls erzeugt die Anweisung einen Fehler.

Falls CHECK_POLICY auf OFF festgelegt ist, kann CHECK_EXPIRATION nicht auf ON festgelegt werden. Eine ALTER LOGIN-Anweisung mit dieser Kombination von Optionen erzeugt einen Fehler.

Sie können ALTER_LOGIN mit dem DISABLE-Argument nicht dazu verwenden, den Zugriff auf eine Windows-Gruppe zu verweigern. Dies ist beabsichtigt. ALTER_LOGIN [*domain\group*] DISABLE gibt zum Beispiel die folgende Fehlermeldung zurück:

    `"Msg 15151, Level 16, State 1, Line 1
    "Cannot alter the login '*Domain\Group*', because it does not exist or you do not have permission."`

In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] werden Anmeldedaten, die für die Authentifizierung einer Verbindung und Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um eine Aktualisierung des Authentifizierungscache zu erzwingen und sicherzustellen, dass eine Datenbank über die aktuelle Version der Tabelle mit Anmeldenamen verfügt.

## <a name="permissions"></a>Berechtigungen

Erfordert die ALTER ANY LOGIN-Berechtigung.

Falls die CREDENTIAL-Option verwendet wird, ist auch die ALTER ANY CREDENTIAL-Berechtigung erforderlich.

Wenn die zu ändernde Anmeldung Mitglied der festen Serverrolle **sysadmin** oder Empfänger der CONTROL SERVER-Berechtigung ist, ist auch die CONTROL SERVER-Berechtigung für die folgenden Änderungen erforderlich:

- Zurücksetzen des Kennworts ohne Eingabe des alten Kennworts.
- Aktivieren von MUST_CHANGE, CHECK_POLICY oder CHECK_EXPIRATION.
- Ändern des Anmeldenamens.
- Aktivieren oder Deaktivieren der Anmeldung.
- Zuordnen der Anmeldung zu anderen Anmeldeinformationen.

Ein Prinzipal kann das Kennwort, die Standardsprache und die Standarddatenbank für seine eigene Anmeldung ändern.

Nur ein SQL-Prinzipal mit `sysadmin`-Berechtigungen kann einen ALTER LOGIN-Befehl für Azure AD-Anmeldeinformationen ausführen.

## <a name="examples"></a>Beispiele

Zu diesen Beispielen gehören auch Beispiele zur Verwendung anderer SQL-Produkte. Oben sehen Sie, welche Argumente unterstützt werden.

### <a name="a-enabling-a-disabled-login"></a>A. Aktivieren einer deaktivierten Anmeldung

Im folgenden Beispiel wird die Anmeldung `Mary5` aktiviert.

```sql
ALTER LOGIN Mary5 ENABLE;
```

### <a name="b-changing-the-password-of-a-login"></a>B. Ändern des Kennworts einer Anmeldung

Im folgenden Beispiel wird das Kennwort der Anmeldung `Mary5` in ein sicheres Kennwort geändert.

```sql
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';
```

### <a name="c-changing-the-name-of-a-login"></a>C. Ändern des Namens einer Anmeldung

Im folgenden Beispiel wird der Name der Anmeldung `Mary5` in `John2` geändert.

```sql
ALTER LOGIN Mary5 WITH NAME = John2;
```

### <a name="d-mapping-a-login-to-a-credential"></a>D. Zuordnen einer Anmeldung zu Anmeldeinformationen

Im folgenden Beispiel wird die Anmeldung `John2` den Anmeldeinformationen `Custodian04` zugeordnet.

```sql
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;
```

### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>E. Zuordnen einer Anmeldung zu Anmeldeinformationen der erweiterbaren Schlüsselverwaltung

Im folgenden Beispiel wird die Anmeldung `Mary5` den EKM-Anmeldeinformationen `EKMProvider1` zugeordnet.

**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher und verwaltete Azure SQL-Datenbank-Instanzen.

```sql
ALTER LOGIN Mary5
ADD CREDENTIAL EKMProvider1;
GO
```

### <a name="f-unlocking-a-login"></a>F. Entsperren einer Anmeldung

Um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung zu entsperren, führen Sie die folgende Anweisung aus und ersetzen \*\*\*\* durch das gewünschte Kontokennwort.

```sql
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;

GO
```

Um eine Anmeldung zu entsperren, ohne das Kennwort zu ändern, deaktivieren Sie die Überprüfungsrichtlinie, und aktivieren Sie diese dann erneut.

```sql
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;
GO
```

### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. Ändern des Kennworts für eine Anmeldung mit HASHED

Im folgenden Beispiel wird das Kennwort für die `TestUser`-Anmeldung in einen bereits vorhandenen Hashwert geändert.

**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher und verwaltete Azure SQL-Datenbank-Instanzen.

```sql
ALTER LOGIN TestUser WITH
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;
GO
```

### <a name="h-disabling-the-login-of-an-azure-ad-user"></a>H. Deaktivieren der Anmeldeinformationen eines Azure AD-Benutzers

Im folgenden Beispiel werden die Anmeldeinformationen des Azure AD-Benutzers joe@contoso.com deaktiviert.

```sql
ALTER LOGIN [joe@contoso.com] DISABLE
```

## <a name="see-also"></a>Weitere Informationen

- [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md)
- [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [CREATE CREDENTIAL](../../t-sql/statements/create-credential-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> ||||||
> |-|-|-|-|-|
> |[SQL Server](alter-login-transact-sql.md?view=sql-server-2017)|[SQL-Datenbank<br />Singleton/Pool für elastische Datenbanken](alter-login-transact-sql.md?view=azuresqldb-current)|[SQL-Datenbank<br />verwaltete Instanz](alter-login-transact-sql.md?view=azuresqldb-mi-current)|**_\* SQL Data<br />Warehouse \*_**|[Analytics Platform<br />System (PDW)](alter-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

## <a name="azure-sql-data-warehouse"></a>Azure SQL Data Warehouse

## <a name="syntax"></a>Syntax

```
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse

ALTER LOGIN login_name
  {
      <status_option>
    | WITH <set_option> [ ,.. .n ]
  }
[;]

<status_option> ::=
    ENABLE | DISABLE
  
<set_option> ::=
    PASSWORD ='password'
    [
      OLD_PASSWORD ='oldpassword'
    ]
    | NAME = login_name
```

## <a name="arguments"></a>Argumente

*login_name* Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung an, die geändert wird. Domänenanmeldungen müssen in Klammern eingeschlossen werden: [Domäne\Benutzer].

ENABLE | DISABLE Aktiviert oder deaktiviert diese Anmeldung. Das Deaktivieren einer Anmeldung wirkt sich nicht auf das Verhalten der bereits verbundenen Anmeldungen aus. (Verwenden Sie die `KILL`-Anweisung, um eine vorhandene Verbindung zu beenden.) Deaktivierte Anmeldungen behalten ihre Berechtigungen bei und sind weiterhin für den Identitätswechsel verfügbar.

PASSWORD **='** _password_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt das Kennwort für die Anmeldung an, die geändert wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

Ständig aktive Verbindungen mit SQL-Datenbank erfordern alle 10 Stunden eine erneute Authentifizierung, die von der Datenbank-Engine durchgeführt. Die Datenbank-Engine versucht, eine erneute Authentifizierung mit dem ursprünglich übermittelten Kennwort durchzuführen. Dabei ist keine Eingabe des Benutzers erforderlich. Aus Leistungsgründen wird die Verbindung nicht erneut authentifiziert, wenn ein Kennwort in SQL-Datenbank zurückgesetzt wird. Dies ist auch nicht der Fall, wenn die Verbindung aufgrund von Verbindungspooling zurückgesetzt wird. Dies unterscheidet sich von dem Verhalten von SQL Server (lokal). Wenn das Kennwort nach der ersten Authentifizierung der Verbindung geändert wurde, muss diese Verbindung beendet und eine neue unter Verwendung des neuen Kennworts hergestellt werden. Ein Benutzer mit der KILL DATABASE CONNECTION-Berechtigung kann eine Verbindung mit SQL-Datenbank mit dem Befehl KILL explizit beenden. Weitere Informationen finden Sie unter [KILL](../../t-sql/language-elements/kill-transact-sql.md).

> [!IMPORTANT]
> Wenn für eine Anmeldung (oder den Benutzer einer eigenständigen Datenbank) eine Verbindung hergestellt und diese authentifiziert wird, werden von der Verbindung Identitätsinformationen zur Anmeldung zwischengespeichert. Bei einer Anmeldung unter Verwendung der Windows-Authentifizierung umfassen die Informationen Angaben zur Mitgliedschaft in Windows-Gruppen. Die Identität der Anmeldung bleibt für die Dauer der Verbindung authentifiziert. Um Identitätsänderungen zu erzwingen, z. B. das Zurücksetzen eines Kennworts oder eine Änderung der Windows-Gruppenmitgliedschaft, muss die Anmeldung von der Authentifizierungsstelle (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) abgemeldet und erneut angemeldet werden. Ein Mitglied der festen Serverrolle **sysadmin** oder eine beliebige Anmeldung mit der **ALTER ANY CONNECTION** -Berechtigung kann den **KILL** -Befehl verwenden, um eine Verbindung zu beenden und zu erzwingen, dass für eine Anmeldung eine erneute Verbindung hergestellt wird. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ist in der Lage, Verbindungsinformationen wiederzuverwenden, wenn mehrere Verbindungen mit dem Fenster Objekt-Explorer und Abfrage-Editor hergestellt werden. Schließen Sie alle Verbindungen, um eine erneute Verbindung zu erzwingen.

OLD_PASSWORD **='** _oldpassword_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Das aktuelle Kennwort der Anmeldung, der ein neues Kennwort zugewiesen wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

NAME = *login_name* Der neue Name der Anmeldung, die umbenannt wird. Falls es sich dabei um eine Windows-Anmeldung handelt, muss die SID des entsprechenden Windows-Prinzipals für den neuen Namen mit der SID übereinstimmen, die der Anmeldung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist. Der neue Name einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung darf keinen umgekehrten Schrägstrich (\\) enthalten.

## <a name="remarks"></a>Remarks

In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] werden Anmeldedaten, die für die Authentifizierung einer Verbindung und Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um das Aktualisieren der Authentifizierungsdatenbank zu erzwingen und sicherzustellen, dass die Datenbank über die aktuelle Version der Tabelle mit Anmeldenamen verfügt.

## <a name="permissions"></a>Berechtigungen

Erfordert die ALTER ANY LOGIN-Berechtigung.

Wenn die zu ändernde Anmeldung Mitglied der festen Serverrolle **sysadmin** oder Empfänger der CONTROL SERVER-Berechtigung ist, ist auch die CONTROL SERVER-Berechtigung für die folgenden Änderungen erforderlich:

- Zurücksetzen des Kennworts ohne Eingabe des alten Kennworts.
- Ändern des Anmeldenamens.
- Aktivieren oder Deaktivieren der Anmeldung.
- Zuordnen der Anmeldung zu anderen Anmeldeinformationen.

Ein Prinzipal kann das Kennwort seiner eigenen Anmeldung ändern.

## <a name="examples"></a>Beispiele

Zu diesen Beispielen gehören auch Beispiele zur Verwendung anderer SQL-Produkte. Oben sehen Sie, welche Argumente unterstützt werden.

### <a name="a-enabling-a-disabled-login"></a>A. Aktivieren einer deaktivierten Anmeldung

Im folgenden Beispiel wird die Anmeldung `Mary5` aktiviert.

```sql
ALTER LOGIN Mary5 ENABLE;
```

### <a name="b-changing-the-password-of-a-login"></a>B. Ändern des Kennworts einer Anmeldung

Im folgenden Beispiel wird das Kennwort der Anmeldung `Mary5` in ein sicheres Kennwort geändert.

```sql
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';
```

### <a name="c-changing-the-name-of-a-login"></a>C. Ändern des Namens einer Anmeldung

Im folgenden Beispiel wird der Name der Anmeldung `Mary5` in `John2` geändert.

```sql
ALTER LOGIN Mary5 WITH NAME = John2;
```

### <a name="d-mapping-a-login-to-a-credential"></a>D. Zuordnen einer Anmeldung zu Anmeldeinformationen

Im folgenden Beispiel wird die Anmeldung `John2` den Anmeldeinformationen `Custodian04` zugeordnet.

```sql
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;
```

### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>E. Zuordnen einer Anmeldung zu Anmeldeinformationen der erweiterbaren Schlüsselverwaltung

Im folgenden Beispiel wird die Anmeldung `Mary5` den EKM-Anmeldeinformationen `EKMProvider1` zugeordnet.

**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.

```sql
ALTER LOGIN Mary5
ADD CREDENTIAL EKMProvider1;
GO
```

### <a name="f-unlocking-a-login"></a>F. Entsperren einer Anmeldung

Um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung zu entsperren, führen Sie die folgende Anweisung aus und ersetzen \*\*\*\* durch das gewünschte Kontokennwort.

```sql
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;

GO
```

Um eine Anmeldung zu entsperren, ohne das Kennwort zu ändern, deaktivieren Sie die Überprüfungsrichtlinie, und aktivieren Sie diese dann erneut.

```sql
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;
GO
```

### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. Ändern des Kennworts für eine Anmeldung mit HASHED

Im folgenden Beispiel wird das Kennwort für die `TestUser`-Anmeldung in einen bereits vorhandenen Hashwert geändert.

**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.

```sql
ALTER LOGIN TestUser WITH
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;
GO
```

## <a name="see-also"></a>Weitere Informationen

- [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md)
- [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [CREATE CREDENTIAL](../../t-sql/statements/create-credential-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)

::: moniker-end
::: moniker range=">=aps-pdw-2016||=sqlallproducts-allversions"

> ||||||
> |-|-|-|-|-|
> |[SQL Server](alter-login-transact-sql.md?view=sql-server-2017)|[SQL-Datenbank<br />Singleton/Pool für elastische Datenbanken](alter-login-transact-sql.md?view=azuresqldb-current)|[SQL-Datenbank<br />verwaltete Instanz](alter-login-transact-sql.md?view=azuresqldb-mi-current)|[SQL Data<br />Warehouse](alter-login-transact-sql.md?view=azure-sqldw-latest)|**_\* Analytics<br />Platform System (PDW) \*_**

&nbsp;

## <a name="analytics-platform-system"></a>Analyseplattformsystem

## <a name="syntax"></a>Syntax

```
-- Syntax for Analytics Platform System

ALTER LOGIN login_name
    {
    <status_option>
    | WITH <set_option> [ ,... ]
    }

<status_option> ::=ENABLE | DISABLE

<set_option> ::=
    PASSWORD ='password'
    [
      OLD_PASSWORD ='oldpassword'
      | <password_option> [<password_option> ]
    ]
    | NAME = login_name
    | CHECK_POLICY = { ON | OFF }
    | CHECK_EXPIRATION = { ON | OFF }

<password_option> ::=
    MUST_CHANGE | UNLOCK
```

## <a name="arguments"></a>Argumente

*login_name* Gibt den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung an, die geändert wird. Domänenanmeldungen müssen in Klammern eingeschlossen werden: [Domäne\Benutzer].

ENABLE | DISABLE Aktiviert oder deaktiviert diese Anmeldung. Das Deaktivieren einer Anmeldung wirkt sich nicht auf das Verhalten der bereits verbundenen Anmeldungen aus. (Verwenden Sie die `KILL`-Anweisung, um eine vorhandene Verbindung zu beenden.) Deaktivierte Anmeldungen behalten ihre Berechtigungen bei und sind weiterhin für den Identitätswechsel verfügbar.

PASSWORD **='** _password_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt das Kennwort für die Anmeldung an, die geändert wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

> [!IMPORTANT]
> Wenn für eine Anmeldung (oder den Benutzer einer eigenständigen Datenbank) eine Verbindung hergestellt und diese authentifiziert wird, werden von der Verbindung Identitätsinformationen zur Anmeldung zwischengespeichert. Bei einer Anmeldung unter Verwendung der Windows-Authentifizierung umfassen die Informationen Angaben zur Mitgliedschaft in Windows-Gruppen. Die Identität der Anmeldung bleibt für die Dauer der Verbindung authentifiziert. Um Identitätsänderungen zu erzwingen, z. B. das Zurücksetzen eines Kennworts oder eine Änderung der Windows-Gruppenmitgliedschaft, muss die Anmeldung von der Authentifizierungsstelle (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) abgemeldet und erneut angemeldet werden. Ein Mitglied der festen Serverrolle **sysadmin** oder eine beliebige Anmeldung mit der **ALTER ANY CONNECTION** -Berechtigung kann den **KILL** -Befehl verwenden, um eine Verbindung zu beenden und zu erzwingen, dass für eine Anmeldung eine erneute Verbindung hergestellt wird. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ist in der Lage, Verbindungsinformationen wiederzuverwenden, wenn mehrere Verbindungen mit dem Fenster Objekt-Explorer und Abfrage-Editor hergestellt werden. Schließen Sie alle Verbindungen, um eine erneute Verbindung zu erzwingen.

OLD_PASSWORD **='** _oldpassword_ **'** Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Das aktuelle Kennwort der Anmeldung, der ein neues Kennwort zugewiesen wird. Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.

MUST_CHANGE Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Falls diese Option angegeben wird, fordert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Eingabe eines aktualisierten Kennworts auf, wenn die geänderte Anmeldung zum ersten Mal verwendet wird.

NAME = *login_name* Der neue Name der Anmeldung, die umbenannt wird. Falls es sich bei den Anmeldeinformationen um Windows-Anmeldeinformationen handelt, muss die SID des entsprechenden Windows-Prinzipals für den neuen Namen mit der SID übereinstimmen, die den Anmeldeinformationen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist. Der neue Name einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung darf keinen umgekehrten Schrägstrich (\\) enthalten.

CHECK_EXPIRATION = { ON | **OFF** } Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, ob die Richtlinie für das Ablaufen von Kennwörtern für diesen Anmeldenamen erzwungen werden soll. Der Standardwert ist OFF.

CHECK_POLICY **=** { **ON** | OFF } Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, dass die Windows-Kennwortrichtlinien des Computers, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, für diesen Anmeldenamen erzwungen werden sollen. Der Standardwert ist ON.

UNLOCK Gilt nur für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldungen. Gibt an, dass die Sperre einer Anmeldung aufgehoben wird.

## <a name="remarks"></a>Remarks

Wenn CHECK_POLICY auf ON festgelegt ist, kann das HASHED-Argument nicht verwendet werden.

Wenn CHECK_POLICY in ON geändert wird, passiert Folgendes:

- Der Kennwortverlauf wird mit dem Wert des aktuellen Kennworthashes initialisiert.

  Wenn CHECK_POLICY in OFF geändert wird, passiert Folgendes:

- CHECK_EXPIRATION wird ebenfalls auf OFF festgelegt.
- Der Kennwortverlauf wird gelöscht.
- Der Wert von *lockout_time* wird zurückgesetzt.

Falls MUST_CHANGE angegeben wird, müssen CHECK_EXPIRATION und CHECK_POLICY auf ON festgelegt werden. Andernfalls erzeugt die Anweisung einen Fehler.

Falls CHECK_POLICY auf OFF festgelegt ist, kann CHECK_EXPIRATION nicht auf ON festgelegt werden. Eine ALTER LOGIN-Anweisung mit dieser Kombination von Optionen erzeugt einen Fehler.

Sie können ALTER_LOGIN mit dem DISABLE-Argument nicht dazu verwenden, den Zugriff auf eine Windows-Gruppe zu verweigern. Dies ist beabsichtigt. ALTER_LOGIN [*domain\group*] DISABLE gibt zum Beispiel die folgende Fehlermeldung zurück:

    `"Msg 15151, Level 16, State 1, Line 1
    "Cannot alter the login '*Domain\Group*', because it does not exist or you do not have permission."`

In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] werden Anmeldedaten, die für die Authentifizierung einer Verbindung und Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um eine Aktualisierung des Authentifizierungscache zu erzwingen und sicherzustellen, dass eine Datenbank über die aktuelle Version der Tabelle mit Anmeldenamen verfügt.

## <a name="permissions"></a>Berechtigungen

Erfordert die ALTER ANY LOGIN-Berechtigung.

Falls die CREDENTIAL-Option verwendet wird, ist auch die ALTER ANY CREDENTIAL-Berechtigung erforderlich.

Wenn die zu ändernde Anmeldung Mitglied der festen Serverrolle **sysadmin** oder Empfänger der CONTROL SERVER-Berechtigung ist, ist auch die CONTROL SERVER-Berechtigung für die folgenden Änderungen erforderlich:

- Zurücksetzen des Kennworts ohne Eingabe des alten Kennworts.
- Aktivieren von MUST_CHANGE, CHECK_POLICY oder CHECK_EXPIRATION.
- Ändern des Anmeldenamens.
- Aktivieren oder Deaktivieren der Anmeldung.
- Zuordnen der Anmeldung zu anderen Anmeldeinformationen.

Ein Prinzipal kann das Kennwort, die Standardsprache und die Standarddatenbank für seine eigene Anmeldung ändern.

## <a name="examples"></a>Beispiele

Zu diesen Beispielen gehören auch Beispiele zur Verwendung anderer SQL-Produkte. Oben sehen Sie, welche Argumente unterstützt werden.

### <a name="a-enabling-a-disabled-login"></a>A. Aktivieren einer deaktivierten Anmeldung

Im folgenden Beispiel wird die Anmeldung `Mary5` aktiviert.

```sql
ALTER LOGIN Mary5 ENABLE;
```

### <a name="b-changing-the-password-of-a-login"></a>B. Ändern des Kennworts einer Anmeldung

Im folgenden Beispiel wird das Kennwort der Anmeldung `Mary5` in ein sicheres Kennwort geändert.

```sql
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';
```

### <a name="c-changing-the-name-of-a-login"></a>C. Ändern des Namens einer Anmeldung

Im folgenden Beispiel wird der Name der Anmeldung `Mary5` in `John2` geändert.

```sql
ALTER LOGIN Mary5 WITH NAME = John2;
```

### <a name="d-mapping-a-login-to-a-credential"></a>D. Zuordnen einer Anmeldung zu Anmeldeinformationen

Im folgenden Beispiel wird die Anmeldung `John2` den Anmeldeinformationen `Custodian04` zugeordnet.

```sql
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;
```

### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>E. Zuordnen einer Anmeldung zu Anmeldeinformationen der erweiterbaren Schlüsselverwaltung

Im folgenden Beispiel wird die Anmeldung `Mary5` den EKM-Anmeldeinformationen `EKMProvider1` zugeordnet.

**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.

```sql
ALTER LOGIN Mary5
ADD CREDENTIAL EKMProvider1;
GO
```

### <a name="f-unlocking-a-login"></a>F. Entsperren einer Anmeldung

Um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldung zu entsperren, führen Sie die folgende Anweisung aus und ersetzen \*\*\*\* durch das gewünschte Kontokennwort.

```sql
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;

GO
```

Um eine Anmeldung zu entsperren, ohne das Kennwort zu ändern, deaktivieren Sie die Überprüfungsrichtlinie, und aktivieren Sie diese dann erneut.

```sql
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;
GO
```

### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. Ändern des Kennworts für eine Anmeldung mit HASHED

Im folgenden Beispiel wird das Kennwort für die `TestUser`-Anmeldung in einen bereits vorhandenen Hashwert geändert.

**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.

```sql
ALTER LOGIN TestUser WITH
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;
GO
```

## <a name="see-also"></a>Weitere Informationen

- [Anmeldeinformationen](../../relational-databases/security/authentication-access/credentials-database-engine.md)
- [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)
- [CREATE CREDENTIAL](../../t-sql/statements/create-credential-transact-sql.md)
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)
- [Erweiterbare Schlüsselverwaltung (Extensible Key Management, EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)

::: moniker-end
