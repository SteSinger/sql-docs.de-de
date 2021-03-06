---
title: Öffnen und Speichern von Dateien mit in Azure bereitgestellten SSIS-Paketen | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Dateien lokal und in Azure öffnen und speichern, wenn Sie SSIS-Pakete, die lokale Dateisysteme verwenden, per Lift & Shift in SSIS in Azure migrieren.
ms.date: 06/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
ms.openlocfilehash: 696b7bbd19ed41aeedaf0cbba683870c04de1b13
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67896200"
---
# <a name="open-and-save-files-on-premises-and-in-azure-with-ssis-packages-deployed-in-azure"></a>Öffnen und Speichern von Dateien lokal und in Azure mit in Azure bereitgestellten SSIS-Paketen

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



In diesem Artikel wird beschrieben, wie Sie Dateien lokal und in Azure öffnen und speichern, wenn Sie SSIS-Pakete, die lokale Dateisysteme verwenden, per Lift & Shift in SSIS in Azure migrieren.

## <a name="save-temporary-files"></a>Speichern von temporären Dateien
Wenn Sie temporäre Dateien während einer einzelnen Paketausführung speichern und verarbeiten müssen, können Pakete das aktuelle Arbeitsverzeichnis (`.`) oder den temporären Ordner (`%TEMP%`) Ihrer Azure SSIS Integration Runtime-Knoten verwenden.

## <a name="use-on-premises-file-shares"></a>Verwenden von lokalen Dateifreigaben
Wenn Sie Pakete, die lokale Dateisysteme verwenden, zu SSIS in Azure migrieren und weiterhin **lokale Dateifreigaben** verwenden möchten, führen Sie die folgenden Schritte durch:
1.  Übertragen Sie die Dateien von den lokalen Dateisystemen auf die lokalen Dateifreigaben.
2.  Verknüpfen Sie die lokalen Dateifreigaben mit einem virtuellen Azure-Netzwerk.
3.  Verknüpfen Sie Ihre Azure SSIS IR mit demselben virtuellen Netzwerk. Weitere Informationen finden Sie unter [Verknüpfen einer Azure SSIS Integration Runtime mit einem virtuellen Netzwerk](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network).
4.  Verbinden Sie Ihre Azure SSIS IR mit den lokalen Dateifreigaben innerhalb desselben virtuellen Netzwerks, indem Sie Anmeldeinformationen einrichten, die mit der Windows-Authentifizierung verwendet werden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Datenquellen und Dateifreigaben mit der Windows-Authentifizierung](ssis-azure-connect-with-windows-auth.md).
5.  Ändern Sie lokale Dateipfade in Ihren Paketen in UNC-Pfade, die auf lokale Dateifreigaben verweisen. Ändern Sie z.B. den Pfad `C:\abc.txt` in `\\<on-prem-server-name>\<share-name>\abc.txt`.

## <a name="use-azure-file-shares"></a>Verwenden von Azure-Dateifreigaben
Wenn Sie Pakete, die lokale Dateisysteme verwenden, zu SSIS in Azure migrieren und **Azure Files**verwenden möchten, führen Sie die folgenden Schritte durch:
1.  Übertragen Sie die Dateien von den lokalen Dateisystemen zu Azure Files. Weitere Informationen finden Sie unter [Azure Files](https://azure.microsoft.com/services/storage/files/).
2.  Verbinden Sie Azure SSIS IR mit Azure Files, indem Sie Anmeldeinformationen einrichten, die mit der Windows-Authentifizierung verwendet werden. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Datenquellen und Dateifreigaben mit der Windows-Authentifizierung](ssis-azure-connect-with-windows-auth.md).
3.  Ändern Sie lokale Dateipfade in Ihren Paketen in UNC-Pfade, die auf Azure Files verweisen. Ändern Sie z.B. den Pfad `C:\abc.txt` in `\\<storage-account-name>.file.core.windows.net\<share-name>\abc.txt`.
