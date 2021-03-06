---
title: Ausführen eines SSIS-Pakets über die Eingabeaufforderung | Microsoft-Dokumentation
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 964fdf4d4abb58d7baf27ee9e2f8b6900a7d0bbb
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2019
ms.locfileid: "71295712"
---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>Ausführen eines SSIS-Pakets über die Eingabeaufforderung mit „DTExec.exe“

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


In diesem Schnellstart wird gezeigt, wie Sie ein SSIS-Paket über die Eingabeaufforderung ausführen, indem Sie `DTExec.exe` mit den entsprechenden Parametern ausführen.

> [!NOTE]
> Die in diesem Artikel beschriebene Methode wurde nicht Paketen getestet, die für einen Azure SQL-Datenbank-Server bereitgestellt werden.

Weitere Informationen zu `DTExec.exe` finden Sie unter [dtexec Utility](https://docs.microsoft.com/sql/integration-services/packages/dtexec-utility) (Hilfprogramm dtexec).

## <a name="supported-platforms"></a>Unterstützte Plattformen

Mithilfe der Informationen in diesem Schnellstart können Sie auf den folgenden Plattformen SSIS-Pakete ausführen:

-   SQL Server unter Windows

Die in diesem Artikel beschriebene Methode wurde nicht Paketen getestet, die für einen Azure SQL-Datenbank-Server bereitgestellt werden. Weitere Informationen zum Bereitstellen und Ausführen von Paketen in Azure finden Sie unter [Migration von SQL Server Integration Services-Workloads in die Cloud per Lift & Shift](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Anhand der Informationen in diesem Schnellstart können Sie unter Linux keine SSIS-Pakete ausführen. Weitere Informationen zum Ausführen von Paketen finden Sie unter [Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS](../linux/sql-server-linux-migrate-ssis.md).

## <a name="run-a-package-with-dtexec"></a>Ausführen eines Pakets mit dtexec

Wenn sich der Ordner, der `DTExec.exe` enthält, nicht in Ihrer Umgebungsvariable `path` befindet, müssen Sie möglicherweise mit dem Befehl `cd` in das Verzeichnis wechseln. Bei SQL Server 2017 lautet dieser Ordner in der Regel `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`.

Mit den im folgenden Beispiel verwendeten Parameterwerten führt das Programm das Paket im angegebenen Ordnerpfad auf dem SSIS-Server aus – d.h. dem Server, der die SSIS-Katalogdatenbank (SSISDB) hostet. Der `/Server`-Parameter stellt den Namen des Servers bereit. Das Programm stellt als aktueller Benutzer eine Verbindung mit der integrierten Windows-Authentifizierung her. Um die SQL-Authentifizierung zu verwenden, geben Sie die entsprechenden Werte für die Parameter `/User` und `Password` an.

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Führen Sie `DTExec.exe` aus, und geben Sie mindestens für die Parameter `ISServer` und `Server` Werte an, wie im folgenden Beispiel gezeigt:

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>Nächste Schritte
- Erfahren Sie mehr über weitere Möglichkeiten, ein Paket auszuführen.
    - [Run an SSIS package with SSMS](./ssis-quickstart-run-ssms.md) (Ausführen eines SSIS-Pakets mit SSMS)
    - [Run an SSIS package with Transact-SQL (SSMS) (Ausführen eines SSIS-Pakets mit Transact-SQL [SSMS])](./ssis-quickstart-run-tsql-ssms.md)
    - [Run an SSIS package with Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md) (Ausführen eines SSIS-Pakets mit Transact-SQL [VS Code])
    - [Ausführen eines SSIS-Pakets mit PowerShell](ssis-quickstart-run-powershell.md)
    - [Run an SSIS package with C#](./ssis-quickstart-run-dotnet.md) (Ausführen eines SSIS-Pakets mit C#) 
