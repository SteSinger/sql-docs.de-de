---
title: Escapesequenz Skalarfunktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36e108fcc61b2390d5fd72ac4ad322778ccfb4b2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057073"
---
# <a name="scalar-function-escape-sequence"></a>Skalarfunktion-Escapesequenz
ODBC verwendet Escapesequenzen für Skalarfunktionen. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Hinweise  
 In BNF-Schreibweise lautet die Syntax:  
  
 *ODBC-Skalar-Funktion-Escapesequenz* :: =  
  
 *Initiator der ODBC-esc* fn *-Skalarfunktion ODBC-esc-Terminator*  
  
 *-Skalarfunktion* :: = *Funktionsname-* (*Argumentliste*)  
  
 (Die Definitionen für die Nichtterminale *Funktionsname-* und *Funktionsname-* (*Argumentliste*) abgeleitet werden, aus der Liste von Skalarfunktionen in [ Anhang E: Skalare Funktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *Initiator der ODBC-esc* :: = {  
  
 *ODBC-esc-Terminator* :: =}  
  
 Um zu bestimmen, ob die Datenquelle, Verfahren unterstützt und der Treiber die Aufrufsyntax des ODBC-Prozedur unterstützt, eine Anwendung aufrufen kann **SQLGetInfo**. Weitere Informationen finden Sie unter [Anhang E: Skalare Funktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
