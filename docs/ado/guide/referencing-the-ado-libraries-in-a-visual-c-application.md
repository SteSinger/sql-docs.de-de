---
title: Verweis auf die ADO-Bibliotheken In Visual C++-Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 62fb1b89299af1f466e446c8adba422a841f0196
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923023"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Verweis auf die ADO-Bibliotheken in Visual C++-Anwendungen
Um die neueste Version von ADO in Visual C++-Anwendung verwenden zu können, verwenden Sie die folgenden `#import` Richtlinie:  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 Um ADO MD oder ADOX verwenden, müssen Sie importieren *msadomd.dll* oder *msadox.dll*, mithilfe der oben aufgeführten Syntax.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Um eine frühere Version von ADO verwenden, ersetzen *"MSADO15.dll"* oben mit einem der folgenden Typbibliotheken.  
  
-   *msado27.tlb*, ADO 2.7 Typbibliothek.  
  
-   *msado26.tlb*, ADO 2.6-Typbibliothek  
  
-   *msado25.tlb*, ADO-2,5-Typbibliothek  
  
-   *MSADO21.tlb*, ADO 2.1 Typbibliothek.  
  
-   *msado20.tlb*, ADO-2.0-Typbibliothek
