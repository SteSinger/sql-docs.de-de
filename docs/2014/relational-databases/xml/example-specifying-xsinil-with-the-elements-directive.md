---
title: 'Beispiel: Angeben von XSINIL mit der ELEMENTS-Direktive | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying XSINIL example
ms.assetid: 07c873ff-1f9d-480e-8536-862c39eb8249
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34cc4479a26d633e689963a945095248f683993f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63287275"
---
# <a name="example-specifying-xsinil-with-the-elements-directive"></a>Beispiel: Angeben von XSINIL mit der ELEMENTS-Direktive
  In der folgenden Abfrage wird die `ELEMENTS` -Direktive angegeben, um elementzentrierte XML-Daten aus dem Abfrageergebnis zu generieren.  
  
## <a name="example"></a>Beispiel  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 Dies ist das Teilergebnis.  
  
```  
<row>  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
 Da die `Color`-Spalte NULL-Werte für einige Produkte aufweist, generieren die resultierenden XML-Daten nicht das entsprechende <`Color`>-Element. Indem die `XSINIL`-Direktive zusammen mit `ELEMENTS` hinzugefügt wird, können Sie das <`Color`>-Element auch für NULL-Farbwerte im Resultset generieren.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS XSINIL ;  
```  
  
 Dies ist das Teilergebnis:  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
  <Color xsi:nil="true" />  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)  
  
  
