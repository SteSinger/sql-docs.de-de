---
title: Generieren von NULL-Werten mithilfe des XSINIL-Parameters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d056959f5e05d3de79fa81d33331390f4decb49a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63205603"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Generieren von NULL-Werten mithilfe des XSINIL-Parameters
  Von der **ELEMENTS** -Direktive wird XML konstruiert, in der jede Spalte zu einem Element im XML-Code zugeordnet wird. Wenn der Spaltenwert NULL ist, wird kein Element hinzugefügt. Durch Angeben des optionalen Parameters **XSINIL** für die ELEMENTS-Direktive können Sie anfordern, dass auch für den NULL-Wert ein Element erstellt wird. In diesem Fall wird für ein Element das **xsi:nil** -Attribut, das auf TRUE festgelegt ist, für jeden NULL-Spaltenwert zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)  
  
  
