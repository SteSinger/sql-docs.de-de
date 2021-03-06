---
title: Importieren von Informationen zum registrierten Server
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.importregisteredservers.f1
helpviewer_keywords:
- transferring registered server information
- Registered Servers [SQL Server], importing
- importing registered server information
ms.assetid: cc497a14-1360-4887-b70c-002f042823b6
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 32ef669c238c52ec5e5e20804c896b4364c8bc85
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75241352"
---
# <a name="import-registered-server-information-sql-server-management-studio"></a>Importieren von Informationen zum registrierten Server (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie Sie gespeicherte Informationen zu registrierten Servern in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]importieren. Durch das Exportieren und Importieren von Dateien mit registrierten Servern können Sie schnell und einfach mehrere Computer mit denselben Servern konfigurieren. Besonders hilfreich ist dies, wenn Sie eine große Anzahl von Servern auf Computern an mehreren Standorten verwalten oder Sie für einen weniger erfahrenen Benutzer die grundlegenden Verbindungseinstellungen konfigurieren möchten.  
  
> [!NOTE]  
>  Sie können keine registrierten Serverinformationen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aus früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]importieren.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-import-registered-server-information"></a>So importieren Sie Informationen zum registrierten Server  
  
1.  Klicken Sie in Registrierte Server auf der Symbolleiste Registrierte Server auf den Servertyp. Der Servertyp muss mit dem Exportdateityp des registrierten Servers identisch sein. Wenn Sie z. B. Informationen zum registrierten Server von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exportiert haben, müssen Sie auf der Symbolleiste Registrierte Server auf **SQL Server** klicken.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine Servergruppe, und klicken Sie dann auf **Importieren**.  
  
3.  Wählen Sie im Dialogfeld **Registrierte Server importieren** die zu importierende Datei mit den registrierten Servern aus, und klicken Sie dann auf **OK**.  
  
     **Importieren einer Datei**  
     Geben Sie den Namen der Importdatei in das Textfeld ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen (**...**), um eine Importdatei auf dem Clientcomputer auszuwählen. Wenn Sie eine vorhandene Datei auswählen, werden die Daten der registrierten Server an die Datei angehängt. Die Importdatei kann nur eine zuvor exportierte Datei mit registrierten Servern sein. Dateien mit registrierten Servern haben die Dateierweiterung .regsrvr.  
  
     **Wählen Sie die Server Gruppe für den Import aus.**  
     Wählen Sie einen Stammknoten oder eine bestimmte Servergruppe aus, in den/die die Einträge zu den registrierten Servern in der Datei importiert werden. Sie können alle registrierten Server, die registrierten Server in einer bestimmten Servergruppe oder einzelne registrierte Server in die Exportdatei importieren. Die Importfunktion ist rekursiv. Wenn z. B. Servergruppe A die Servergruppe B enthält und Servergruppe B die Servergruppen C und D enthält, werden beim Import von Servergruppe A alle Einträge in A, B, C und D exportiert.  
  
     In der Servergruppe werden nur die Servergruppen der Baumstruktur des aktuellen registrierten Servers angezeigt.  
  
     Wenn Sie eine vorhandene Servergruppe oder einen vorhandenen Server importieren, werden Sie in einer Meldung darauf hingewiesen, dass bei diesem Vorgang ein vorhandener Server oder eine vorhandene Servergruppe überschrieben werden.  
  
 Serverregistrierungen, die die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung nutzen, speichern die Kennwörter auf Benutzerbasis. Nach dem Importieren der Serverregistrierungen müssen Benutzer beim ersten Herstellen der Verbindung für jeden Server ein Kennwort eingeben. Diese werden in den Listen der registrierten Server gespeichert. Bei Servern, die mithilfe der Windows-Authentifizierung registriert wurden, ist dies nicht erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ändern Sie die Registrierungs &#40;eines Servers SQL Server Management Studio&#41;](change-a-server-s-registration-sql-server-management-studio.md) die [Informationen zum registrierten Server &#40;SQL Server Management Studio exportieren&#41;](export-registered-server-information-sql-server-management-studio.md)   
 [Erstellen Sie einen neuen registrierten Server &#40;SQL Server Management Studio&#41;](create-a-new-registered-server-sql-server-management-studio.md)  
  
  
