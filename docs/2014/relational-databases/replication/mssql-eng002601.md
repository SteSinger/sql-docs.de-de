---
title: MSSQL_ENG002601 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002601 error
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a3994aa8a442f0ec1522bdf2314e0d6023e94bcf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62667064"
---
# <a name="mssqleng002601"></a>MSSQL_ENG002601
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2601|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name|Nicht zutreffend|  
|Meldungstext|Eine Zeile mit doppeltem Schlüssel kann nicht in das '%.*ls'-Objekt mit dem eindeutigen '%.\*ls'-Index eingefügt werden.|  
  
## <a name="explanation"></a>Erklärung  
 Das ist ein allgemeiner Fehler, der unabhängig davon ausgelöst werden kann, ob eine Datenbank repliziert wird. Bei replizierten Datenbanken wird der Fehler in der Regel ausgelöst, weil Primärschlüssel in der Topologie nicht richtig verwaltet wurden. In einer verteilten Umgebung muss unbedingt sichergestellt werden, dass in mehreren Knoten nicht der gleiche Wert in eine Primärschlüsselspalte oder eine andere eindeutige Spalte eingefügt wird. Die folgenden Ursachen können zugrunde liegen:  
  
-   Einfügungen und Updates an einer Zeile finden in mehreren Knoten statt. Die Mergereplikation und aktualisierbare Abonnements für Transaktionsreplikationen stellen jeweils eine Konflikterkennung und -lösung bereit. Dennoch ist es besser, eine bestimmte Zeile nur in einem Knoten einzufügen oder zu aktualisieren. Die Peer-zu-Peer-Transaktionsreplikation stellt keine Konflikterkennung und -lösung bereit. Einfügungen und Updates müssen partitioniert werden.  
  
-   Auf einem Abonnenten wurde eine Zeile eingefügt, die schreibgeschützt sein sollte. Abonnenten von Momentaufnahmeveröffentlichungen sollten als schreibgeschützt behandelt werden, ebenso wie Abonnenten von Transaktionsveröffentlichungen, außer es werden aktualisierbare Abonnements oder die Peer-zu-Peer-Transaktionsreplikation verwendet.  
  
-   Es wird eine Tabelle mit einer Identitätsspalte verwendet, die Spalte wird jedoch nicht ordnungsgemäß verwaltet.  
  
-   Bei der Mergereplikation dieser Fehler kann auch auftreten, während eines INSERTS in die Systemtabelle **MSmerge_contents**; der Fehler wird ausgelöst, ähnelt: Zeile mit doppeltem Schlüssel kann nicht in 'MSmerge_contents'-Objekt mit dem eindeutigen Index 'ucl1SycContents.' eingefügt werden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Die erforderliche Aktion hängt davon ab, weshalb der Fehler ausgelöst wurde:  
  
-   Einfügungen und Updates an einer Zeile finden in mehreren Knoten statt.  
  
     Unabhängig vom Typ der verwendeten Replikation wird empfohlen, Einfügungen und Updates möglichst zu partitionieren, da dies den Verarbeitungsaufwand bei der Konflikterkennung und -lösung reduziert. Bei der Peer-zu-Peer-Transaktionsreplikation ist eine Partitionierung von Einfügungen und Updates erforderlich. Weitere Informationen finden Sie unter [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).  
  
-   Auf einem Abonnenten wurde eine Zeile eingefügt, die schreibgeschützt sein sollte.  
  
     Fügen Sie auf dem Abonnenten keine Zeilen ein und aktualisieren Sie keine Zeilen, es sei denn Sie verwenden die Mergereplikation, die Transaktionsreplikation mit aktualisierbaren Abonnements oder die Peer-zu-Peer-Transaktionsreplikation.  
  
-   Es wird eine Tabelle mit einer Identitätsspalte verwendet, die Spalte wird jedoch nicht ordnungsgemäß verwaltet.  
  
     Bei der Mergereplikation und der Transaktionsreplikation mit aktualisierbaren Abonnements sollten Identitätsspalten automatisch durch die Replikation verwaltet werden. Bei der Peer-zu-Peer-Transaktionsreplikation müssen sie manuell verwaltet werden. Weitere Informationen finden Sie unter [Replizieren von Identitätsspalten](publish/replicate-identity-columns.md).  
  
-   Der Fehler tritt während eines INSERTs in der **MSmerge_contents**-Systemtabelle auf.  
  
     Dieser Fehler kann auftreten, wenn für die Joinsfiltereigenschaft **join_unique_key**ein falscher Wert festgelegt wurde. Diese Eigenschaft sollte nur auf TRUE festgelegt werden, wenn die verknüpfte Spalte in der übergeordneten Tabelle eindeutig ist. Wenn die Eigenschaft auf TRUE festgelegt ist, die Spalte jedoch nicht eindeutig ist, wird dieser Fehler ausgelöst. Weitere Informationen zum Festlegen dieser Eigenschaft finden Sie unter [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
