---
title: SQLSetStmtOption (Desktop-Datenbanktreiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20043c96771bf888defa2c8fbeb028aaa18f5abc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905347"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (Desktop-Datenbanktreiber)

|*fOption*|Kommentare|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Die asynchrone Verarbeitung wird nicht unterstützt. Die SQL_ASYNC_ENABLE fOption SQLSTATE S1C00 zurück (nicht-Treiber).|  
|SQL_KEYSET_SIZE|Die einzigen gültigen Keysetgröße ist 0 (null), da kombiniert und dynamische Cursor werden nicht unterstützt. Wenn dieser Wert auf jede andere Zahl festgelegt ist, wird es in 0 geändert und der Aufruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01 s 02 (der Optionswert wurde geändert).|  
|SQL_MAX_ROWS|Die einzigen gültigen Rowsetgröße ist 0 (null), da die Anzahl der zurückgegebenen Zeilen einschränken der Desktop-Datenbanktreiber nicht unterstützt wird. Wenn dieser Wert auf jede andere Zahl festgelegt ist, wird es in 0 geändert und der Aufruf gibt SQL_SUCCESS_WITH_INFO und SQLSTATE 01 s 02 (der Optionswert wurde geändert).|  
|SQL_QUERY_TIMEOUT|Wird nicht unterstützt.|  
|SQL_ROW_NUMBER|Wird nicht unterstützt.|  
|SQL_SIMULATE_CURSOR|Wird nicht unterstützt.|
