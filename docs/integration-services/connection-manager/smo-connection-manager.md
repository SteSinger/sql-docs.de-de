---
title: SMO-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.smoconnection.f1
helpviewer_keywords:
- connections [Integration Services], SMO
- SMO connection manager
- connection managers [Integration Services], SMO
ms.assetid: d273f1fb-a6a8-4f2f-a5ff-55c2e3de4723
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 87400e2216b51bfab0132f369e452f27447b0572
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294399"
---
# <a name="smo-connection-manager"></a>SMO-Verbindungs-Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Mit einem SMO-Verbindungs-Manager kann ein Paket eine Verbindung mit einem SMO-Server (SQL Management Object) herstellen. Die Übertragungstasks von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwenden einen SMO-Verbindungs-Manager. Beispielsweise verwendet der Task Anmeldungen übertragen, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldungen überträgt, einen SMO-Verbindungs-Manager.  
  
 Wenn Sie einem Paket einen SMO-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine SMO-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der **Connections** -Sammlung im Paket den Verbindungs-Manager hinzufügt. Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **SMOServer**festgelegt.  
  
 Es gibt folgende Möglichkeiten, um einen SMO-Verbindungs-Manager zu konfigurieren:  
  
-   Geben Sie den Namen eines Servers an, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert ist.  
  
-   Wählen Sie den Authentifizierungsmodus zum Herstellen einer Verbindung mit dem Server aus.  
  
## <a name="configuration-of-the-smo-connection-manager"></a>Konfiguration des SMO-Verbindungs-Managers  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [SMO-Verbindungs-Manager-Editor](../../integration-services/connection-manager/smo-connection-manager-editor.md).  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="smo-connection-manager-editor"></a>SMO-Verbindungs-Manager-Editor
  Verwenden Sie den **Editor für den SMO-Verbindungs-Manager** , um eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindung zu konfigurieren, die von verschiedenen Tasks zur Übermittlung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objekten verwendet werden kann.  
  
 Weitere Informationen zum SMO-Verbindungs-Manager finden Sie unter [SMO Connection Manager](../../integration-services/connection-manager/smo-connection-manager.md).  
  
### <a name="options"></a>enthalten  
 **Servername**  
 Geben Sie den Namen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz ein, oder wählen Sie den Servernamen aus der Liste aus.  
  
 **Aktualisieren**  
 Aktualisiert die Liste verfügbarer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen, die im Netzwerk erkannt werden können.  
  
 **Windows-Authentifizierung verwenden**  
 Verwendet die Windows-Authentifizierung, um eine Verbindung mit der ausgewählten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz herzustellen.  
  
 **SQL Server-Authentifizierung verwenden**  
 Verwendet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung, um eine Verbindung mit der ausgewählten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz herzustellen.  
  
 **User name**  
 Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung ausgewählt haben, geben Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzernamen ein.  
  
 **Kennwort**  
 Wenn Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung ausgewählt haben, geben Sie dass Kennwort ein.  
  
 **Verbindung testen**  
 Testet die Verbindung entsprechend der Konfiguration.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Verbindungen &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
