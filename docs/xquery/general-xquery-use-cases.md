---
title: General XQuery-Anwendungsfälle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, general usage cases
ms.assetid: 5187c97b-6866-474d-8bdb-a082634039cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e844425f0c512cfe7c15354bf1aeb100d6104e2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004521"
---
# <a name="general-xquery-use-cases"></a>Allgemeine Einsatzgebiete für XQuery
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Dieses Thema stellt allgemeine Beispiele für die Verwendung von XQuery zur Verfügung.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-query-catalog-descriptions-to-find-products-and-weights"></a>A. Abfragen von Produkten und Gewichten in Katalogbeschreibungen  
 Die folgende Abfrage gibt die Produktmodell-IDs und (sofern vorhanden) die Gewichtungen aus der Produktkatalogbeschreibung zurück. Die Abfrage erstellt XML in der folgenden Form:  
  
```  
<Product ProductModelID="...">  
  <Weight>...</Weight>  
</Product>  
```  
  
 Im Folgenden wird die Abfrage aufgeführt:  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  <Product  ProductModelID="{ (/p1:ProductDescription/@ProductModelID)[1] }">  
     {   
       /p1:ProductDescription/p1:Specifications/Weight   
     }   
  </Product>  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not null  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die **Namespace** -Schlüsselwort im XQuery-Prolog definiert ein Namespacepräfix, das verwendet wird, im Hauptteil Abfrage.  
  
-   Der Body-Teil der Abfrage bewirkt die Konstruktion des erforderlichen XML-Codes.  
  
-   In der WHERE-Klausel der **exist()** Methode wird verwendet, um nur Zeilen zu suchen, die produktkatalogbeschreibungen enthalten. D. h. der XML-Code, der enthält der <`ProductDescription`> Element.  
  
 Dies ist das Ergebnis:  
  
```  
<Product ProductModelID="19"/>  
<Product ProductModelID="23"/>   
<Product ProductModelID="25"/>   
<Product ProductModelID="28"><Weight>Varies with size.</Weight></Product>  
<Product ProductModelID="34"/>  
<Product ProductModelID="35"/>  
```  
  
 Die folgende Abfrage ruft die gleiche Informationen, aber nur für die Produktmodelle, deren katalogbeschreibung das Gewicht, enthält der <`Weight`>-Element in den Spezifikationen, die <`Specifications`> Element. In diesem Beispiel wird WITH XLMNAMESPACES zum Deklarieren des pd-Präfixes und seiner Namespacebindung verwendet. Auf diese Weise wird die Bindung nicht in beiden beschrieben die **query()** Methode und die **exist()** Methode.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT CatalogDescription.query('  
          <Product  ProductModelID="{ (/pd:ProductDescription/@ProductModelID)[1] }">  
                 {   
                      /pd:ProductDescription/pd:Specifications/Weight   
                 }   
          </Product>  
') as x  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/pd:ProductDescription/pd:Specifications//Weight ') = 1  
```  
  
 In der vorherigen Abfrage die **exist()** -Methode der der **Xml** -Datentyp in die WHERE-Klausel überprüft, um festzustellen, ob eine <`Weight`>-Element in der <`Specifications`> Element.  
  
### <a name="b-find-product-model-ids-for-product-models-whose-catalog-descriptions-include-front-angle-and-small-size-pictures"></a>B. Suchen von Produktmodell-IDs für Produktmodelle, deren Katalogbeschreibungen Bilder mit frontalem Blickwinkel und geringer Größe enthalten  
 Der XML der produktkatalogbeschreibung enthält produktabbildungen, die <`Picture`> Element. Jedes Bild besitzt mehrere Eigenschaften. Dazu gehören der bildwinkel, das <`Angle`>-Element, und die Größe der <`Size`> Element.  
  
 Für Produktmodelle, deren Katalogbeschreibungen Bilder mit frontalem Blickwinkel und geringer Größe enthalten, konstruiert die Abfrage XML-Code, der die folgende Form aufweist:  
  
```  
< Product ProductModelID="...">  
  <Picture>  
    <Angle>front</Angle>  
    <Size>small</Size>  
  </Picture>  
</Product>  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT CatalogDescription.query('  
   <pd:Product  ProductModelID="{ (/pd:ProductDescription/@ProductModelID)[1] }">  
      <Picture>  
         {  /pd:ProductDescription/pd:Picture/pd:Angle }   
         {  /pd:ProductDescription/pd:Picture/pd:Size }   
      </Picture>  
   </pd:Product>  
') as Result  
FROM  Production.ProductModel  
WHERE CatalogDescription.exist('/pd:ProductDescription/pd:Picture') = 1  
AND   CatalogDescription.value('(/pd:ProductDescription/pd:Picture/pd:Angle)[1]', 'varchar(20)')  = 'front'  
AND   CatalogDescription.value('(/pd:ProductDescription/pd:Picture/pd:Size)[1]', 'varchar(20)')  = 'small'  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   In der WHERE-Klausel der **exist()** Methode wird verwendet, um nur die Zeilen abgerufen, die produktkatalogbeschreibungen mit der <`Picture`> Element.  
  
-   Der WHERE-Klausel der **Value()-Methode** Methode zwei Mal Vergleich der Werte von der <`Size`> und <`Angle`> Elemente.  
  
 Dies ist ein Teilergebnis gezeigt:  
  
```  
<p1:Product   
  xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
  ProductModelID="19">  
  <Picture>  
    <p1:Angle>front</p1:Angle>  
    <p1:Size>small</p1:Size>  
  </Picture>  
</p1:Product>  
...  
```  
  
### <a name="c-create-a-flat-list-of-the-product-model-name-and-feature-pairs-with-each-pair-enclosed-in-the-features-element"></a>C. Erstellen Sie eine flache Liste des Produkts Model Name-Funktion-Paare, für jedes Paar eingeschlossen in die \<Features >-Element  
 In der Katalogbeschreibung des Produktmodells enthält der XML-Code mehrere Produktfunktionen. Alle diese Features sind enthalten, der <`Features`> Element. Die Abfrage verwendet [XML-Konstruktion (XQuery)](../xquery/xml-construction-xquery.md) der erforderlichen XML-Code erstellen. Der Ausdruck in den geschweiften Klammern wird durch das Ergebnis ersetzt.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  for $pd in /p1:ProductDescription,  
   $f in $pd/p1:Features/*  
  return  
   <Feature>  
     <ProductModelName> { data($pd/@ProductModelName) } </ProductModelName>  
     { $f }  
  </Feature>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   $pd / P1: Features / * gibt nur die untergeordneten Elemente des <`Features`>, aber $pd / P1:Features/Node() gibt alle Knoten zurück. Das schließt Elementknoten, Textknoten, Verarbeitungsanweisungen und Kommentare ein.  
  
-   Die beiden FOR-Schleifen generieren ein kartesisches Produkt, aus dem der Produktname und die individuelle Funktion zurückgegeben werden.  
  
-   Die **ProductName** ist ein Attribut. Die XML-Konstruktion in dieser Abfrage gibt dieses als ein Element zurück.  
  
 Dies ist ein Teilergebnis gezeigt:  
  
```  
<Feature>  
 <ProductModelName>Mountain 100</ProductModelName>  
 <ProductModelID>19</ProductModelID>  
 <p1:Warranty   
   xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
 </p1:Warranty>  
</Feature>  
<Feature>  
 <ProductModelName>Mountain 100</ProductModelName>  
 <ProductModelID>19</ProductModelID>  
 <p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer   
           or any AdventureWorks retail store.</p2:Description>  
    </p2:Maintenance>  
</Feature>  
...  
...      
```  
  
### <a name="d-from-the-catalog-description-of-a-product-model-list-the-product-model-name-model-id-and-features-grouped-inside-a-product-element"></a>D. Anhand der katalogbeschreibung eines Produktmodells, Liste der Product-Modell-Name, Modell-ID und Features gruppiert in einem \<Product >-Element  
 In der katalogbeschreibung des Produktmodells gespeicherte Informationen die folgende Abfrage listet produktmodellname, Modell-ID, und mit, Features gruppiert in einem \<Product >-Element.  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
     declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>  
         <ProductModelName>   
           { data(/pd:ProductDescription/@ProductModelName) }   
         </ProductModelName>  
         <ProductModelID>   
           { data(/pd:ProductDescription/@ProductModelID) }   
         </ProductModelID>  
         { /pd:ProductDescription/pd:Features/* }  
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Dies ist ein Teilergebnis gezeigt:  
  
```  
<Product>  
  <ProductModelName>Mountain 100</ProductModelName>  
  <ProductModelID>19</ProductModelID>  
  <p1:Warranty>... </p1:Warranty>  
  <p2:Maintenance>...  </p2:Maintenance>  
  <p3:wheel xmlns:p3="https://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p3:wheel>  
  <p4:saddle xmlns:p4="https://www.adventure-works.com/schemas/OtherFeatures">  
    <p5:i xmlns:p5="http://www.w3.org/1999/xhtml">Anatomic design</p5:i> and made from durable leather for a full-day of riding in comfort.</p4:saddle>  
  <p6:pedal xmlns:p6="https://www.adventure-works.com/schemas/OtherFeatures">  
    <p7:b xmlns:p7="http://www.w3.org/1999/xhtml">Top-of-the-line</p7:b> clipless pedals with adjustable tension.</p6:pedal>  
   ...  
```  
  
### <a name="e-retrieve-product-model-feature-descriptions"></a>E. Abrufen von Produktmodell-Funktionsbeschreibungen  
 Die folgende Abfrage erstellt XML mit einem <`Product`>-Element mit **ProducModelID**, **ProductModelName** Attribute und die ersten beiden Produktfunktionen enthält. Insbesondere werden die ersten beiden Produktfunktionen enthält die ersten beiden untergeordneten Elemente von der <`Features`> Element. Wenn mehrere Funktionen vorhanden sind, gibt es eine leere <`There-is-more/`> Element.  
  
```  
SELECT CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /pd:ProductDescription/@ProductModelID }  
          { /pd:ProductDescription/@ProductModelName }   
          {  
            for $f in /pd:ProductDescription/pd:Features/*[position()<=2]  
            return  
            $f   
          }  
          {  
            if (count(/pd:ProductDescription/pd:Features/*) > 2)  
            then <there-is-more/>  
            else ()  
          }   
     </Product>          
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not NULL  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die FOR... RETURN-Schleifenstruktur Ruft die ersten beiden Produktfunktionen ab. Die **position()** Funktion wird verwendet, um die Position der Elemente in der Sequenz zu finden.  
  
### <a name="f-find-element-names-from-the-product-catalog-description-that-end-with-ons"></a>F. Suchen von Elementnamen in der Produktkatalogbeschreibung, die mit "ons" enden  
 Die folgende Abfrage durchsucht die katalogbeschreibungen und gibt alle Elemente in der <`ProductDescription`> Element, dessen Name mit "Ons" endet.  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
     declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      for $pd in /p1:ProductDescription/*[substring(local-name(.),string-length(local-name(.))-2,3)="ons"]  
      return   
          <Root>  
             { $pd }  
          </Root>  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not NULL  
```  
  
 Dies ist ein Teilergebnis gezeigt:  
  
```  
ProductModelID   Result  
-----------------------------------------  
         19        <Root>         
                     <p1:Specifications xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">          
                          ...         
                     </p1:Specifications>         
                   </Root>          
```  
  
### <a name="g-find-summary-descriptions-that-contain-the-word-aerodynamic"></a>G. Suchen von Zusammenfassungsbeschreibungen mit dem Wort "Aerodynamic"  
 Die folgende Abfrage ruft die Produktmodelle ab, deren Produktbeschreibung das Wort "Aerodynamic" in der zusammenfassenden Beschreibung enthält:  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
          <Prod >  
             { /pd:ProductDescription/@ProductModelID }  
             { /pd:ProductDescription/pd:Summary }  
          </Prod>  
 ') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.value('  
     contains( string( (/pd:ProductDescription/pd:Summary)[1] ),"Aerodynamic")','bit') = 1  
```  
  
 Beachten Sie, der angibt, die SELECT-Abfrage **query()** und **Value()-Methode** Methoden der **Xml** -Datentyp. Deshalb muss die Namespacedeklaration nicht zweimal in zwei verschiedenen Abfrageprologen wiederholt werden, sondern das Präfix pd wird in der Abfrage verwendet und nur einmal mit WITH XMLNAMESPACES definiert.  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die WHERE-Klausel verwendet wird, um nur die Zeilen abzurufen, in die katalogbeschreibung das Wort "Aerodynamic", in enthält, der <`Summary`> Element.  
  
-   Die **contains()** Funktion wird verwendet, um festzustellen, ob das Wort im Text enthalten ist.  
  
-   Die **Value()-Methode** Methode der **Xml** -Datentyps vergleicht den Rückgabewert von **contains()** auf 1.  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID Result        
-------------- ------------------------------------------  
28     <Prod ProductModelID="28">  
        <pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
       <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">  
         A TRUE multi-sport bike that offers streamlined riding and a  
         revolutionary design. Aerodynamic design lets you ride with the   
         pros, and the gearing will conquer hilly roads.</p1:p>  
       </pd:Summary>  
      </Prod>    
```  
  
### <a name="h-find-product-models-whose-catalog-descriptions-do-not-include-product-model-pictures"></a>H. Suchen nach Produktmodellen, deren Katalogbeschreibung keine Produktmodellbilder enthält.  
 Die folgende Abfrage ruft ProductModelIDs für Produkte, deren katalogbeschreibungen nicht Modelle umfassen eine <`Picture`> Element.  
  
```  
SELECT  ProductModelID  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not NULL  
AND     CatalogDescription.exist('declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /p1:ProductDescription/p1:Picture  
') = 0  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Wenn die **exist()** -Methode in die WHERE-Klausel False (0) zurück, die Produktmodell-ID wird zurückgegeben. Ansonsten wird sie nicht zurückgegeben.  
  
-   Da alle produktbeschreibungen enthalten ein <`Picture`>-Element, das Resultset leer ist in diesem Fall.  
  
## <a name="see-also"></a>Siehe auch  
 [XQueries Einbeziehung von Hierarchien](../xquery/xqueries-involving-hierarchy.md)   
 [XQueries Involving Order](../xquery/xqueries-involving-order.md)   
 [Behandlung relationaler Daten mit XQuery-Abfragen](../xquery/xqueries-handling-relational-data.md)   
 [Zeichenfolgensuche in XQuery](../xquery/string-search-in-xquery.md)   
 [Handhabung von Namespaces in XQuery](../xquery/handling-namespaces-in-xquery.md)   
 [Hinzufügen von Namespaces zu Abfragen mit WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [XML-Daten &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
