---
title: Konfigurieren der Schwellenwerte für Bereinigung und Abgleich
description: Erfahren Sie, wie Sie Schwellenwerte konfigurieren, die während der computerunterstützten Bereinigung und Abgleich von Aktivitäten in SQL Server Data Quality Services (DQS) verwendet werden.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.admin.config.general.f1
helpviewer_keywords:
- cleansing,threshold value
- cleansing threshold values
- matching,threshold value
ms.assetid: d2305409-7115-45a4-8f60-1213c0a47368
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 4fcbc8e4e6d6a9c1df07d8e1b1aa68c08c162817
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75557892"
---
# <a name="configure-threshold-values-for-cleansing-and-matching---data-quality-services-dqs"></a>Konfigurieren der Schwellenwerte für Bereinigung und Abgleich: Data Quality Services (DQS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Thema wird beschrieben, wie Schwellenwerte, die während den computerunterstützten Bereinigungs- und Abgleichsaktivitäten in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) verwendet werden, konfiguriert werden.  
  
##  <a name="BeforeYouBegin"></a>Bevor Sie beginnen  
  
###  <a name="Security"></a>Sicherung  
  
####  <a name="Permissions"></a>Griff  
 Sie müssen die Rolle „dqs_administrator“ in der DQS_MAIN-Datenbank haben, um diese Schwellenwerte zu konfigurieren.  
  
##  <a name="Configure"></a>Konfigurieren der Schwellenwerte  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Führen Sie die Data Quality-Client Anwendung](../data-quality-services/run-the-data-quality-client-application.md)aus.  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Konfiguration**.  
  
3.  Klicken Sie anschließend auf die Registerkarte **Allgemeine Einstellungen** . Auf dieser Registerkarte können Sie Schwellenwerte für die Bereinigung und abgleichsaktivitäten angeben.  
  
4.  Um Schwellenwerte für die Bereinigungsaktivität anzugeben, geben Sie entsprechende Werte in den folgenden Feldern im Bereich **Interaktive Bereinigung** an:  
  
    -   Minimal **Ergebnis für Vorschläge**: das minimale Ergebnis oder der Vertrauensgrad, der von DQS zum vorschlagen von Ersetzungen für einen Wert während des computerunterstützten Bereinigungs Prozesses verwendet wird. Geben Sie einen Wert in der Dezimalnotation des entsprechenden Prozentwerts ein. Geben Sie beispielsweise 0,75 für 75 % ein. Dieser Wert sollte kleiner oder gleich dem Wert sein, der im Feld **Mindestergebnis für automatische Korrekturen** angegeben wurde. Der Standardwert ist 0,7.  
  
    -   Minimale **Bewertung für automatische Korrekturen**: das minimale Ergebnis oder der Vertrauensgrad, der von DQS zum automatischen Korrigieren eines Werts während des computergestützten Bereinigungs Prozesses verwendet wird. Geben Sie einen Wert in der Dezimalnotation des entsprechenden Prozentwerts ein. Geben Sie beispielsweise 0,9 für 90 % ein. Der Standardwert ist 0,8.  
  
5.  Um einen Schwellenwert für die Abgleichsaktivität anzugeben, geben Sie einen Wert im Feld **Mindestergebnis für Datensätze** unter dem Bereich **Abgleich** an. Dieser Wert gibt das minimale Ergebnis für einen Datensatz an, das als Übereinstimmung mit einem anderen Datensatz betrachtet werden soll. Der Standardwert ist 80 %.  
  
6.  Klicken Sie auf **Schließen**.  
  
  
