---
title: Installieren von Python-Paketen mit pip
description: Erfahren Sie, wie Sie mit Python-pip neue Python-Pakete auf einer Instanz von SQL Server Machine Learning Services installieren.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 2e3452a6aad04d0d524e4eb0e6bd473fd39a2bf7
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542150"
---
# <a name="install-python-packages-with-sqlmlutils"></a>Installieren von Python-Paketen mit sqlmlutils

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie Funktionen im [**sqlmlutils**](https://github.com/Microsoft/sqlmlutils)-Paket verwenden, um neue Python-Pakete in einer Instanz von SQL Server Machine Learning Services zu installieren. Die von Ihnen installierten Pakete können verwendet werden, um Python-Skripts innerhalb einer Datenbank mithilfe der T-SQL-Anweisung [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) auszuführen.

Weitere Informationen zu dem Paketspeicherort und Installationspfaden finden Sie unter [Abrufen von Paketinformationen für Python](../package-management/python-package-information.md).

> [!NOTE]
> Der Python-Standardbefehl `pip install` wird für das Hinzufügen von Python-Paketen in SQL Server nicht empfohlen. Verwenden Sie stattdessen **sqlmlutils**, wie in diesem Artikel beschrieben.

## <a name="prerequisites"></a>Voraussetzungen

+ [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) muss mit der Python-Sprachoption installiert sein.

+ Installieren Sie [Python](https://www.python.org/) auf dem Clientcomputer, den Sie mit SQL Server verbinden. Möglicherweise möchten Sie auch eine Python-Entwicklungsumgebung wie [Visual Studio Code](https://code.visualstudio.com/download) mit der [Python-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-python.python) verwenden. 

+ Installieren Sie [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) oder [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms) (SSMS) auf dem Clientcomputer, den Sie zum Herstellen der Verbindung mit SQL Server verwenden. Sie können auch andere Datenbankverwaltungs- oder Abfragetools verwenden, doch dieser Artikel geht von Azure Data Studio oder SSMS aus.

### <a name="other-considerations"></a>Weitere Überlegungen

+ Die Pakete müssen Python 3.5-kompatibel sein und unter Windows ausgeführt werden.

+ Die Python-Paketbibliothek befindet sich im Ordner „Programme“ Ihrer SQL Server-Instanz, und für die Installation in diesem Ordner sind standardmäßig Administratorberechtigungen erforderlich. Weitere Informationen finden Sie unter [Speicherort der Paketbibliothek](../package-management/python-package-information.md#default-python-library-location).

+ Die Paketinstallation erfolgt pro Instanz. Wenn Sie über mehrere Instanzen von Machine Learning Services verfügen, müssen Sie das Paket zu jeder hinzufügen.

+ Bevor Sie ein Paket hinzufügen, sollten Sie überprüfen, ob das Paket für die SQL Server-Umgebung geeignet ist.

  + Es wird empfohlen, Python innerhalb der Datenbank für Tasks zu verwenden, die von einer engen Integration in die Datenbank-Engine profitieren, z. B. maschinelles Lernen, anstatt von Tasks, die einfache Datenbankabfragen ausführen.

  + Wenn Sie Pakete hinzufügen, deren Ausführung auf dem Server sehr rechenintensiv ist, wird die Leistung beeinträchtigt.

  + In einer gesicherten SQL Server-Umgebung sollten Sie Folgendes vermeiden:
    + Pakete, für die Netzwerkzugriff erforderlich ist
    + Pakete, für die erhöhte Zugriffsrechte für das Dateisystem erforderlich sind
    + Pakete, die für die Webentwicklung oder andere Aufgaben verwendet werden und nicht von der Ausführung in SQL Server profitieren

## <a name="install-sqlmlutils-on-the-client-computer"></a>Installieren von sqlmlutils auf dem Clientcomputer

Zur Verwendung von **sqlmlutils** müssen Sie dies zunächst auf dem Clientcomputer installieren, den Sie mit SQL Server verbinden.

1. Laden Sie die neueste **sqlmlutils**-ZIP-Datei von https://github.com/Microsoft/sqlmlutils/tree/master/Python/dist auf den Clientcomputer herunter. Entpacken Sie die Datei jedoch nicht.

1. Öffnen Sie eine **Eingabeaufforderung**, und führen Sie den folgenden Befehl aus, um das **sqlmlutils**-Paket zu installieren. Ersetzen Sie den vollständigen Pfad zur **sqlmlutils**-ZIP-Datei, die Sie heruntergeladen haben. In diesem Beispiel wird davon ausgegangen, dass dies die heruntergeladene Datei ist: `c:\temp\sqlmlutils_0.6.0.zip`.

   ```console
   pip install --upgrade --upgrade-strategy only-if-needed c:\temp\sqlmlutils_0.6.0.zip
   ```

## <a name="add-a-python-package-on-sql-server"></a>Hinzufügen eines Python-Pakets in SQL Server

Im folgenden Beispiel fügen Sie in SQL Server das Paket [text-tools](https://pypi.org/project/text-tools/) hinzu.

### <a name="add-the-package-online"></a>Hinzufügen des Pakets über eine Internetverbindung

Wenn der Clientcomputer, mit dem Sie sich mit SQL Server verbinden, über einen Internetzugang verfügt, können Sie mit **sqlmlutils** das Paket **text-tools** und alle Abhängigkeiten über das Internet suchen. Anschließend können Sie das Paket per Remotezugriff in einer SQL Server-Instanz installieren.

1. Öffnen Sie auf dem Clientcomputer **Python** oder eine Python-Umgebung.

1. Verwenden Sie die folgenden Befehle, um das Paket **text-tools** zu installieren. Ersetzen Sie die eigenen Verbindungsdaten der SQL Server-Datenbank. (Wenn Sie keine Windows-Authentifizierung verwenden, fügen Sie die Parameter `uid` und `pwd` hinzu.)

   ```python
   import sqlmlutils
   connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase")
   sqlmlutils.SQLPackageManager(connection).install("text-tools")
   ```

### <a name="add-the-package-offline"></a>Hinzufügen des Pakets ohne Internetverbindung

Wenn der Clientcomputer, mit dem Sie sich mit SQL Server verbinden, über keine Internetverbindung verfügt, können Sie mit **pip** auf einem Computer mit Internetzugang das Paket und alle abhängigen Pakete in einen lokalen Ordner herunterladen. Anschließend kopieren Sie den Ordner auf den Clientcomputer, auf dem Sie das Paket offline installieren können.

#### <a name="on-a-computer-with-internet-access"></a>Auf einem Computer mit Internetzugriff

1. Öffnen Sie eine **Eingabeaufforderung**, und führen Sie den folgenden Befehl aus, um einen lokalen Ordner zu erstellen, der das Paket **text-tools** enthält. In diesem Beispiel wird der Ordner `c:\temp\text-tools` erstellt.

   ```console
   pip download text-tools -d c:\temp\text-tools
   ```

1. Kopieren Sie den `text-tools`-Ordner auf den Clientcomputer. Im folgenden Beispiel wird davon ausgegangen, dass Sie ihn nach `c:\temp\packages\text-tools` kopiert haben.

#### <a name="on-the-client-computer"></a>Auf dem Clientcomputer

Verwenden Sie **sqlmlutils**, um jedes Paket (WHL-Datei) aus dem lokalen Ordner zu installieren, der von **pip** erstellt wurde. Es spielt keine Rolle, in welcher Reihenfolge Sie die Pakete installieren.

In diesem Beispiel weist **text-tools** keine Abhängigkeiten auf, sodass es nur eine Datei aus dem Ordner `text-tools` gibt, die Sie installieren können. Im Gegensatz dazu hat ein Paket wie **scikit-plot** elf Abhängigkeiten, sodass Sie zwölf Dateien im Ordner finden würden (das Paket **scikit-plot** und die elf abhängigen Pakete), die Sie jeweils installieren würden.

Führen Sie folgendes Python-Skript aus. Ersetzen Sie den tatsächlichen Dateipfad und Paketnamen sowie die eigenen Verbindungsdaten der SQL Server-Datenbank. (Wenn Sie keine Windows-Authentifizierung verwenden, fügen Sie die Parameter `uid` und `pwd` hinzu.) Wiederholen Sie die `sqlmlutils.SQLPackageManager`-Anweisung für jede Paketdatei im Ordner.

```python
import sqlmlutils
connection = sqlmlutils.ConnectionInfo(server="yourserver", database="yourdatabase")
sqlmlutils.SQLPackageManager(connection).install("c:/temp/packages/text-tools/text_tools-1.0.0-py3-none-any.whl")
```

## <a name="use-the-package-in-sql-server"></a>Verwenden des Pakets in SQL Server

Sie können das Paket jetzt in einem Python-Skript in SQL Server verwenden. Beispiel:

```python
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
from text_tools.finders import find_best_string
corpus = "Lorem Ipsum text"
query = "Ipsum"
first_match = find_best_string(query, corpus)
print(first_match)
  '
```

## <a name="remove-the-package-from-sql-server"></a>Entfernen eines Pakets aus SQL Server

Wenn Sie das Paket **text-tools** entfernen möchten, verwenden Sie den folgenden Python-Befehl auf dem Clientcomputer und die Verbindungsvariablen, die Sie zuvor definiert haben.

```python
sqlmlutils.SQLPackageManager(connection).uninstall("text-tools")
```

## <a name="see-also"></a>Siehe auch

+ Informationen zu Python-Paketen, die in SQL Server Machine Learning Services installiert sind, finden Sie unter [Abrufen von Paketinformationen für Python](../package-management/python-package-information.md).

+ Informationen zum Installieren von R-Paketen in SQL Server Machine Learning Services finden Sie unter [Installieren neuer R-Pakete auf SQL Server](../r/install-additional-r-packages-on-sql-server.md).
