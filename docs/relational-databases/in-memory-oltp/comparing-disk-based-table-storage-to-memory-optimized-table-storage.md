---
title: Vergleichen des datenträgerbasierten Tabellenspeichers mit dem speicheroptimierten Tabellenspeicher | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: eacf443c-001a-445f-ad1c-5f5a45eca6f4
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 08b1cc612c8156b54db4cdea06184f3866f722ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951054"
---
# <a name="comparing-disk-based-table-storage-to-memory-optimized-table-storage"></a>Vergleichen des datenträgerbasierten Tabellenspeichers mit dem speicheroptimierten Tabellenspeicher
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  
  
|Kategorien|Datenträgerbasierte Tabelle|Dauerhafte speicheroptimierte Tabelle|  
|----------------|-----------------------|-------------------------------------|  
|DDL|Metadateninformationen werden in Systemtabellen in der primären Dateigruppe der Datenbank gespeichert, und der Zugriff erfolgt über Katalogsichten.|Metadateninformationen werden in Systemtabellen in der primären Dateigruppe der Datenbank gespeichert, und der Zugriff erfolgt über Katalogsichten.|  
|Struktur|Zeilen werden in 8-KB-Seiten gespeichert. In einer Seite werden nur Zeilen aus derselben Tabelle gespeichert.|Zeilen werden als einzelne Zeilen gespeichert. Es gibt keine Seitenstruktur. Zwei aufeinanderfolgende Zeilen in einer Datendatei können zu verschiedenen speicheroptimierten Tabellen gehören.|  
|Indizes|Indizes werden ähnlich wie Datenzeilen in einer Seitenstruktur gespeichert.|Nur die Indexdefinition (und nicht die Indexzeilen) werden dauerhaft gespeichert. Indizes werden im Arbeitsspeicher beibehalten und erneut generiert, wenn die speicheroptimierte Tabelle als Teil einer neu gestarteten Datenbank in den Arbeitsspeicher geladen wird. Da Indexzeilen nicht dauerhaft gespeichert werden, werden Indexänderungen nicht protokolliert.|  
|DML-Vorgang|Der erste Schritt besteht darin, die Seite zu suchen und dann in den Pufferpool zu laden.<br /><br /> Insert<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fügt die Zeile auf der Seite ein und berücksichtigt bei gruppierten Indizes die Zeilenreihenfolge.<br /><br /> DELETE<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sucht die zu löschende Zeile in der Seite und markiert sie als gelöscht.<br /><br /> Update<br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sucht die Zeile in der Seite. Das Update erfolgt für Nichtschlüsselspalten als direkte Aktualisierung. Ein Schlüsselspaltenupdate setzt sich aus Löschung und Einfügung zusammen.<br /><br /> Nachdem der DML-Vorgang abgeschlossen wurde, werden die betroffenen Seiten im Rahmen der Pufferpoolrichtlinie, des Prüfpunkts oder des Transaktionscommits für minimal protokollierte Vorgänge auf den Datenträger geleert. Sowohl Lese- als auch Schreibvorgänge in Seiten führen zu unnötigen E/A-Vorgängen.|Bei speicheroptimierten Tabellen werden DML-Vorgänge direkt im Arbeitsspeicher ausgeführt, da sich die Daten im Arbeitsspeicher befinden. Es gibt einen Hintergrundthread, der die Protokolldatensätze für speicheroptimierte Tabellen liest und dauerhaft in Daten- und Änderungsdateien speichert. Ein Update generiert eine neue Zeilenversion. Ein Update wird jedoch als Vorgang protokolliert, der aus einer Löschung und einer Einfügung besteht.|  
|Datenfragmentierung|Bei der Datenbearbeitung werden Daten fragmentiert, was zu teilweise gefüllten und logisch aufeinanderfolgenden Seiten führt, die auf dem Datenträger nicht zusammenhängend sind. Dadurch wird die Datenzugriffsleistung beeinträchtigt und eine Datendefragmentierung erforderlich.|Da speicheroptimierte Daten nicht in Seiten gespeichert werden, tritt keine Datenfragmentierung auf. Während Zeilen im Lauf der Zeit aktualisiert und gelöscht werden, müssen die Daten- und Änderungsdateien jedoch komprimiert werden. Dies geschieht mithilfe eines MERGE-Hintergrundthreads auf Grundlage einer Mergerichtlinie.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen und Verwalten von Speicher für speicheroptimierte Objekte](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
