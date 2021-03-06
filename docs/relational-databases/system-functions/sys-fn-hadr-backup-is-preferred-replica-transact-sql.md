---
title: Sys. fn_hadr_backup_is_preferred_replica (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_hadr_backup_is_preferred_replica_TSQL
- sys.fn_hadr_backup_is_preferred_replica
- fn_hadr_backup_is_preferred_replica_TSQL
- fn_hadr_backup_is_preferred_replica
dev_langs:
- TSQL
helpviewer_keywords:
- backup on secondary replicas
- active secondary replicas [SQL Server], backup on secondary replicas
- sys.fn_hadr_backup_is_preferred_replica function
ms.assetid: 61b9be77-e2f6-4da1-b2ae-a62cbe226145
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4e343e7e9657b69ebd06a147cb99fa19e3c36aab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68120246"
---
# <a name="sysfnhadrbackupispreferredreplica--transact-sql"></a>Sys. fn_hadr_backup_is_preferred_replica (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Dient zum Ermitteln, ob das aktuelle Replikat das bevorzugte Sicherungsreplikat ist.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.fn_hadr_backup_is_preferred_replica ( 'dbname' )  
```  
  
## <a name="arguments"></a>Argumente  
 "*Dbname*"  
 Der Name der zu sichernden Datenbank. *Dbname* Typ Sysname ist.  
  
## <a name="returns"></a>Rückgabewert  
 Gibt 1 zurück, wenn die Datenbank auf der aktuellen Instanz das bevorzugte Replikat ist. Andernfalls wird 0 zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie diese Funktion in einem Sicherungsskript, um zu ermitteln, ob sich die aktuelle Datenbank auf dem für Sicherungen bevorzugten Replikat befindet. Sie können ein Skript über jedes Verfügbarkeitsreplikat ausführen. Jeder dieser Aufträge untersucht die gleichen Daten, um zu bestimmen, welcher Auftrag auszuführen, nur eine der geplanten Aufträge fortgesetzt, die tatsächlich in den Sicherungsstatus vorhanden. Beispielcode kann sich wie folgt zusammensetzen.  
  
```  
If sys.fn_hadr_backup_is_preferred_replica( @dbname ) <> 1   
BEGIN  
-- If this is not the preferred replica, exit (probably without error).  
END  
-- If this is the preferred replica, continue to do the backup.  
  
```  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-sysfnhadrbackupispreferredreplica"></a>A. Verwenden von sys.fn_hadr_backup_is_preferred_replica  
 Im folgenden Beispiel wird 1 zurückgegeben, wenn die aktuelle Datenbank dem bevorzugten Sicherungsreplikat entspricht.  
  
```  
SELECT sys.fn_hadr_backup_is_preferred_replica ('TestDB');  
GO  
```  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Always On-Verfügbarkeitsgruppen Funktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/always-on-availability-groups-functions-transact-sql.md)   
 [Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [Aktive sekundäre Replikate: Sicherung auf sekundären Replikaten &#40;Always On-Verfügbarkeitsgruppen&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)[Always On-Verfügbarkeitsgruppen-Katalogsichten &#40;Transact-SQL    &#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)  
  
  
