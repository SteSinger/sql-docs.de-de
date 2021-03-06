---
title: Globale Einstellungen (Dialogfelder) (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 6df20fbb-e92d-475f-a94d-aaf70b06eb9b
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 702f7b5ec8ea1fc5eeea7ce95fae84bdcb17418a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075430"
---
# <a name="global-settings-dialogs-mysqltosql"></a>Globale Einstellungen (Dialogfelder) (MySQLToSQL))
Mithilfe der Dialogfelder-Seite des der **globale Einstellungen** Dialogfeld zum Angeben der Standardaktion für Benutzer und die Einstellungen für die Warnung für SSMA.  
  
Um die Einstellungen des Dialogfelds auf die **Tools** , wählen Sie im Menü **globale Einstellungen**, klicken Sie auf **GUI** am unteren Rand der linken Seite, und wählen Sie dann **-Dialogfelder**.  
  
## <a name="options"></a>Optionen  
**Warnung vor dem Überschreiben von Objekten**  
Wenn SSMA Objekte in SQL Server konvertiert, möglicherweise einige Objekte in SQL Server-Metadaten des Projekts bereits vorhanden. Diese Objekte möglicherweise bereits konvertiert wurden, oder die Objekte möglicherweise einfach denselben Namen in das Zielschema als Objekte, die Sie konvertieren möchten.  
  
Verwenden Sie diese Option, um anzugeben, ob SSMA Sie auffordert, für das Überschreiben von doppelten Objektdefinitionen:  
  
-   Bei Auswahl von **"true"** , SSMA wird ein Warnungsdialogfeld angezeigt, wenn es sich um ein doppeltes Objekt trifft. In diesem Dialogfeld können Sie einzelne Objekte oder alle doppelten Objekte überschrieben, oder überspringen Sie einzelne Objekte oder alle doppelten Objekte angeben.  
  
-   Bei Auswahl von **"false"** , **Objekt überschreiben Standardaktion** Option wird angezeigt, in dem Sie die Standardaktion anzugeben.  
  
**Standardaktion des Objekts überschreiben**  
Diese Option wird angezeigt, wenn Sie die Option **"false"** für die **Warnung vor dem Überschreiben von Objekten** Option.  
  
Verwenden Sie diese Option, um anzugeben, das Standardobjekt Verhalten überschreiben:  
  
-   Bei Auswahl von **"true"** , SSMA werden Objekte in den Metadaten der SQL Server-Projekt, die den gleichen Namen aufweisen und das gleiche Ziel-Schema-Objekts, das konvertiert werden, automatisch überschrieben.  
  
-   Bei Auswahl von **"false"** , SSMA Metadaten des Objekts während der Konvertierung nicht überschrieben.  
  
