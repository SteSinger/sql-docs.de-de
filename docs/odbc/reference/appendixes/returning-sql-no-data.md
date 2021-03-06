---
title: Rückgabe von SQL_NO_DATA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2613593d9c2e20d5dfa01c0a0b4f9886dbc8e889
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057131"
---
# <a name="returning-sqlnodata"></a>Rückgabe von SQL_NO_DATA
Wenn eine ODBC *2.x* Anwendung arbeiten, eine ODBC- *3.x* Treiber ruft **SQLExecDirect**, **SQLExecute**, oder  **SQLParamData**, und ein gesuchtes Update oder Delete-Anweisung wurde ausgeführt, aber keine Auswirkungen auf die Zeilen in der Datenquelle, die ODBC *3.x* Treiber sollte SQL_SUCCESS zurück. Wenn eine ODBC *3.x* arbeiten mit einer ODBC-Anwendung *3.x* Treiber ruft **SQLExecDirect**, **SQLExecute**, oder  **SQLParamData** dasselbe Ergebnis erzielt, die ODBC *3.x* Treiber sollte SQL_NO_DATA zurückgegeben werden.  
  
 Wenn eine gesuchte update oder-Anweisung in DELETE ein Batch von Anweisungen hat keine Auswirkungen auf alle Zeilen in der Datenquelle **SQLMoreResults** gibt SQL_SUCCESS zurück. Es kann keine SQL_NO_DATA, zurückgeben, da dieser Wert bedeuten würde, dass es sind keine weiteren Ergebnisse, nicht, die es ein Ergebnis aus einer komplexen aktualisieren/löschen, die keine Zeilen betroffen.
