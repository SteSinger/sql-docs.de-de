---
title: Append-Methode (ADOX-Spalten) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Columns::raw_Append
- Columns::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6493157c00e5a71c7c2f085191231bb33bb5279a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967324"
---
# <a name="append-method-adox-columns"></a>Append-Methode (ADOX-Spalten)
Fügt ein neues [Spalte](../../../ado/reference/adox-api/column-object-adox.md) -Objekt an die [Spalten](../../../ado/reference/adox-api/columns-collection-adox.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Columns.Append Column [,Type] [,DefinedSize]  
```  
  
#### <a name="parameters"></a>Parameter  
 *Spalte*  
 Die **Spalte** anzufügende Objekt oder den Namen der Spalte zu erstellen und anfügen.  
  
 *Typ*  
 Dies ist optional. Ein **lange** Wert, der den Datentyp der Spalte angibt. Die *Typ* Parameter entspricht der [Typ](../../../ado/reference/adox-api/type-property-column-adox.md) Eigenschaft eine **Spalte** Objekt.  
  
 *DefinedSize*  
 Dies ist optional. Ein **lange** Wert, der die Größe der Spalte angibt. Die *DefinedSize* Parameter entspricht der [DefinedSize](../../../ado/reference/adox-api/definedsize-property-adox.md) Eigenschaft eine **Spalte** Objekt.  
  
> [!NOTE]
>  Beim Anfügen, wird ein Fehler auftreten. ein **Spalte** auf die **Spalten** Auflistung von ein [Index](../../../ado/reference/adox-api/index-object-adox.md) Wenn die **Spalte** ist nicht in einem [Tabelle](../../../ado/reference/adox-api/table-object-adox.md) , ist bereits angefügt, um die [Tabellen](../../../ado/reference/adox-api/tables-collection-adox.md) Auflistung.  
  
## <a name="applies-to"></a>Gilt für  
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Spalten und Tabellen Append-Methode, Name-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append-Methode, Typ des Schlüssels, RelatedColumn-, RelatedTable- und UpdateRule-Eigenschaften-Beispiel (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog-Eigenschaft – Beispiel (VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)   
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX Indizes)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append-Methode (ADOX-Schlüssel)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append-Methode (ADOX Prozeduren)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append-Methode (ADOX-Tabellen)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append-Methode (ADOX-Ansichten)](../../../ado/reference/adox-api/append-method-adox-views.md)
