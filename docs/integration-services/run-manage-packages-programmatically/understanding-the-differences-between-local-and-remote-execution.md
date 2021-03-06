---
title: Grundlegendes zu den Unterschieden zwischen der lokalen und der Remoteausführung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9280f92233909077afd0507c5c2de7b93467ccb1
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71282057"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>Grundlegendes zu den Unterschieden zwischen der lokalen und der Remoteausführung

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Paketentwickler und Administratoren sollten die Beschränkungen hinsichtlich des Ausführungsorts eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakets beachten.  
  
-   **Ein Paket wird auf dem gleichen Computer ausgeführt wie das Programm, das es startet**. Auch wenn ein Progamm ein Paket lädt, das auf einem anderen Server remote gespeichert ist, wird das Paket auf dem lokalen Computer ausgeführt.  
  
-   **Sie können ein Paket außerhalb der Entwicklungsumgebung nur auf Computern ausführen, auf denen Integration Services installiert ist**. Sie können Pakete außerhalb von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nur auf Clientcomputern ausführen, auf denen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installiert ist, wobei die Bedingungen Ihrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Lizenz möglicherweise die Installation von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] auf weiteren Computern nicht zulassen. Bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] handelt es sich um eine Serverkomponente, die nicht an Clientcomputer weitergegeben werden darf. Um Pakete von einem Clientcomputer aus auszuführen, müssen Sie diese so starten, dass die Ausführung auf dem Server sichergestellt ist.  
  
 Weitere Informationen zum Laden und Ausführen eines gespeicherten Pakets finden Sie unter:  
  
-   [Programmgesteuertes Laden und Ausführen eines lokalen Pakets](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [Programmgesteuertes Laden und Ausführen eines Remotepakets](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 Weitere Informationen zum Ausführen eines Pakets und Laden von dessen Ausgabe in ein benutzerdefiniertes Programm finden Sie unter:  
  
-   [Laden der Ausgabe eines lokalen Pakets](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuertes Laden und Ausführen eines lokalen Pakets](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Programmgesteuertes Laden und Ausführen eines Remotepakets](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Laden der Ausgabe eines lokalen Pakets](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
