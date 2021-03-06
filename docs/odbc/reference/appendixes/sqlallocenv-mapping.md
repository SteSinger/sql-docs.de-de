---
title: SQLAllocEnv-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afbd1404cb40408166ecfc59993db7b183ae5ed2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065007"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv-Zuordnung
Wenn eine Anwendung ruft **SQLAllocEnv** über einen ODBC *3.x* Treiber, den Aufruf von **SQLAllocEnv**(*Phenv*) zugeordnet**SQLAllocHandle** wie folgt:  
  
1.  Der Treiber-Manager weist ein Umgebungshandle und an die Anwendung zurückgegeben. Der Treiber-Manager ruft **SQLSetEnvAttr** umgebungsattributs SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC2 festgelegt.  
  
2.  Wenn die Anwendung die erste Verbindung zu einem Treiber hergestellt wird, ruft der Treiber-Manager  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     in den Treiber mit *OutputHandlePtr* festgelegt *Phenv*.
