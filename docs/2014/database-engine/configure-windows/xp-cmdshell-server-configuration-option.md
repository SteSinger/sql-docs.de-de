---
title: xp_cmdshell (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9f4ab373c9827adff6e0138a81b5eaa57d1c4414
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62755172"
---
# <a name="xpcmdshell-server-configuration-option"></a>xp_cmdshell (Serverkonfigurationsoption)
  Die **xp_cmdshell** -Option ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Serverkonfigurationsoption, mit der Systemadministratoren steuern können, ob auf einem System die erweiterte gespeicherte Prozedur **xp_cmdshell** ausgeführt werden kann. Die Option **xp_cmdshell** ist in neuen Installationen standardmäßig deaktiviert. Sie kann mithilfe der richtlinienbasierten Verwaltung oder durch Ausführen der gespeicherten Systemprozedur **sp_configure** aktiviert werden, wie im folgenden Beispiel dargestellt:  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
