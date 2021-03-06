---
title: ADOStreamConstruction-Schnittstelle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 70a6dd02722a34159b345a83b32897aa8c38d0ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920784"
---
# <a name="adostreamconstruction-interface"></a>ADOStreamConstruction-Schnittstelle
Die **ADOStreamConstruction** Schnittstelle wird verwendet, um eine ADO erstellen **Stream** Objekt von einem OLE DB **IStream** Objekts in einer C/C++-Anwendung.  
  
## <a name="properties"></a>Eigenschaften  
  
|||  
|-|-|  
|[Stream-Eigenschaft](../../../ado/reference/ado-api/stream-property.md)|Lese-/Schreibzugriff. Ruft ab oder legt ihn fest, eine OLE DB **Stream** Objekt.|  
  
## <a name="methods"></a>Methoden  
 Keine  
  
## <a name="events"></a>Ereignisse  
 Keine  
  
## <a name="remarks"></a>Hinweise  
 Erhalten eine OLE DB **IStream** Objekt (`pStream`), die zur Erstellung eines ADO **Stream** Objekt (`adoStr`) die folgenden drei grundlegenden Schritten:  
  
1.  Erstellen Sie ein ADO **Stream** Objekt:  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  Abfrage der **IADOStreamConstruction** Schnittstelle, für die **Stream** Objekt:  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 Rufen Sie die `IADOStreamConstruction::get_Stream` -Methode zum Festlegen von OLE DB-Eigenschaft **IStream** der ADO-Objekt **Stream** Objekt:  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 Die resultierenden `adoStr` Objekt stellt nun das ADO **Stream** Objekt erstellt, die von der OLE DB **IStream** Objekt.  
  
## <a name="requirements"></a>Anforderungen  
 **Version:** ADO 2.0 oder höher  
  
 **Bibliothek:** "MSADO15.dll"  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Siehe auch  
 [ADO – API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)
