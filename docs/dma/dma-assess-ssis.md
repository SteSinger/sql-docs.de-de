---
title: Erstellen einer SSIS-Migrations Bewertung mit dem Datenmigrations-Assistent
description: Erfahren Sie, wie Sie mit Datenmigrations-Assistent einen lokalen SQL Server Integration Service (SSIS) vor der Migration zu einer Azure SQL-Datenbank oder einer verwalteten Azure SQL-Datenbank-Instanz bewerten.
ms.date: 08/23/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: chugugrace
ms.author: chugu
ms.custom: seo-lt-2019
ms.openlocfilehash: 1652d5eec9d6419e7b39f96a8b854eef8651bf26
ms.sourcegitcommit: 7183735e38dd94aa3b9bab2b73ccab54c916ff86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74687157"
---
# <a name="perform-a-sql-server-integration-service-migration-assessment-with-data-migration-assistant"></a>Durchführen einer SQL Server Integration Service-Migrations Bewertung mit Datenmigrations-Assistent

## <a name="prerequisites"></a>Voraussetzungen

Zum Bewerten der SSIS-Pakete (SQL Server Integration Service) müssen die folgenden Komponenten mit Datenmigrations-Assistent installiert werden:

- SQL Server Integrations Dienst mit der gleichen Version wie die SSIS-Pakete zur Bewertung.
- Azure Feature Pack oder andere Komponenten von Drittanbietern, wenn diese Komponenten von SSIS-Paketen bewertet werden.  

DMA muss mit **Administrator** Zugriff ausgeführt werden, um SSIS-Pakete im Paket Speicher zu bewerten.

## <a name="performance-assessments"></a>Leistungsbewertungen

Die folgenden schrittweisen Anweisungen unterstützen Sie bei der ersten Bewertung der Migration von SSIS-Paketen (SQL Server Integration Service) zu Azure SQL-Datenbank oder einer verwalteten Azure SQL-Datenbank-Instanz mithilfe von Datenmigrations-Assistent.

## <a name="create-an-assessment"></a>Erstellen einer Bewertung

1. Wählen Sie das Symbol **neu** (+) aus, und wählen Sie dann den Projekttyp **Bewertung** als **Integrations Dienst**aus.

1. Legen Sie den Typ von Quell- und Zielserver fest.

    Wählen Sie die Quelle als **SQL Server**aus, und legen Sie den Ziel Servertyp als **Azure SQL-Datenbank** oder **verwaltete Azure SQL-Datenbank-Instanz**fest.

1. Klicken Sie auf **Erstellen**.

    ![Bewertung erstellen](media/dma-assess-ssis/dma-assess-ssis-create.png)

## <a name="connect-to-a-server"></a>Verbinden mit einem Server

1. Befolgen Sie die Standardoption, und klicken Sie auf **weiter** , um **Quellen auszuwählen**.
1. Geben Sie den SQL Server-Instanznamen ein, wählen Sie den Authentifizierungstyp und die richtigen Verbindungs Eigenschaften
1. Optionale Geben Sie einen Ordner Pfad ein, der SSIS-Pakete enthält.
1. Optionale Geben Sie ggf. das Paket Verschlüsselungs Kennwort ein.
1. Klicken Sie auf Verbindung mit dem SQL-Quell Server **herstellen** .
  ![Quelle hinzufügen](media/dma-assess-ssis/dma-assess-ssis-addsource.png)

## <a name="add-sources-to-assess"></a>Hinzufügen von Quellen zur Bewertung

1. Wählen Sie die zu Bewertungs baren SSIS-Paket Speichertypen aus, und klicken Sie dann auf **Hinzufügen**.
![Quelle hinzufügen](media/dma-assess-ssis/dma-assess-ssis-addsource-type.png)
1. Wählen Sie **Quellen hinzufügen** aus, um das Menü verbindungsflyout zu öffnen, wenn Sie mehrere Ordner bewerten müssen.
1. Klicken Sie auf **Start Assessment**.
  ![Bewertung starten](media/dma-assess-ssis/dma-assess-ssis-assess.png)

## <a name="view-results"></a>Anzeigen der Ergebnisse

Die Kategorie Kompatibilitätsprobleme bietet teilweise unterstützte oder nicht unterstützte Funktionen, die die Migration von lokalen SSIS-Paketen zu Azure-SSIS Integration Runtime blockieren. Anschließend werden Empfehlungen bereitstellen, die Ihnen helfen, diese Probleme zu beheben.

![Anzeigen der Ergebnisse](media/dma-assess-ssis/dma-assess-ssis-result.png)

## <a name="next-steps"></a>Nächste Schritte

- [Migrieren von lokalen SSIS-Workloads zu SSIS in der ADF-Übersicht](https://docs.microsoft.com/azure/data-factory/scenario-ssis-migration-overview)
- [Migrieren von SQL Server Integration Services Paketen zu einer verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages-managed-instance)
- [Erneutes Bereitstellen von SQL Server Integration Services-Paketen für Azure SQL-Datenbank](https://docs.microsoft.com/azure/dms/how-to-migrate-ssis-packages)
