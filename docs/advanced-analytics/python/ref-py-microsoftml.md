---
title: Python-Paket für microsoftml
description: Einführung der Microsoft Machine Learning-Algorithmen und -Modelle für Python in Bezug auf Machine Learning-Workloads in SQL Server.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7ecbfd2edd20a312fc8a6d451938f1407585ded5
ms.sourcegitcommit: b4ad3182aa99f9cbfd15f4c3f910317d6128a2e5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73706954"
---
# <a name="microsoftml-python-module-in-sql-server"></a>microsoftml (Python-Modul in SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**microsoftml** ist ein mit Python35 kompatibles Modul von Microsoft, das leistungsstarke Machine Learning-Algorithmen bereitstellt. Sie enthält Funktionen für Training, Transformationen, Bewertung, Text- und Bildanalyse sowie Featureextraktion zum Ableiten von Werten aus vorhandenen Daten.

Die Machine Learning-APIs wurden von Microsoft für interne Machine Learning-Anwendungen entwickelt und im Laufe der Jahre so optimiert, dass sie bei Big Data eine hohe Leistung durch Verarbeitung auf Mehrkernprozessoren und schnelles Datenstreaming unterstützen. Dieses Paket basiert auf dem Python-Äquivalent der R-Version [MicrosoftML](../r/ref-r-microsoftml.md), die ähnliche Funktionen aufweist. 

## <a name="full-reference-documentation"></a>Vollständige Referenzdokumentation

Die **microsoftml**-Bibliothek wird in mehreren Microsoft-Produkten bereitgestellt. Die Verwendung ist jedoch immer identisch, unabhängig davon, ob Sie die Bibliothek in SQL Server oder einem anderen Produkt abrufen. Aus diesem Grund wird die [Dokumentation für einzelne microsoftml-Funktionen](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) nur an einer Stelle in der [Python-Referenz](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) für Microsoft Machine Learning Server veröffentlicht. Abweichungen durch produktspezifisches Verhalten finden Sie ggf. auf der Hilfeseite der Funktion.

## <a name="versions-and-platforms"></a>Versionen und Plattformen

Das **microsoftml**-Modul basiert auf Python 3.5 und ist nur verfügbar, wenn Sie eines der folgenden Microsoft-Produkte oder Downloads installieren:

+ [SQL Server-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md)
+ [Microsoft Machine Learning Server 9.2.0 oder höher](https://docs.microsoft.com/machine-learning-server/)
+ [Python-Client-Bibliotheken für einen Data Science-Client](setup-python-client-tools-sql.md)

> [!NOTE]
> Vollständige Produktversionen sind in SQL Server 2017 nur unter Windows verfügbar. In [SQL Server 2019](../../linux/sql-server-linux-setup-machine-learning.md) wird **microsoftml** sowohl unter Windows als auch unter Linux unterstützt.

## <a name="package-dependencies"></a>Paketabhängigkeiten

Die Algorithmen folgender Elemente hängen in **microsoftml** von [revoscalepy](ref-py-revoscalepy.md) ab:

+ Datenquellenobjekte: Die von **microsoftml**-Funktionen genutzten Daten werden mithilfe von **revoscalepy**-Funktionen erstellt.
+ Remotecomputing (das Verschieben der Funktionsausführung in eine SQL Server-Remoteinstanz): Die **revoscalepy**-Bibliothek stellt Funktionen zum Erstellen und Aktivieren eines Remotecomputekontexts für SQL Server bereit.

In den meisten Fällen werden die Pakete bei der Verwendung von **microsoftml** zusammen geladen.

## <a name="functions-by-category"></a>Funktionen nach Kategorie

In diesem Abschnitt werden die Funktionen nach Kategorien aufgelistet, damit Sie einen Überblick über die Verwendung der einzelnen Funktionen erhalten. Im [Inhaltsverzeichnis](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference) können Sie in alphabetischer Reihenfolge nach den Funktionen suchen.

## <a name="1-training-functions"></a>1: Trainingsfunktionen

| Funktion | und Beschreibung |
|----------|-------------|
|[microsoftml.rx_ensemble](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-ensemble) | Trainiert ein Modellensemble |
|[microsoftml.rx_fast_forest](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-forest)  | Zufällige Gesamtstruktur |
|[microsoftml.rx_fast_linear](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-linear) | Lineares Modell mit doppeltem stochastischen Koordinatenanstieg |
|[microsoftml.rx_fast_trees](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-fast-trees) | Verstärkte Entscheidungsbäume |
|[microsoftml.rx_logistic_regression](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-logistic-regression) | Logistische Regression |
|[microsoftml.rx_neural_network](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-neural-network) | Neuronales Netzwerk |
|[microsoftml.rx_oneclass_svm](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-oneclass-svm) | Erkennt Anomalien |

<a name="ml-transforms"></a>

## <a name="2-transform-functions"></a>2: Transformationsfunktionen

### <a name="categorical-variable-handling"></a>Behandeln von kategorischen Variablen

| Funktion | und Beschreibung |
|----------|-------------|
|[microsoftml.categorical](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical) | Konvertiert Textspalten in Kategorien |
|[microsoftml.categorical_hash](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/categorical-hash) | Erstellt einen Hash für eine Textspalte und konvertiert diese in Kategorien |

### <a name="schema-manipulation"></a>Schemabearbeitung

| Funktion | und Beschreibung |
|----------|-------------|
|[microsoftml.concat](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/concat) | Verkettet mehrere Spalten zu einem einzelnen Vektor |
|[microsoftml.drop_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/drop-columns) | Löscht Spalten aus einem Dataset |
|[microsoftml.select_columns](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/select-columns) | Behält Spalten eines Datasets bei |


### <a name="variable-selection"></a>Variablenauswahl

| Funktion | und Beschreibung |
|----------|-------------|
|[microsoftml.count_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/count-select) |Wählt Funktionen basierend auf Anzahlen aus |
|[microsoftml.mutualinformation_select](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/mutualinformation-select) | Wählt Funktionen auf der Grundlage von gegenseitigen Informationen aus |


### <a name="text-analytics"></a>Textanalyse

| Funktion | und Beschreibung |
|----------|-------------|
|[microsoftml.featurize_text](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-text) | Konvertiert Textspalten in numerische Funktionen |
|[microsoftml.get_sentiment](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/get-sentiment) | Stimmungsanalyse |


### <a name="image-analytics"></a>Bildanalyse 

| Funktion | und Beschreibung |
|----------|-------------|
|[microsoftml.load_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/load-image) | Lädt ein Bild |
|[microsoftml.resize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/resize-image) | Ändert die Größe eines Bilds |
|[microsoftml.extract_pixels](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/extract-pixels) | Extrahiert Pixel aus einem Bild |
|[microsoftml.featurize_image](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/featurize-image) | Konvertiert ein Bild in Features |

### <a name="featurization-functions"></a>Featurefunktionen

| Funktion | und Beschreibung |
|----------|-------------|
|[microsoftml.rx_featurize](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-featurize) | Datentransformation für Datenquellen |

<a name="ml-scoring"></a>

## <a name="3-scoring-functions"></a>3: Bewertungsfunktionen

| Funktion | und Beschreibung |
|----------|-------------|
|[microsoftml.rx_predict](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/rx-predict) | Nimmt Bewertungen unter Verwendung eines Microsoft Machine Learning-Modells vor |

## <a name="how-to-call-microsoftml"></a>Vorgehensweise beim Abrufen von microsoftml

Funktionen in **microsoftml** können in Python-Code aufgerufen werden, der in gespeicherten Prozeduren gekapselt ist. Die meisten Entwickler erstellen **microsoftml**-Lösungen lokal, und migrieren den fertigen Python-Code anschließend als Bereitstellungsübung in gespeicherte Prozeduren.

Das **microsoftml**-Paket für Python ist standardmäßig installiert, im Gegensatz zu **revoscalepy** wird es jedoch nicht standardmäßig geladen, wenn Sie eine Python-Sitzung mit den mit SQL Server installierten Python-Dateien starten.

Importieren Sie zunächst das **microsoftml**-Paket, und importieren Sie anschließend **revoscalepy**, wenn Sie Remotecomputekontexte oder zugehörige Verbindungs- oder Datenquellenobjekte verwenden müssen. Verweisen Sie dann auf die einzelnen Funktionen, die Sie benötigen.

```python
from microsoftml.modules.logistic_regression.rx_logistic_regression import rx_logistic_regression
from revoscalepy.functions.RxSummary import rx_summary
from revoscalepy.etl.RxImport import rx_import_datasource
```

## <a name="see-also"></a>Siehe auch

+ [Python-Tutorials](../tutorials/sql-server-python-tutorials.md)
+ [Tutorial: Einbetten von Python-Code in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Python-Referenz (Microsoft Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/python-reference/introducing-python-package-reference)

