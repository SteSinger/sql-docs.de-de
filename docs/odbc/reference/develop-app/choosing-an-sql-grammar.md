---
title: Auswählen einer SQL-Grammatik | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], SQL grammar
- SQL grammar [ODBC], selecting
ms.assetid: 4e0d189b-e407-47e0-92a9-f9982230dd0e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6f7bf7e77f892f10de17402b59e732523d58fbc6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036549"
---
# <a name="choosing-an-sql-grammar"></a>Auswählen einer SQL-Grammatik
Die erste Entscheidung bei der Erstellung der SQL-Anweisungen ist die Grammatik zu verwenden. Zusätzlich zu der Grammatiken für verschiedene Standardorganisationen, z. B. Open Group, ANSI und ISO-Images definiert praktisch jeden DBMS-Hersteller eine eigene Grammatik, von denen jede geringfügig von der Standard variiert.  
  
 [Anhang C: SQL-Grammatik](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), beschreibt die minimale SQL-Grammatik, die alle ODBC-Treiber unterstützen muss. Diese Grammatik ist eine Teilmenge der Ebene der SQL-92-Eintrag. Treiber unterstützen möglicherweise weitere Grammatik entspricht, den Zwischenspeicher voll oder FIPS 127-2-Transitional Ebenen definiert von SQL-92. Weitere Informationen finden Sie unter [mindestens SQL-Grammatik](../../../odbc/reference/appendixes/sql-minimum-grammar.md) in Anhang C: SQL-Grammatik und SQL-92.  
  
 Anhang C definiert auch *escape-Zeichensequenzen* mit standard-Grammatik für gängiger Sprachfeatures, z. B. outer Join, unterliegen nicht der SQL-92-Grammatik. Weitere Informationen finden Sie unter [ODBC-Escapesequenzen](../../../odbc/reference/appendixes/odbc-escape-sequences.md) in Anhang C: SQL-Grammatik und [Escapesequenzen](../../../odbc/reference/develop-app/escape-sequences.md)weiter unten in diesem Abschnitt.  
  
 Die Grammatik, die ausgewählt wird, wirkt sich auf, wie der Treiber die Anweisung verarbeitet. Treiber müssen die SQL-92-SQL und der ODBC-definierten Escapesequenzen für DBMS-spezifische SQL ändern. Da die meisten SQL-Grammatik, die sich auf einem oder mehreren der verschiedenen Standards basieren, werden die meisten Treiber nur wenig oder keine Arbeit, um diese Anforderung zu erfüllen. Es häufig besteht nur aus der Suche nach der Escape-Sequenzen, die definiert von ODBC und Ersetzen sie mit speziellen DBMS-Grammatik. Wenn ein Treiber Grammatik, die er nicht erkennt trifft, wird die Grammatik DBMS-spezifische und übergibt die SQL-Anweisung ohne Änderungen an die Datenquelle für die Ausführung.  
  
 Aus diesem Grund Es gibt zwei Möglichkeiten der Grammatik verwendet: die SQL-92-Grammatik (und den ODBC-Escapesequenzen) und ein DBMS-spezifische-Grammatik. Nur die SQL-92-Grammatik ist von diesen beiden interoperabel, damit alle interoperable Anwendungen verwendet werden soll. Anwendungen, die nicht vollständig kompatibel sind, können die SQL-92-Grammatik oder eine Grammatik für DBMS-spezifische verwenden. DBMS-spezifische Grammatiken haben zwei Vorteile: Sie können alle Features, die nicht von SQL-92 abgedeckt ausnutzen, und sie sind geringfügig schneller, da der Treiber nicht verfügt, sie zu ändern. Die zweite Funktion kann teilweise erzwungen werden, durch Festlegen des Attributs der SQL_ATTR_NOSCAN-Anweisung, die den Treiber von Suchen und ersetzen die Escape-Sequenzen beendet wird.  
  
 Wenn die SQL-92-Grammatik verwendet wird, die Anwendung erkennen, wie er durch den Aufruf vom Treiber geändert wird **SQLNativeSql**. Dies ist häufig nützlich, beim Debuggen von Anwendungen. **SQLNativeSql** akzeptiert eine SQL-Anweisung und gibt sie zurück, nachdem der Treiber verändert wurde. Da diese Funktion in der Konformitätsgrad des Core-Schnittstelle ist, wird es von allen Treibern unterstützt.
