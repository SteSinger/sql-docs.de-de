---
title: Referenz zu azdata bdc hdfs status
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc hdfs status-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f3548feb06b05699750ce5c088c05c4e3cc67d57
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531791"
---
# <a name="azdata-bdc-hdfs-status"></a>azdata bdc hdfs status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata bdc hdfs status show](#azdata-bdc-hdfs-status-show) | HDFS-Dienststatus
## <a name="azdata-bdc-hdfs-status-show"></a>azdata bdc hdfs status show
HDFS-Dienststatus
```bash
azdata bdc hdfs status show [--resource -r] 
                            [--all -a]
```
### <a name="examples"></a>Beispiele
Ruft den Status des HDFS-Diensts ab
```bash
azdata bdc hdfs status show
```
Ruft den Status des HDFS-Diensts mit allen Instanzen ab
```bash
azdata bdc hdfs status show --all
```
Ruft den Status der Speicherressource im HDFS-Dienst ab
```bash
azdata bdc hdfs status show --resource storage-0
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--resource -r`
Ruft diese Ressource in diesem Dienst ab
#### `--all -a`
Zeigt alle Instanzen jeder Ressource im Dienst an
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zum Installieren des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern von SQL Server 2019](deploy-install-azdata.md).
