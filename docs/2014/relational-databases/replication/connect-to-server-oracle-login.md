---
title: Verbindung mit Server herstellen (Oracle), Anmeldename | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fddf6045921fa14e09aaff918f84125eb907e9ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721742"
---
# <a name="connect-to-server-oracle-login"></a>Verbindung mit Server herstellen (Oracle), Anmeldename
  Auf der Registerkarte **Anmeldename** des Dialogfelds **Verbindung mit Server herstellen** können Sie das Konto angeben, unter dem der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verteiler Verbindungen mit dem Oracle-Verleger herstellt. Sie müssen dafür dasselbe Konto verwenden wie für das Schema des administrativen Replikationsbenutzers, das Sie bei der Konfiguration des Verlegers angegeben haben. Weitere Informationen finden Sie unter [Konfigurieren eines Oracle-Verlegers](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Optionen  
 **Serverinstanz**  
 Der TNS-Name (Transparent Network Substrate) des Oracle-Verlegers, der bei Konfiguration der auf dem Verteiler installierten Oracle-Clientsoftware angegeben wurde.  
  
 **Authentifizierung**  
 Wählen Sie **Oracle-Standardauthentifizierung** (empfohlen) oder **Windows-Authentifizierung**aus. Bei Auswahl von **Windows-Authentifizierung**:  
  
-   Der Oracle-Server muss so konfiguriert sein, dass mit den Windows-Anmeldeinformationen Verbindungen hergestellt werden können. Weitere Informationen finden Sie in der Oracle-Dokumentation.  
  
-   Sie müssen dazu auf demselben [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto angemeldet sein, wie für das Schema des administrativen Replikationsbenutzers angegeben wurde.  
  
 **Anmeldename** und **Kennwort**  
 Wenn Sie für die **Authentifizierung** die Option **Oracle-Standardauthentifizierung** ausgewählt haben, geben Sie den zu verwendenden Anmeldenamen und das Kennwort an. Verwenden Sie dabei dieselben Angaben wie für das Schema des administrativen Replikationsbenutzers.  
  
## <a name="see-also"></a>Siehe auch  
 [Glossary of Terms for Oracle Publishing](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
