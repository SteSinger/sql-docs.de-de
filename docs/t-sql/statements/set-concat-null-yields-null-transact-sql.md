---
title: SET CONCAT_NULL_YIELDS_NULL (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CONCAT_NULL_YIELDS_NULL_TSQL
- SET CONCAT_NULL_YIELDS_NULL
- CONCAT_NULL_YIELDS_NULL
- SET_CONCAT_NULL_YIELDS_NULL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_NULL_YIELDS_NULL option
- null values [SQL Server], concatenation results
- concatenation [SQL Server]
- SET CONCAT_NULL_YIELDS_NULL statement
ms.assetid: 3091b71c-6518-4eb4-88ab-acae49102bc5
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 33a6e32fead5e2c16a9b1c66d6de78d49adbee58
ms.sourcegitcommit: eae9efe2a2d3758685e85039ffb8fa698aa47f9b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73962446"
---
# <a name="set-concat_null_yields_null-transact-sql"></a>SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Steuert die Behandlung von Verkettungsergebnissen als NULL-Werte oder als leere Zeichenfolgen.  
  
> [!IMPORTANT]  
>  In einer späteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird CONCAT_NULL_YIELDS_NULL immer auf ON festgelegt, und jede Anwendung, die für die Option explizit OFF festlegt, löst einen Fehler aus. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql
-- Syntax for SQL Server  
    
SET CONCAT_NULL_YIELDS_NULL { ON | OFF }   
```  
  
```sql
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET CONCAT_NULL_YIELDS_NULL ON    
```  
  
## <a name="remarks"></a>Remarks  
 Wenn SET CONCAT_NULL_YIELDS_NULL auf ON festgelegt ist, führt die Verkettung eines NULL-Wertes mit einer Zeichenfolge zum Ergebnis NULL. `SELECT 'abc' + NULL` ergibt beispielsweise `NULL`. Wenn SET CONCAT_NULL_YIELDS_NULL auf OFF festgelegt ist, erzeugt die Verkettung eines NULL-Wertes mit einer Zeichenfolge als Ergebnis die Zeichenfolge (der NULL-Wert wird als leere Zeichenfolge behandelt). `SELECT 'abc' + NULL` ergibt beispielsweise `abc`.  
  
 Wenn SET CONCAT_NULL_YIELDS_NULL nicht angegeben ist, gilt die Einstellung der **CONCAT_NULL_YIELDS_NULL**-Datenbankoption.  
  
> [!NOTE]  
>  SET CONCAT_NULL_YIELDS_NULL stimmt mit der CONCAT_NULL_YIELDS_NULL-Einstellung von ALTER DATABASE überein.  
  
 Die Einstellung von SET CONCAT_NULL_YIELDS_NULL wird zur Ausführungszeit und nicht zur Analysezeit festgelegt.  

SET CONCAT_NULL_YIELDS_NULL muss beim Erstellen oder Ändern von indizierten Sichten, Indizes für berechnete Spalten, gefilterte Indizes oder räumliche Indizes auf **ON** festgelegt sein. Wenn SET CONCAT_NULL_YIELDS_NULL auf **OFF** festgelegt ist, treten bei CREATE-, UPDATE-, INSERT- und DELETE-Anweisungen in Tabellen mit Indizes für berechnete Spalten, gefilterte Indices, räumliche Indizes oder indizierte Sichten Fehler auf. Weitere Informationen zu den erforderlichen Einstellungen der SET-Option mit indizierten Sichten und Indizes für berechnete Spalten finden Sie in den Überlegungen zum Verwenden der SET-Anweisungen unter [SET-Anweisungen &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md).
  
 Wenn CONCAT_NULL_YIELDS_NULL auf OFF festgelegt wird, ist die Zeichenfolgenverkettung über Servergrenzen hinweg nicht möglich.  
  
 Um die aktuelle Einstellung anzuzeigen, führen Sie die folgende Abfrage aus.  
  
```sql
DECLARE @CONCAT_SETTING VARCHAR(3) = 'OFF';  
IF ( (4096 & @@OPTIONS) = 4096 ) SET @CONCAT_SETTING = 'ON';  
SELECT @CONCAT_SETTING AS CONCAT_NULL_YIELDS_NULL; 
```  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung beider `SET CONCAT_NULL_YIELDS_NULL`-Einstellungen.  
  
```sql
PRINT 'Setting CONCAT_NULL_YIELDS_NULL ON';  
GO  
-- SET CONCAT_NULL_YIELDS_NULL ON and testing.  
SET CONCAT_NULL_YIELDS_NULL ON;  
GO  
SELECT 'abc' + NULL ;  
GO  
  
-- SET CONCAT_NULL_YIELDS_NULL OFF and testing.  
SET CONCAT_NULL_YIELDS_NULL OFF;  
GO  
SELECT 'abc' + NULL;   
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SET-Anweisungen (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  
