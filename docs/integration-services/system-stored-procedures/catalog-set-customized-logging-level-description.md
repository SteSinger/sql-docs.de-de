---
title: catalog.set_customized_logging_level_description | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 6ceaa39f-2439-457b-b99f-f12d88a1be32
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b836c5b2ef056e630a5ff6bf00848fa5bb3a5e31
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295354"
---
# <a name="catalogset_customized_logging_level_description"></a>catalog.set_customized_logging_level_description 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Ändert die Beschreibung eines vorhandenen benutzerdefinierten Protokolliergrads. Weitere Informationen zu benutzerdefinierten Protokolliergraden finden Sie unter [Integration Services &#40;SSIS&#41; Logging (SSIS-Protokollierung [SQL Server Integration Services])](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Syntax  
  
```sql  
catalog.set_customized_logging_level_description [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
```  
  
## <a name="arguments"></a>Argumente  
 [ @level_name = ] *level_name*  
 Der Name für einen vorhandenen benutzerdefinierten Protokolliergrad.  
  
 Das Argument *level_name* ist vom Typ **nvarchar(128)** .  
  
 [ @level_description = ] *level_description*  
 Die neue Beschreibung für den jeweiligen benutzerdefinierten Protokolliergrad.  
  
 Das Argument *level_description* ist vom Typ **nvarchar(1024)** .  
  
## <a name="remarks"></a>Remarks  
  
## <a name="return-codes"></a>Rückgabecodes  
 0 (Erfolg)  
  
 Wenn die gespeicherte Prozedur fehlschlägt, wird ein Fehler ausgelöst.  
  
## <a name="result-set"></a>Resultset  
 None  
  
## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
  
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
  
## <a name="errors-and-warnings"></a>Fehler und Warnungen  
 Die folgende Liste beschreibt Bedingungen, unter denen die gespeicherte Prozedur fehlschlägt.  
  
-   Der Benutzer verfügt nicht über die erforderlichen Berechtigungen.  
  
  
