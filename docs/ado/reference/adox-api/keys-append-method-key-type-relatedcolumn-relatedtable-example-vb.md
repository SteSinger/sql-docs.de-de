---
title: Erstellen Sie eine neue Fremdschlüssel-Beziehung zwischen Tabellen – Beispiel (VB) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Key Type property [ADOX], Visual Basic example
- RelatedTable property [ADOX], Visual Basic example
- Keys Append method [ADOX], Visual Basic example
- UpdateRule property [ADOX], Visual Basic example
- RelatedColumn property [ADOX], Visual Basic example
ms.assetid: 13b5b1c3-6af6-439e-bb65-976578ba6bc2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6873b964adfcfc5bffed5d093bed48f4fbd29a20
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965868"
---
# <a name="keys-append-method-key-type-relatedcolumn-relatedtable-and-updaterule-properties-example-vb"></a>Append-Methode für Schlüssel, Key Type-, RelatedColumn-, RelatedTable- und UpdateRule-Eigenschaften – Beispiel (VB)
Der folgende Code veranschaulicht, wie eine neue Fremdschlüssel-Beziehung zwischen zwei vorhandenen Tabellen, die mit dem Namen **Kunden** und **Bestellungen**.  
  
```  
' BeginCreateKeyVB  
Sub Main()  
    On Error GoTo CreateKeyError  
  
    Dim kyForeign As New ADOX.Key  
    Dim cat As New ADOX.Catalog  
  
    ' Connect to the catalog.  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Define the foreign key.  
    kyForeign.Name = "CustOrder"  
    kyForeign.Type = adKeyForeign  
    kyForeign.RelatedTable = "Customers"  
    kyForeign.Columns.Append "CustomerId"  
    kyForeign.Columns("CustomerId").RelatedColumn = "CustomerId"  
    kyForeign.UpdateRule = adRICascade  
  
    ' Append the foreign key to the keys collection.  
    cat.Tables("Orders").Keys.Append kyForeign  
  
    'Delete the key t demonstrate the Delete method.  
    cat.Tables("Orders").Keys.Delete kyForeign.Name  
  
    'Clean up.  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set kyForeign = Nothing  
    Exit Sub  
  
CreateKeyError:  
    Set cat = Nothing  
    Set kyForeign = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
' EndCreateKeyVB  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Append-Methode (ADOX-Spalten)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [-Objekt (ADOX)](../../../ado/reference/adox-api/key-object-adox.md)   
 [Keys-Auflistung (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)   
 [Name-Eigenschaft (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [RelatedColumn-Eigenschaft (ADOX)](../../../ado/reference/adox-api/relatedcolumn-property-adox.md)   
 [RelatedTable-Eigenschaft (ADOX)](../../../ado/reference/adox-api/relatedtable-property-adox.md)   
 [Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type-Eigenschaft (Schlüssel) (ADOX)](../../../ado/reference/adox-api/type-property-key-adox.md)   
 [UpdateRule-Eigenschaft (ADOX)](../../../ado/reference/adox-api/updaterule-property-adox.md)
