---
title: Erste Schritte mit SQL Server für Red Hat Enterprise Linux
titleSuffix: SQL Server
description: In diesem Schnellstart erfahren Sie, wie Sie SQL Server 2017 oder SQL Server 2019 unter Red Hat Enterprise Linux installieren und dann eine Datenbank mit „sqlcmd“ erstellen und abfragen.
author: VanMSFT
ms.author: vanto
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: b94ea0ef8956e7807f075da548ae817dc6a205df
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531372"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Schnellstart: Installieren von SQL Server und Erstellen einer Datenbank unter Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

In diesem Schnellstart installieren Sie SQL Server 2017 oder SQL Server 2019 unter Red Hat Enterprise Linux (RHEL). Danach stellen Sie eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

In diesem Schnellstart installieren Sie SQL Server 2019 unter Red Hat Enterprise Linux (RHEL) 7.3 oder höher. Danach stellen Sie eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

::: moniker-end

> [!TIP]
> Für dieses Tutorial sind Benutzereingaben und eine Internetverbindung erforderlich. Wenn Sie am [unbeaufsichtigten](sql-server-linux-setup.md#unattended) oder am [Offline](sql-server-linux-setup.md#offline)-Installationsverfahren interessiert sind, finden Sie weitere Informationen im [Leitfaden für die Installation von SQL Server für Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen einen Computer mit RHEL 7.3, 7.4, 7.5 oder 7.6 haben, der **mindestens 2 GB** Arbeitsspeicher hat.

Um Red Hat Enterprise Linux auf Ihrem eigenen Computer zu installieren, navigieren Sie zu [https://access.redhat.com/products/red-hat-enterprise-linux/evaluation](https://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Sie können auch virtuelle RHEL-Computer in Azure erstellen. Weitere Informationen finden Sie unter [Erstellen und Verwalten virtueller Linux-Computer mit der Azure-Befehlszeilenschnittstelle](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm). Verwenden Sie `--image RHEL` im Aufruf von `az vm create`.

Wenn Sie bereits eine CTP- oder RC-Version von SQL Server installiert haben, müssen Sie zuerst das alte Repository entfernen, bevor Sie die folgenden Schritte ausführen. Weitere Informationen finden Sie unter [Konfigurieren von Linux-Repositorys für SQL Server 2017 und 2019](sql-server-linux-change-repo.md).

Weitere Systemanforderungen finden Sie unter [Systemanforderungen für SQL Server für Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installieren von SQL Server

Um SQL Server unter RHEL zu konfigurieren, führen Sie in einem Terminal die folgenden Befehle aus, um das Paket **mssql-server** zu installieren:

1. Laden Sie die Konfigurationsdatei für das Microsoft SQL Server 2017 Red Hat-Repository herunter:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!TIP]
   > Wenn Sie SQL Server 2019 installieren möchten, müssen Sie stattdessen das Repository SQL Server 2019 registrieren. Verwenden Sie für Installationen von SQL Server 2019 den folgenden Befehl:
   >
   > ```bash
   > sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2019.repo
   > ```

2. Führen Sie die folgenden Befehle aus, um SQL Server zu installieren:

   ```bash
   sudo yum install -y mssql-server
   ```

3. Nachdem die Paketinstallation abgeschlossen ist, führen Sie **mssql-conf setup** aus, und befolgen Sie die Anweisungen, um das Systemadministratorkennwort festzulegen und Ihre Edition auszuwählen.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Für die folgenden SQL Server 2017-Editionen sind kostenlose Lizenzen verfügbar: Evaluation, Developer und Express.

   > [!NOTE]
   > Stellen Sie sicher, dass Sie ein sicheres Kennwort für das Systemadministratorkonto angeben (minimale Länge von 8 Zeichen, Groß-und Kleinbuchstaben, Ziffern und/oder nicht-alphanumerische Symbole).

4. Nachdem die Konfiguration abgeschlossen ist, überprüfen Sie, ob der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```

5. Um Remoteverbindungen zuzulassen, öffnen Sie den SQL Server Port in der Firewall unter RHEL. Der Standardport für SQL Server ist TCP 1433. Wenn Sie **FirewallD** für Ihre Firewall verwenden, können Sie die folgenden Befehle verwenden:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

Ab jetzt wird SQL Server auf Ihrem RHEL-Computer ausgeführt und ist einsatzbereit!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installieren von SQL Server

Um SQL Server unter RHEL zu konfigurieren, führen Sie in einem Terminal die folgenden Befehle aus, um das Paket **mssql-server** zu installieren:

1. Laden Sie die Konfigurationsdatei für das Microsoft SQL Server 2019 Red Hat-Repository herunter:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2019.repo
   ```

2. Führen Sie die folgenden Befehle aus, um SQL Server zu installieren:

   ```bash
   sudo yum install -y mssql-server
   ```

3. Nachdem die Paketinstallation abgeschlossen ist, führen Sie **mssql-conf setup** aus, und befolgen Sie die Anweisungen, um das Systemadministratorkennwort festzulegen und Ihre Edition auszuwählen.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Stellen Sie sicher, dass Sie ein sicheres Kennwort für das Systemadministratorkonto angeben (minimale Länge von 8 Zeichen, Groß-und Kleinbuchstaben, Ziffern und/oder nicht-alphanumerische Symbole).

4. Nachdem die Konfiguration abgeschlossen ist, überprüfen Sie, ob der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```

5. Um Remoteverbindungen zuzulassen, öffnen Sie den SQL Server Port in der Firewall unter RHEL. Der Standardport für SQL Server ist TCP 1433. Wenn Sie **FirewallD** für Ihre Firewall verwenden, können Sie die folgenden Befehle verwenden:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

Jetzt wird SQL Server 2019 auf Ihrem RHEL-Computer ausgeführt und ist einsatzbereit!

::: moniker-end

## <a id="tools"></a>Installieren der SQL Server-Befehlszeilentools

Um eine Datenbank zu erstellen, müssen Sie eine Verbindung mit einem Tool herstellen, das Transact-SQL-Anweisungen auf dem SQL Server-Computer ausführen kann. Mit den folgenden Schritten installieren Sie die SQL Server-Befehlszeilentools: [sqlcmd](../tools/sqlcmd-utility.md) und [bcp](../tools/bcp-utility.md).

1. Laden Sie die Konfigurationsdatei für das Microsoft Red Hat-Repository herunter.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Wenn Sie eine frühere Version von **mssql-tools** installiert hatten, entfernen Sie alle älteren unixODBC-Pakete.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Führen Sie die folgenden Befehle aus, um **mssql-tools** mit dem unixODBC-Entwicklerpaket zu installieren.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Fügen Sie für einfacheres Arbeiten `/opt/mssql-tools/bin/` zu Ihrer **PATH**-Umgebungsvariablen hinzu. Dadurch können Sie die Tools ausführen, ohne den vollständigen Pfad angeben zu müssen. Führen Sie die folgenden Befehle aus, um **PATH** sowohl für Anmeldesitzungen als auch für interaktive Sitzungen oder Sitzungen ohne Anmeldung zu ändern:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
