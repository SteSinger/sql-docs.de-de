---
title: Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c0b0b8236187698917dddd3ca98830add6c3fde9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63245666"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools
  In diesem Thema wird beschrieben, wie WMI konfiguriert wird, um den Serverstatus in SQL Server-Tools in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] anzuzeigen. Bei der Verbindungsherstellung mit Servern wird von den Komponenten Registrierte Server und Objekt-Explorer von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]sowie auch vom [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager Windows Management Instrumentation (WMI) zum Abrufen des Status der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Dienste (MSSQLSERVER) und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent-Dienste (MSSQLSERVER) verwendet. Zum Anzeigen des Dienststatus muss der Benutzer über Remotezugriffsrechte für das WMI-Objekt verfügen. Zum Konfigurieren dieser Berechtigung muss auf dem Server WMI installiert sein.  
  
##  <a name="SSMSProcedure"></a> So konfigurieren Sie die WMI-Berechtigungen  
  
1.  Klicken Sie auf dem Remoteserver im Menü **Start** auf **Ausführen**.  
  
2.  In der **öffnen** geben `wmimgmt.msc`, und klicken Sie dann auf **OK**.  
  
3.  Klicken Sie im Programm **Windows-Verwaltungsinfrastruktur** mit der rechten Maustaste auf **WMI-Steuerung (Lokal)** , und klicken Sie dann auf **Eigenschaften**.  
  
4.  Erweitern Sie im Dialogfeld **Eigenschaften von WMI-Steuerung (Lokal)** auf der Registerkarte **Sicherheit** den Eintrag **Root**, und klicken Sie dann auf **CIMV2**.  
  
5.  Klicken Sie auf **Sicherheit** , um das Dialogfeld **Sicherheit für ROOT\CIMV2** zu öffnen.  
  
6.  Fügen Sie zum Feld **Gruppen- oder Benutzernamen** eine Gruppe oder einen Benutzer hinzu, und markieren Sie die Gruppe bzw. den Benutzer.  
  
7.  In der **Berechtigungen für** _\<Gruppen- oder Benutzername >_ wählen Sie im der **zulassen** Spalte, für die **Remoteaktivierung** Berechtigung , für Benutzer, die Sie Remote möchten der Dienststatus erkannt.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Dienstes](agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
