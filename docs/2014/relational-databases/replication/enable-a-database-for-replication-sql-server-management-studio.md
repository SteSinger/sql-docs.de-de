---
title: Aktivieren einer Datenbank für die Replikation (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f31471aceef4937ee34d6492605e3a98dbcd973b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721334"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>Aktivieren einer Datenbank für die Replikation (SQL Server Management Studio)
  Eine Datenbank wird implizit für die Replikation aktiviert, wenn ein Mitglied der festen Serverrolle **sysadmin** mit dem Assistenten für neue Veröffentlichung eine Veröffentlichung erstellt. Ein Mitglied der festen Serverrolle **sysadmin** kann eine Datenbank auch explizit für die Replikation aktivieren, sodass ein Mitglied der festen Datenbankrolle **db_owner** eine oder mehrere Veröffentlichungen in der Datenbank erstellen kann. Verwenden Sie zum expliziten Aktivieren einer Datenbank im Dialogfeld **Verlegereigenschaften – \<Verleger>** die Seite **Veröffentlichungsdatenbanken**. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [Create a Publication](publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>So aktivieren Sie eine Datenbank für die Replikation  
  
1.  Aktivieren Sie im Dialogfeld **Verlegereigenschaften - \<Verleger>** auf der Seite **Veröffentlichungsdatenbanken** das Kontrollkästchen **Transaktionsreplikation** und/oder **Mergereplikation** für jede Datenbank, die Sie replizieren möchten. Aktivieren Sie **Transaktionsreplikation** , um die Datenbank für die Momentaufnahmereplikation zu aktivieren.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
