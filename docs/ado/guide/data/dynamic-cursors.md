---
title: Dynamische Cursor | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], dynamic
- dynamic cursors [ADO]
ms.assetid: 00460f30-8cf7-494e-82df-41012f40ae51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86e51b7880004117e8efc96bd310c6de705d43a6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925506"
---
# <a name="dynamic-cursors"></a>Dynamische Cursor
Dynamische Cursor erkennen alle Änderungen, die auf die Zeilen im Resultset, unabhängig davon, ob die Änderungen aus, in den Cursor oder von anderen Benutzern außerhalb des Cursors auftreten. Alle INSERT-, Update- und Delete-Anweisungen, die von allen Benutzern werden über den Cursor sichtbar. Der dynamische-Cursor kann Änderungen, die Zeilen, die Reihenfolge und die Werte im Resultset nach dem Öffnen des Cursors erkennen. Updates, die außerhalb des Cursors sind nicht sichtbar, bis sie ein Commit ausgeführt werden (es sei denn, die die Transaktionsisolationsstufe des Cursors "Commit" auf festgelegt ist).  
  
 Nehmen wir beispielsweise an ein dynamischer Cursor ruft zwei Zeilen und einer anderen Anwendung, und klicken Sie dann eine der Zeilen aktualisiert und löscht die andere. Wenn der dynamische Cursor diese Zeilen dann abruft, findet er die gelöschte Zeile nicht, die neuen Werte der aktualisierten Zeile werden jedoch angezeigt.  
  
 Der dynamische Cursor ist eine gute Wahl, wenn Ihre Anwendung alle gleichzeitige Updates, die von anderen Benutzern vorgenommene erkannt werden muss. Verwenden Sie die **AdOpenDynamic CursorTypeEnum** , um anzugeben, dass Sie einen dynamischen Cursor in ADO verwenden möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorwärtscursor](../../../ado/guide/data/forward-only-cursors.md)   
 [Statische Cursor](../../../ado/guide/data/static-cursors.md)   
 [KEYSET-Cursor](../../../ado/guide/data/keyset-cursors.md)
