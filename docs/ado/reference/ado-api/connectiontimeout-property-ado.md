---
title: ConnectionTimeout-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 03d3de2c4aabaf4ad8cbc45d9900b33883ff9a48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933463"
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout-Eigenschaft (ADO)
Gibt an, wie lange warten, die beim Herstellen einer Verbindung, bevor der Versuch beendet und ein Fehler generiert.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** hodnota ukazuje, in Sekunden an, wie lange warten, bis die Verbindung zu öffnen. Standardwert ist 15.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die **ConnectionTimeout** Eigenschaft für eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt, wenn Verzögerungen von Netzwerk-Datenverkehr oder hohem Server verwenden, einen Verbindungsversuch abzubrechen erforderlich machen. Wenn die Zeit aus der **ConnectionTimeout** eigenschafteneinstellung abläuft, vor dem Öffnen der Verbindung ein Fehler auftritt und ADO den Versuch abbricht. Wenn Sie die Eigenschaft auf 0 (null) festlegen, wartet die ADO auf unbestimmte Zeit, bis die Verbindung geöffnet wird. Stellen Sie sicher, dass der Anbieter, der Sie Code schreiben, unterstützt die **ConnectionTimeout** Funktionalität.  
  
 Die **ConnectionTimeout** Eigenschaft ist Lese-/Schreibzugriff auf, wenn die Verbindung ist geschlossen und Read-only, wenn er geöffnet ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [ConnectionString und ConnectionTimeout State-Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString und ConnectionTimeout State-Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
