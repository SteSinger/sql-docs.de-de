---
title: DateCreated-Eigenschaft (ADOX) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0151b6388a19fc95227cbfa55a571e0a797d0acc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966570"
---
# <a name="datecreated-property-adox"></a>DateCreated-Eigenschaft (ADOX)
Gibt das Datum, die das Objekt erstellt wurde.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Variant** Wert, der das Erstellungsdatum angibt. Der Wert ist null Wenn **DateCreated** wird vom Anbieter nicht unterstützt.  
  
## <a name="remarks"></a>Hinweise  
 Die **DateCreated** -Eigenschaft ist null für die neu angefügte Objekte. Nach dem Anfügen eines neuen [Ansicht](../../../ado/reference/adox-api/view-object-adox.md) oder [Prozedur](../../../ado/reference/adox-api/procedure-object-adox.md), rufen Sie die [aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md) -Methode der der [Ansichten](../../../ado/reference/adox-api/views-collection-adox.md) oder [Prozeduren ](../../../ado/reference/adox-api/procedures-collection-adox.md) Auflistung abzurufenden Werte für die **DateCreated** Eigenschaft.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Procedure Object (ADOX) (Procedure-Objekt (ADOX))](../../../ado/reference/adox-api/procedure-object-adox.md)|[Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[View-Objekt (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [DateCreated und DateModified Eigenschaften – Beispiel (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [DateModified-Eigenschaft (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
