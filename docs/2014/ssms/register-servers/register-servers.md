---
title: Registrieren von Servern
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlserverregisteredserver.dhelp
helpviewer_keywords:
- connections [SQL Server], registered servers
- registering servers
- servers [SQL Server], registering
- server management [SQL Server], registering servers
- server registration [SQL Server]
ms.assetid: c2a2513e-fa09-419c-99e7-a12d57c5a0db
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: abc12a642343e2c9bf259142680bf101cebf3e8b
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75241319"
---
# <a name="register-servers"></a>Registrieren von Servern
  Durch das Registrieren eines Servers in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Sie die Serververbindungsinformationen für zukünftige Verbindungen speichern. Es gibt drei Möglichkeiten, einen Server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zu registrieren.  
  
1.  Lokale Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden beim ersten Start von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] nach der Installation automatisch registriert.  
  
2.  Der automatische Registrierungsprozess kann aber jederzeit gestartet werden, um die Registrierung von lokalen Serverinstanzen wiederherzustellen.  
  
3.  Und letztlich können Sie einen Server mit dem Tool für registrierte Server von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]registrieren.  
  
## <a name="benefits-of-registered-servers"></a>Vorteile von registrierten Servern  
 Die Option "Registrierte Server" bietet folgende Möglichkeiten:  
  
-   Registrieren von Servern zum Beibehalten der Verbindungsinformationen.  
  
-   Ermitteln, ob ein registrierter Server ausgeführt wird.  
  
-   Einfaches Herstellen einer Verbindung zwischen dem Objekt-Explorer und dem Abfrage-Editor mit einem registrierten Server.  
  
-   Bearbeiten oder Löschen der Registrierungsinformationen für einen registrierten Server.  
  
-   Erstellen von Servergruppen.  
  
-   Bereitstellen benutzerfreundlicher Namen für registrierte Server durch Angeben eines Werts im Feld **Name des registrierten Servers** , der von dem in der Liste **Servername** abweicht.  
  
-   Bereitstellen detaillierter Beschreibungen für registrierte Server.  
  
-   Bereitstellen detaillierter Beschreibungen registrierter Servergruppen.  
  
-   Exportieren registrierter Servergruppen.  
  
-   Importieren registrierter Servergruppen.  
  
-   Anzeigen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Protokolldateien für Online- oder Offlineinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="related-tasks"></a>Related Tasks  
 Erste Schritte mit registrierten Servern finden Sie in den folgenden Themen:  
  
|**Beschreibung**|**Thema**|  
|---------------------|---------------|  
|Registrieren lokaler Serverinstanzen|[Registrieren eines verbundenen Servers &#40;SQL Server Management Studio&#41;](register-a-connected-server-sql-server-management-studio.md)|  
|Registrieren eines Servers|[Erstellen Sie einen neuen registrierten Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)|  
|Anzeigen registrierter Server|[Registrierte Server in SQL Server Management Studio anzeigen](view-registered-servers-in-sql-server-management-studio.md)|  
|Entfernen eines registrierten Servers|[&#40;SQL Server Management Studio eines registrierten Servers entfernen&#41;](remove-a-registered-server-sql-server-management-studio.md)|  
|Ändern der Registrierung eines Servers|[Ändern Sie die Registrierungs &#40;eines Servers SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md)|  
|Herstellen einer Verbindung zu einem registrierten Server|[Herstellen einer Verbindung mit einem registrierten Server &#40;SQL Server Management Studio&#41;](connect-to-a-registered-server-sql-server-management-studio.md)|  
|Trennen eines registrierten Servers|[Trennen Sie die Verbindung mit einem registrierten Server &#40;SQL Server Management Studio&#41;](disconnect-from-a-registered-server-sql-server-management-studio.md)|  
|Verschieben eines registrierten Servers bzw. einer registrierte Servergruppe|[Verschieben eines registrierten Servers oder einer registrierten Server Gruppe &#40;SQL Server Management Studio&#41;](move-a-registered-server-or-registered-server-group.md)|  
|Ändern des Namens eines registrierten Servers oder einer Servergruppe|[Ändern Sie den Namen eines registrierten Servers oder einer registrierten Server Gruppe &#40;SQL Server Management Studio&#41;](change-the-name-of-registered-server-or-registered-server-group.md)|  
|Erstellen oder Bearbeiten einer Servergruppe|[Erstellen oder Bearbeiten einer Server Gruppe &#40;SQL Server Management Studio&#41;](create-or-edit-a-server-group-sql-server-management-studio.md)|  
|Entfernen einer Servergruppe|[Entfernen einer Server Gruppe &#40;SQL Server Management Studio&#41;](remove-a-server-group-sql-server-management-studio.md)|  
|Exportieren von Informationen zum registrierten Server|[Informationen zum registrierten Server &#40;SQL Server Management Studio exportieren&#41;](export-registered-server-information-sql-server-management-studio.md)|  
|Importieren von Informationen zum registrierten Server|[Importieren von Informationen zum registrierten Server &#40;SQL Server Management Studio&#41;](import-registered-server-information-sql-server-management-studio.md)|  
|Erstellen eines zentralen Verwaltungsservers und einer Servergruppe|[Erstellen eines zentralen Verwaltungs Servers und einer Server Gruppe &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md)|  
|Gleichzeitiges Ausführen von Anweisungen für mehrere Server|[Gleichzeitiges Ausführen von Anweisungen für mehrere Server &#40;SQL Server Management Studio&#41;](execute-statements-against-multiple-servers-simultaneously.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Remoteserver](../../database-engine/configure-windows/remote-servers.md)  
  
  
