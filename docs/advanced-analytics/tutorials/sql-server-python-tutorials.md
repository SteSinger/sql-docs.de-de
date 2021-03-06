---
title: Python-Tutorials
description: In diesem Artikel werden die Python-Tutorials für SQL Server Machine Learning Services beschrieben. Erfahren Sie, wie Sie Python-Skripts ausführen. Erstellen und trainieren Sie Python-Modelle und stellen Sie diese in SQL Server bereit. Erfahren Sie mehr über lokale und Remotecomputekontexte. Erkunden Sie die Microsoft-Python-Pakete für Data Science und Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/04/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 80f714810acd8c04c80fe0b8abe5214a456f6dd6
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199408"
---
# <a name="python-tutorials-for-sql-server-machine-learning-services"></a>Python-Tutorials für SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel werden die Python-Tutorials und -Schnellstarts für [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) beschrieben.

+ Erfahren Sie, wie Sie Python-Skripts ausführen.
+ Erstellen und trainieren Sie Python-Modelle und stellen Sie diese in SQL Server bereit.
+ Erfahren Sie mehr über lokale und Remotecomputekontexte.
+ Erkunden Sie die Microsoft-Python-Pakete für Data Science und Machine Learning.

<a name="bkmk_pythontutorials"></a>

## <a name="python-tutorials"></a>Python-Tutorials

| Lernprogramm | und Beschreibung |
|-|-|
| [Vorhersagen für einen Skiverleih mit linearer Regression](python-ski-rental-linear-regression.md) | Verwenden Sie Python und die lineare Regression, um die Anzahl der Skiausleihen vorherzusagen. Bereiten Sie mithilfe von Notebooks in Azure Data Studio Daten vor und trainieren Sie das Modell, und verwenden Sie T-SQL für die Modellimplementierung. |
| [Kategorisierung von Kunden mit K-Means-Clustering](python-clustering-model.md) | Verwenden Sie Python, um ein K-Means-Clusteringmodell zum Kategorisieren von Kunden zu entwickeln und bereitzustellen. Bereiten Sie mithilfe von Notebooks in Azure Data Studio Daten vor und trainieren Sie das Modell, und verwenden Sie T-SQL für die Modellimplementierung. |
| [Erstellen eines Modells mithilfe von revoscalepy](use-python-revoscalepy-to-create-model.md) | Dieses Tutorial veranschaulicht, wie Sie Code von einem Python-Remoteclient ausführen, indem Sie SQL Server als Computekontext verwenden. Es wird ein Modell mithilfe von **rxLinMod** aus der **revoscalepy**-Bibliothek erstellt. |
| [Python-Datenanalysen für SQL-Entwickler](sqldev-in-database-python-for-sql-developers.md) | In dieser umfassenden exemplarischen Vorgehensweise wird veranschaulicht, wie Sie eine komplette Python-Lösung mithilfe von T-SQL erstellen. |

## <a name="python-quickstarts"></a>Python-Schnellstarts

Wenn SQL Server Machine Learning Services noch Neuland für Sie sind, können Sie auch die Python-Schnellstarts ausprobieren.

| Schnellstart | und Beschreibung |
|-|-|
| [„Hallo Welt“ in Python und SQL Server](quickstart-python-create-script.md) | Erfahren Sie mehr über die Grundlagen zum Abrufen von Python in T-SQL mithilfe von [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). |
| [Verarbeiten von Datentypen und Objekten mithilfe von Python in SQL Server](quickstart-python-data-structures.md) | Dieser Schnellstart zeigt, wie mit den Python-Pandas-Paketen in SQL Server Datenstrukturen verarbeitet werden. |
| [Erstellen und Bewerten eines Vorhersagemodells in Python](quickstart-python-train-score-model.md) | Hier sehen Sie, wie ein Python-Modell erstellt, trainiert und verwendet wird, um Vorhersagen aus neuen Daten zu treffen. |

## <a name="next-steps"></a>Nächste Schritte

+ [Was ist SQL Server Machine Learning Services (Python und R)?](../what-is-sql-server-machine-learning.md)
+ [Python-Erweiterung in SQL Server](../concepts/extension-python.md)