---
title: Artikeloptionen für die Mergereplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], article options
- articles [SQL Server replication], merge replication options
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 478e6b9bb6f8300a845ae8fe9e3202f750f525eb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106114"
---
# <a name="article-options-for-merge-replication"></a>Artikeloptionen für die Mergereplikation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Mergereplikation bietet viele Optionen für Mergetabellenartikel, mit denen Sie das Replikationsverhalten den Anforderungen Ihrer Anwendungen anpassen können. Der Einsatz der Mergereplikation bietet folgende Möglichkeiten:  
  
-   Sie können Zeilenfilter, Joinfilter und Spaltenfilter verwenden. Das Filtern von Tabellenartikeln ermöglicht es Ihnen, Datenpartitionen zu erstellen, die veröffentlicht werden können. Weitere Informationen finden Sie unter [Filtern von veröffentlichten Daten](../../../relational-databases/replication/publish/filter-published-data.md).  
  
-   Sie können angeben, ob Änderungen des Abonnenten auf den Verleger hochgeladen werden sollen. Bei Anwendungen, in denen auf dem Abonnenten bestimmte oder alle Daten schreibgeschützt sein sollen, bieten nur herunterladbare Artikel eine Möglichkeit zur Leistungssteigerung. Weitere Informationen finden Sie unter [Optimieren der Leistung der Mergereplikation durch nur herunterladbare Artikel](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md).  
  
-   Sie können angeben, dass Löschvorgänge für einen oder mehrere Artikel nicht von Replikationstriggern oder in Systemtabellen nachverfolgt werden sollen. Diese Option kann in vielen Anwendungsszenarios nützlich sein. Hierzu gehören auch Szenarios mit Batchlöschvorgängen, die nicht repliziert werden müssen. Weitere Informationen finden Sie unter [Optimieren der Mergereplikationsleistung durch bedingtes Nachverfolgen von Löschvorgängen](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md).  
  
-   Sie können die Verarbeitungsreihenfolge von Artikeln angeben, um sicherzustellen, dass diese in der für die Anwendung erforderlichen Reihenfolge verarbeitet werden. Weitere Informationen finden Sie unter [Specify merge replication options (Festlegen von Mergereplikationsoptionen)](../../../relational-databases/replication/merge/specify-merge-replication-properties.md).  
  
-   Sie können angeben, dass miteinander verbundene Datensätze als Einheit verarbeitet werden sollen (standardmäßig verarbeitet die Mergereplikation Änderungen in Tabellen zeilenweise). Weitere Informationen finden Sie unter [Gruppieren von Änderungen an verknüpften Zeilen mithilfe von logischen Datensätzen](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
-   Sie können die Konflikterkennung und -lösung verwenden, wenn dieselben Daten auf mehreren Knoten der Topologie geändert werden. Weitere Informationen finden Sie unter [Detect and Resolve Merge Replication Conflicts](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
-   Sie können Schemaoptionen angeben, beispielsweise ob Einschränkungen und Trigger auf den Abonnenten kopiert werden. Weitere Informationen finden Sie unter [Angeben von Schemaoptionen](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
-   Verwenden Sie einen Geschäftslogikhandler, um während der Synchronisierung auf viele Bedingungen zu reagieren. Hierzu gehören Datenänderungen, Konflikte und Fehler. Weitere Informationen finden Sie unter [Ausführen von Geschäftslogik während der Mergesynchronisierung](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Daten und Datenbankobjekten](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
