---
title: SQLPostInstallerError-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0d5e0a10b8c530494fa3c026be0d36fde066a97c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053670"
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLPostInstallerError** bietet einen Mechanismus für eine Treiber oder das Konvertierungsprogramm Setup-Bibliothek, um Fehler in der **ConfigDriver**, **ConfigDSN**, und **ConfigTranslator**  Funktionen in die Fehlerwarteschlange Installer. Anwendungen verwenden diese API nicht. Sie verwenden **SQLInstallerError** um den Fehler abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Argumente  
 *fErrorCode*  
 [Eingabe] Installer-Fehlercode.  
  
 *szErrorMsg*  
 [Eingabe] Text der Fehlermeldung.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS oder SQL_ERROR zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLPostInstallerError** veröffentlichen Fehlerwerte nicht für sich selbst. Wenn der Fehler in die Fehlerwarteschlange Installer wurde erfolgreich gesendet wurde (abrufbar mithilfe **SQLInstallerError**), wird SQL_SUCCESS zurückgegeben. Wird SQL_ERROR zurückgegeben, wenn der Wert in der *DwErrorCode* Argument ist nicht der angegebene Installationsprogramm-Fehlercodes.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Hinzufügen, ändern oder Entfernen von Datenquellen|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Festlegen einer Übersetzungsoption|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
