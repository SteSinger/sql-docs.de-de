---
title: Sequenzcontainer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sequencecontainer.f1
helpviewer_keywords:
- Sequence container
- grouping control flows
- containers [Integration Services], Sequence
- subset control flow [Integration Services]
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6255a348383804bb2bb37ae88b5d91dbc6db3eca
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71293938"
---
# <a name="sequence-container"></a>Sequenzcontainer

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Der Sequenzcontainer definiert eine Ablaufsteuerung, die eine Teilmenge der Paketablaufsteuerung ist. Sequenzcontainer gruppieren das Paket zu mehreren separaten Ablaufsteuerungen, die jeweils Tasks und Container enthalten, die innerhalb der allgemeinen Paketablaufsteuerung ausgeführt werden.  
  
 Der Sequenzcontainer kann neben anderen Containern Tasks einschließen. Das Hinzufügen von Tasks und Containern zu einem Sequenzcontainer ist mit dem Hinzufügen von Tasks und Containern zu einem Paket vergleichbar, außer dass Sie die Tasks und Container nicht in den Paketcontainer, sondern in den Sequenzcontainer ziehen. Falls der Sequenzcontainer mehrere Tasks oder Container einschließt, können Sie diese wie bei einem Paket mithilfe von Rangfolgeneinschränkungen verbinden. Weitere Informationen finden Sie unter [Precedence Constraints](../../integration-services/control-flow/precedence-constraints.md).  
  
 Die Verwendung eines Sequenzcontainers bietet viele Vorteile:  
  
-   Deaktivieren von Taskgruppen, um das Debuggen des Pakets auf eine Teilmenge der Paketablaufsteuerung zu konzentrieren.  
  
-   Zentrales Verwalten von Eigenschaften in mehreren Tasks, indem Eigenschaften für einen Sequenzcontainer und nicht für die einzelnen Tasks festgelegt werden.  
  
     Beispielsweise können Sie die **Disable** -Eigenschaft des Sequenzcontainers auf **True** festlegen, um alle Tasks und Container im Sequenzcontainer zu deaktivieren.  
  
-   Bereitstellen des Bereichs für Variablen, die eine Gruppe verwandter Tasks und Container verwendet.  
  
-   Gruppieren vieler Tasks, damit Sie sie durch Erweitern oder Reduzieren des Sequenzcontainers leichter verwalten können.  
  
     Darüber hinaus können Sie Taskgruppen erstellen, die mithilfe des Felds **Gruppe** erweitert und reduziert werden. Das Feld **Gruppe** ist jedoch eine Entwurfszeitfunktion ohne Eigenschaften und ohne Laufzeitverhalten. Weitere Informationen finden Sie unter [Gruppieren von Komponenten oder Aufheben der Gruppierung](../../integration-services/group-or-ungroup-components.md).  
  
-   Legen Sie ein Transaktionsattribut für den Sequenzcontainer fest, um eine Transaktion für eine Teilmenge der Paketablaufsteuerung zu definieren. Auf diese Weise können Sie Transaktionen mit feinerer Granularität verwalten.  
  
     Wenn z. B. ein Sequenzcontainer zwei verwandte Tasks enthält (einen Task, der Daten in einer Tabelle löscht, und einen anderen Task, der Daten in eine Tabelle einfügt), können Sie eine Transaktion konfigurieren, um sicherzustellen, dass für den Löschvorgang ein Rollback ausgeführt wird, falls beim Einfügen ein Fehler auftritt. Weitere Informationen finden Sie unter [Integration Services-Transaktionen](../../integration-services/integration-services-transactions.md).  
  
## <a name="configuration-of-the-sequence-container"></a>Konfiguration des Sequenzcontainers  
 Der Sequenzcontainer weist keine benutzerdefinierte Benutzeroberfläche auf und kann nur im Fenster **Eigenschaften** von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder programmgesteuert konfiguriert werden.  
  
 Informationen zum programmgesteuerten Festlegen dieser Eigenschaften finden Sie in der Dokumentation zur **T:Microsoft.SqlServer.Dts.Runtime.Sequence** -Klasse im Entwicklerhandbuch.  
  
## <a name="related-tasks"></a>Related Tasks  
 Weitere Informationen zum Festlegen der Eigenschaften der Komponente in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]finden Sie unter [Festlegen der Eigenschaften eines Tasks oder Containers](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung](../../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Verbinden von Tasks und Containern mithilfe einer Standardrangfolgeneinschränkung](https://msdn.microsoft.com/library/8f31f15f-98ff-4c35-b41f-8b8cfd148d75)   
 [SQL Server Integration Services-Container](../../integration-services/control-flow/integration-services-containers.md)  
  
  
