---
title: Erweitern von Paketen mit benutzerdefinierten Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 07454f4b273e6a0fab698574bb5d66cdd8adc7af
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71287231"
---
# <a name="extending-packages-with-custom-objects"></a>Erweitern von Paketen mit benutzerdefinierten Objekten

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Wenn die in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bereitgestellten Komponenten nicht Ihren Anforderungen entsprechen, können Sie die Effektivität von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] durch Codieren eigener Erweiterungen erhöhen. Ihnen stehen zwei unterschiedliche Optionen zur Erweiterung der Pakete zur Verfügung: Sie können Code in die leistungsstarken Wrapper schreiben, die vom Skripttask und der Skriptkomponente bereitgestellt werden, oder benutzerdefinierte [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Erweiterungen durch Ableitung von den Basisklassen, die im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objektmodell zur Verfügung stehen, vollständig neu erstellen.  
  
 In diesem Abschnitt wird die erweiterte der beiden Optionen beschrieben: das Erweitern von Paketen mit benutzerdefinierten Objekten.  
  
 Wenn die benutzerdefinierte [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Lösung mehr Flexibilität als das Skripttask und die Skriptkomponente erfordert, oder wenn Sie eine Komponente benötigen, die in mehreren Paketen wieder verwendet wird, dann ermöglicht Ihnen das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objektmodell, benutzerdefinierte Tasks, Datenflusskomponenten und andere Paketobjekte zu erstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwickeln benutzerdefinierter Objekte für Integration Services](../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 Erläutert die benutzerdefinierten Objekte, die für [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erstellt werden können, und fasst die wesentlichen Schritte und Einstellungen zusammen.  
  
 [Beibehalten von benutzerdefinierten Objekten](../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 Erläutert die Standardpersistenz benutzerdefinierter Objekte sowie den Prozess der Implementierung von benutzerdefinierter Persistenz.  
  
 [Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 Erläutert die gebräuchlichen Verfahren des Erstellens, Bereitstellens und Testens der verschiedenen Typen benutzerdefinierter Objekte.  
  
 [Entwickeln eines benutzerdefinierten Tasks](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 Beschreibt den Prozess des Codierens eines benutzerdefinierten Tasks.  
  
 [Entwickeln eines benutzerdefinierten Verbindungs-Managers](../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 Beschreibt den Prozess des Codierens eines benutzerdefinierten Verbindungs-Managers.  
  
 [Entwickeln eines benutzerdefinierten Protokollanbieters](../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 Beschreibt den Prozess des Codierens eines benutzerdefinierten Protokollanbieters.  
  
 [Entwickeln eines benutzerdefinierten ForEach-Enumerators](../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Beschreibt den Prozess des Codierens eines benutzerdefinierten Enumerators.  
  
 [Entwickeln einer benutzerdefinierten Datenflusskomponente](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 Erläutert die Programmierung benutzerdefinierter Datenflussquellen, Transformationen und Ziele.  
  
## <a name="reference"></a>Verweis  
 [Fehler- und Meldungsreferenz von Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
 Listet die vordefinierten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Fehlercodes mit ihren symbolischen Namen und Beschreibungen auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erweitern von Paketen mit Skripts](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
 Beschreibt, wie die Ablaufsteuerung mithilfe des Skripttasks bzw. der Datenfluss mithilfe der Skriptkomponente erweitert werden können.  
  
 [Programmgesteuertes Erstellen von Paketen](../../integration-services/building-packages-programmatically/building-packages-programmatically.md)  
 Erläutert, wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete programmgesteuert erstellt, konfiguriert, ausgeführt, geladen, gespeichert und verwaltet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichen von Skriptlösungen und benutzerdefinierten Objekten](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  
