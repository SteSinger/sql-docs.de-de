---
title: MTd (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e604f66e48c8c8bb93ff5fd4abb174449f0fcdd9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088443"
---
# <a name="mtd-mdx"></a>Mtd (MDX)


  Gibt eine Menge von gleichgeordneten Elementen zurück, die derselben Ebene angehören wie ein angegebenes Element. Die Menge beginnt mit dem ersten gleichgeordneten Element und endet mit dem angegebenen Element, entsprechend der Einschränkung durch die Year-Ebene in der Time-Dimension.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Mtd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Elementausdruck nicht angegeben ist, wird der Standardwert ist das aktuelle Element der ersten Hierarchie mit einer Ebene des Typs *Monate* in der ersten Dimension des Typs *Zeit* in der Measuregruppe.  
  
 Die **Mtd** -Funktion ist eine Verknüpfungsfunktion für die [PeriodsToDate](../mdx/periodstodate-mdx.md) funktionieren, wenn die Typeigenschaft der Attributhierarchie, die eine Ebene auf dem basiert, um festgelegt ist *Monate*. Somit ist `Mtd(Member_Expression)` äquivalent zu `PeriodsToDate(Month_Level_Expression,Member_Expression)`.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Summe der Monat bis Datum Frachtkosten für Internetverkäufe für den Monat Juli 2002 bis einschließlich 20. Juli zurückgegeben.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Summe &#40;MDX&#41;](../mdx/sum-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
