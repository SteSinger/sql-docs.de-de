---
title: Arbeiten mit Facets der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 037eb57f53bf583195efdf1f91fcd55f94ebaddc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62676902"
---
# <a name="working-with-policy-based-management-facets"></a>Arbeiten mit Facets der richtlinienbasierten Verwaltung
  Ein Facet der richtlinienbasierten Verwaltung ist ein Satz von logischen Eigenschaften, die sich auf einen verwaltungsrelevanten Bereich beziehen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst mehrere vordefinierte Facets. Dazu gehört beispielsweise das Facet für die Oberflächenkonfiguration, das die standardmäßig deaktivierten Funktionen als Eigenschaften definiert.  
  
 Wenn Sie viele ähnliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Umgebungen verwalten, können Sie ein Facet für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]konfigurieren, den Status des Facets in eine Datei kopieren und diese Datei anschließend als Richtlinie in eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] importieren. Sobald der Status in eine Richtlinie umgewandelt wurde, kann die Richtlinie auf andere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Instanzobjekte, Datenbanken oder Datenbankobjekte angewendet werden.  
  
 In diesem Thema wird beschrieben, wie der Status eines Facets in eine XML-Datei kopiert wird.  
  
##  <a name="BeforeYouBegin"></a> Berechtigungen  
 Die Verfahren in diesem Thema erfordern die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
## <a name="viewing-and-copying-facet-states"></a>Anzeigen und Kopieren von Facet-Status  
 [Anzeigen der Facets der richtlinienbasierten Verwaltung für ein SQL Server-Objekt](view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [Kopieren eines Facet-Status der richtlinienbasierten Verwaltung in eine XML-Datei](copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Servern mit der richtlinienbasierten Verwaltung](administer-servers-by-using-policy-based-management.md)  
  
  
