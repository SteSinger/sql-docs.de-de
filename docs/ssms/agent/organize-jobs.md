---
title: Organisieren von Aufträgen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job category
- organize jobs
ms.assetid: 629c3e06-f933-483b-8621-280dbb7a7bd1
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b2167ec7aaf1656312e81abc842c3910a5522947
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68260033"
---
# <a name="organize-jobs"></a>Aufträge organisieren
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Auftragskategorien helfen Ihnen dabei, Ihre Aufträge zum einfachen Filtern und Gruppieren zu organisieren. Sie können z. B. alle Aufträge für die Datenbanksicherung in der Datenbankwartungskategorie organisieren. Sie können zudem eigene Auftragskategorien erstellen.  
  
> [!WARNING]  
> Multiserverkategorien sind nur auf einem Masterserver vorhanden. Auf einem Masterserver ist nur eine Standardauftragskategorie verfügbar: [**Nicht kategorisiert (Multiserver)** ]. Beim Herunterladen eines Multiserverauftrags wird seine Kategorie auf dem Zielserver in **Aufträge vom MSX** geändert.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Beschreibung**|**Thema**|  
|Beschreibt, wie eine Auftragskategorie erstellt wird.|[Erstellen einer Auftragskategorie](../../ssms/agent/create-a-job-category.md)|  
|Beschreibt, wie eine Auftragskategorie gelöscht wird.|[Löschen einer Auftragskategorie](../../ssms/agent/delete-a-job-category.md)|  
|Beschreibt, wie ein Auftrag einer Auftragskategorie zugewiesen wird.|[Zuweisen eines Auftrags zu einer Auftragskategorie](../../ssms/agent/assign-a-job-to-a-job-category.md)|  
|Beschreibt, wie die Mitgliedschaft in einer Auftragskategorie geändert wird.|[Change the Membership of a Job Category](../../ssms/agent/change-the-membership-of-a-job-category.md)|  
|Beschreibt, wie die Kategorieinformationen aufgelistet werden.|[Auflisten von Informationen zu Auftragskategorien](../../ssms/agent/list-job-category-information.md)|  
  
