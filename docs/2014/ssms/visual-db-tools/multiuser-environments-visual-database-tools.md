---
title: Mehrbenutzerumgebungen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- users [SQL Server], multiuser environments
- conflict resolution [Visual Database Tools]
- multiple users making database changes
- multiuser environments [Visual Database Tools]
- database modifications [SQL Server]
- version control [Visual Database Tools]
- Visual Database Tools [SQL Server], multiuser environments
ms.assetid: 330bd48c-9427-4967-b58e-b7c492d5ee36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 382aca19452d5cf21a4b1112d872b12afe38782d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63306003"
---
# <a name="multiuser-environments-visual-database-tools"></a>Mehrbenutzerumgebungen (Visual Database Tools)
  In einer Mehrbenutzerumgebung können andere Benutzer eine Verbindung mit der Datenbank herstellen, in der Sie arbeiten, und Änderungen daran vornehmen. Im Ergebnis können mehrere Benutzer ggf. gleichzeitig mit demselben Datenbankobjekt arbeiten. In einer Mehrbenutzerumgebung kann es daher vorkommen, dass sich die Änderungen anderer Benutzer auf die Datenbank auswirken, während Sie selbst gerade Änderungen vornehmen, und umgekehrt.  
  
 Bei der Arbeit mit Datenbanken in einer Mehrbenutzerumgebung stellen die Zugriffsberechtigungen ein zentrales Thema dar. Die Berechtigungen, die Sie in einer Datenbank besitzen, spielen die entscheidende Rolle im Hinblick auf die Aufgaben, die Sie in der Datenbank ausführen können. Zum Ändern von Objekten in einer Datenbank müssen Sie z. B. die erforderlichen Schreibberechtigungen für die Datenbank besitzen. Weitere Informationen über Berechtigungen finden Sie in der Datenbankdokumentation. Weitere Informationen finden Sie unter [Berechtigungen und Visual Database Tools &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
 Wenn Sie die an einer Tabelle vorgenommenen Änderungen speichern, überprüft der Tabellen-Designer, ob die Datenbank seit Ihrem letzten Speichern von Änderungen modifiziert wurde. Falls ein anderer Benutzer die Datenbank geändert hat, werden Sie darüber benachrichtigt. Eventuell müssen Sie diese Änderungen abgleichen. Weitere Informationen finden Sie unter [Abstimmen der Änderungen von mehreren Benutzern &#40;Visual Database Tools&#41;](reconcile-changes-made-by-multiple-users-visual-database-tools.md).  
  
 In einer Mehrbenutzerumgebung sind einige Besonderheiten zu beachten, damit einander widerstreitende Änderungen vermieden werden. Weitere Informationen finden Sie unter [Probleme bei der Datenbankentwicklung &#40;Visual Database Tools&#41;](issues-of-database-evolution-visual-database-tools.md).  
  
 Ein Weg, Probleme zu vermeiden, ist das Arbeiten an einer Kopie der Datenbank, z. B. einer Testdatenbank. Sie können dann ein Änderungsskript erstellen, das Ihre Änderungen enthält und das Sie nach der offline vorgenommenen Klärung auf die Originaldatenbank anwenden. Weitere Informationen finden Sie unter [Entwicklungs-, Test- und Produktionsdatenbanken &#40;Visual Database Tools&#41;](development-test-and-production-databases-visual-database-tools.md).  
  
  
