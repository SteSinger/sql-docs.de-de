---
title: sp_fulltext_load_thesaurus_file (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_load_thesaurus_file
- sp_fulltext_load_thesaurus_file_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_load_thesaurus_file
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], editing
ms.assetid: 73a309c3-6d22-42dc-a6fe-8a63747aa2e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 96fb5c880346c534c3b956e577f15622e598d48c
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305213"
---
# <a name="sp_fulltext_load_thesaurus_file-transact-sql"></a>sp_fulltext_load_thesaurus_file (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Veranlasst die Serverinstanz, die Daten aus der Thesaurusdatei zu analysieren und zu laden, die der Sprache des angegebenen Gebietsschemabezeichners (Locale Identifier, LCID) entspricht. Diese gespeicherte Prozedur bietet sich zur Anwendung nach dem Update einer Thesaurusdatei an. Das Ausführen von **sp_fulltext_load_thesaurus_file** bewirkt eine Neukompilierung von voll Text Abfragen, die den Thesaurus der angegebenen LCID verwenden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sys.sp_fulltext_load_thesaurus_file lcid [ , @loadOnlyIfNotLoaded  = action ]   
```  
  
## <a name="arguments"></a>Argumente  
 *lcid*  
 Eine ganze Zahl, mit der der Gebietsschemabezeichner (LCID) der Sprache zugeordnet wird, für die Sie die Thesaurus-XML-Definition laden möchten. Verwenden Sie die [sys. fulltext_languages &#40;-Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md) -Katalog Sicht, um die LCIDs von Sprachen zu erhalten, die auf einer Serverinstanz verfügbar sind.  
  
 **\@loadonlyifnotloaded** = -*Aktion*  
 Gibt an, ob die Thesaurusdatei in die internen Thesaurustabellen geladen wird, auch wenn sie bereits geladen wurde. die *Aktion* ist eine von:  
  
|Wert|Definition|  
|-----------|----------------|  
|**0**|Die Thesaurusdatei wird geladen, auch wenn sie bereits geladen wurde. Dies ist das Standardverhalten von **sp_fulltext_load_thesaurus_file**.|  
|1|Die Thesaurusdatei wird nur geladen, wenn Sie noch nicht geladen wurde.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 None  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Thesaurusdateien werden automatisch von Volltextabfragen geladen, die den Thesaurus verwenden. Um die Auswirkungen auf die erstmalige Leistung von voll Text Abfragen zu vermeiden, empfiehlt es sich, **sp_fulltext_load_thesaurus_file**auszuführen.  
  
 Verwenden Sie [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)'**update_languages**', um die Liste der Sprachen zu aktualisieren, die bei der Volltextsuche registriert sind.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der Systemadministrator können die gespeicherte Prozedur **sp_fulltext_load_thesaurus_file** ausführen.  
  
 Nur Systemadministratoren können Thesaurusdateien aktualisieren, ändern und löschen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-load-a-thesaurus-file-even-if-it-is-already-loaded"></a>A. Laden einer Thesaurusdatei, auch wenn sie bereits geladen wurde  
 Im folgenden Beispiel wird die Thesaurusdatei für die englische Sprache analysiert und geladen.  
  
```sql
EXEC sys.sp_fulltext_load_thesaurus_file 1033;
```  
  
### <a name="b-load-a-thesaurus-file-only-if-it-is-not-yet-loaded"></a>B. Laden einer Thesaurusdatei nur dann, wenn Sie noch nicht geladen wurde  
 Im folgenden Beispiel wird die Thesaurusdatei für die arabische Sprache nur dann analysiert und geladen, wenn sie noch nicht geladen wurde.  
  
```sql
EXEC sys.sp_fulltext_load_thesaurus_file 1025, @loadOnlyIfNotLoaded = 1;
```  

## <a name="see-also"></a>Siehe auch

[FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)  
[Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
[Konfigurieren und Verwalten von Thesaurusdateien für die Volltextsuche](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)
