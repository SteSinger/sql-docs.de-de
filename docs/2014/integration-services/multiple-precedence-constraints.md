---
title: Mehrere Rangfolgeneinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c0b75b96f30d2fe7f104e8f59aa03d7de6202e6a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66057413"
---
# <a name="multiple-precedence-constraints"></a>Mehrere Rangfolgeneinschränkungen
  Eine Rangfolgeneinschränkung verbindet zwei ausführbare Dateien: zwei Tasks, zwei Container oder einen Task und einen Container. Sie werden als ausführbare Datei der Rangfolge und als eingeschränkte ausführbare Datei bezeichnet. Eine eingeschränkte ausführbare Datei kann mehrere Rangfolgeneinschränkungen haben. Weitere Informationen finden Sie unter [Precedence Constraints](control-flow/precedence-constraints.md).  
  
 Wenn Sie komplexe Einschränkungsszenarien durch Gruppieren von Einschränkungen zusammenfassen, können Sie eine komplexe Ablaufsteuerung in Paketen implementieren. Beispielsweise ist in der folgenden Abbildung der Task D mit dem Task A durch eine `Success`-Einschränkung verlinkt, der Task D ist mit dem Task B durch eine `Failure`-Einschränkung verlinkt, und der Task D ist mit dem Task C durch eine `Success`-Einschränkung verlinkt. Die Rangfolgeneinschränkungen zwischen Task D und Task A, zwischen Task D und Task B sowie zwischen Task D und Task C nehmen an einer logischen *AND* -Beziehung teil. Damit Task D ausgeführt wird, muss Task A erfolgreich ausgeführt werden, bei Task B muss ein Fehler auftreten, und Task C muss erfolgreich ausgeführt werden.  
  
 ![Durch Rangfolgeneinschränkungen verknüpfte Tasks](media/precedenceconstraints.gif "Durch Rangfolgeneinschränkungen verknüpfte Tasks")  
  
## <a name="logicaland-property"></a>LogicalAnd-Eigenschaft  
 Falls ein Task oder ein Container mehrere Einschränkungen aufweist, gibt die `LogicalAnd`-Eigenschaft an, ob eine Rangfolgeneinschränkung einzeln oder zusammen mit anderen Einschränkungen ausgewertet wird.  
  
 Sie können festlegen, die `LogicalAnd` Eigenschaft mit der **Rangfolgeneinschränkungs-Editor** in [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer oder im Fenster Eigenschaften, die [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] bietet.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Festlegen der Eigenschaften von Rangfolgeneinschränkungen](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
