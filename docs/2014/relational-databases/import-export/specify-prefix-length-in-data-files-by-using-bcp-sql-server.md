---
title: Angeben der Präfixlänge in Datendateien mittels bcp (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], prefix length
- prefix length [SQL Server]
- lengths [SQL Server], prefix characters
- data formats [SQL Server], prefix length
ms.assetid: ce32dd1a-26f1-4f61-b9fa-3f1feea9992e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5d91c82d892888d2e6edde5615ba05a2a9ebf3c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011755"
---
# <a name="specify-prefix-length-in-data-files-by-using-bcp-sql-server"></a>Angeben der Präfixlänge in Datendateien mittels bcp (SQL Server)
  Als kompakteste Form der Dateispeicherung beim Massenexportieren von Daten im nativen Format in eine Datendatei setzt der Befehl **bcp** mindestens ein Zeichen, das auf die Länge des Felds hinweist, vor jedes Feld. Diese Zeichen werden als *Längenpräfixzeichen*bezeichnet.  
  
## <a name="the-bcp-prompt-for-prefix-length"></a>bcp-Eingabeaufforderung für die Präfixlänge  
 Wenn ein interaktiver **bcp** -Befehl die Option **in** oder **out** , jedoch keinen Formatdateischalter (**-f**) bzw. keinen Datenformatschalter (**-n**, **-c**, **-w**oder **-N**) enthält, fordert der Befehl wie folgt zur Eingabe der Präfixlänge für jedes Datenfeld auf:  
  
 `Enter prefix length of field <field_name> [<default>]:`  
  
 Wenn Sie 0 angeben, werden Sie von **bcp** zur Eingabe der Länge des Felds (für einen Zeichendatentyp) oder eines Feldabschlusszeichens (für einen nativen Nicht-Zeichentyp) aufgefordert.  
  
> [!NOTE]  
>  Nachdem Sie interaktiv alle Felder in einem **bcp**-Befehl angegeben haben, werden Sie vom Befehl dazu aufgefordert, Ihre Antworten für die einzelnen Felder in einer Nicht-XML-Formatdatei zu speichern. Weitere Informationen zu Nicht-XML-Formatdateien finden Sie unter [Nicht-XML-Formatdateien &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="overview-of-prefix-length"></a>Übersicht über die Präfixlänge  
 Zum Speichern der Präfixlänge eines Felds muss eine ausreichende Anzahl von Bytes vorhanden sein, um die maximale Länge des Felds darzustellen. Die erforderliche Anzahl von Byte hängt auch ab vom Dateispeichertyp, der NULL-Zulässigkeit einer Spalte und davon, ob die Daten in der Datendatei im systemeigenen Format oder im Zeichenformat gespeichert werden. Beispielsweise erfordert der Datentyp `text` oder `image` vier Präfixzeichen, um die Feldlänge zu speichern, während der Datentyp `varchar` zwei Zeichen erfordert. In der Datendatei werden diese Längenpräfixzeichen im internen binären Datenformat von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gespeichert.  
  
> [!IMPORTANT]  
>  Beim Verwenden des systemeigenen Formats sollten Sie anstelle von Feldabschlusszeichen eher Längenpräfixe verwenden. Systemeigene Formatdaten können zu Konflikten mit Abschlusszeichen führen, weil eine Datendatei im systemeigenen Format im internen binären Datenformat von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert wird.  
  
##  <a name="PrefixLengthsExport"></a> Präfixlängen für den Massenexport  
  
> [!NOTE]  
>  Der Standardwert, der beim Exportieren eines Felds an der Eingabeaufforderung für die Präfixlänge bereitgestellt wird, bezeichnet die effizienteste Präfixlänge für das Feld.  
  
 NULL-Werte werden als leeres Feld dargestellt. Um anzuzeigen, dass das Feld leer ist (NULL darstellt), enthält das Feldpräfix den Wert -1. Das heißt, es ist mindestens 1 Byte erforderlich. Beachten Sie, dass eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellenspalte, wenn sie NULL-Werte zulässt, je nach Dateispeichertyp eine Präfixlänge von 1 oder höher benötigt.  
  
 Verwenden Sie die in der folgenden Tabelle gezeigten Präfixlängen, wenn Sie einen Massenexport von Daten vornehmen und diese in systemeigenen Datentypen oder im Zeichenformat speichern.  
  
|SQL Server<br /><br /> Datentyp|Systemeigenes Format<br /><br /> NOT NULL|Systemeigenes Format<br /><br /> NULL|Zeichenformat<br /><br /> NOT NULL|Zeichenformat<br /><br /> NULL|  
|------------------------------|--------------------------------|----------------------------|-----------------------------------|-------------------------------|  
|`char`|2|2|2|2|  
|`varchar`|2|2|2|2|  
|`nchar`|2|2|2|2|  
|`nvarchar`|2|2|2|2|  
|`text` <sup>1</sup>|4|4|4|4|  
|`ntext` <sup>1</sup>|4|4|4|4|  
|`binary`|2|2|2|2|  
|`varbinary`|2|2|2|2|  
|`image` <sup>1</sup>|4|4|4|4|  
|`datetime`|0|1|0|1|  
|`smalldatetime`|0|1|0|1|  
|`decimal`|1|1|1|1|  
|`numeric`|1|1|1|1|  
|`float`|0|1|0|1|  
|`real`|0|1|0|1|  
|`int`|0|1|0|1|  
|`bigint`|0|1|0|1|  
|`smallint`|0|1|0|1|  
|`tinyint`|0|1|0|1|  
|`money`|0|1|0|1|  
|`smallmoney`|0|1|0|1|  
|`bit`|0|1|0|1|  
|`uniqueidentifier`|1|1|0|1|  
|`timestamp`|1|1|1|1|  
|`varchar(max)`|8|8|8|8|  
|`varbinary(max)`|8|8|8|8|  
|UDT (ein benutzerdefinierter Datentyp)|8|8|8|8|  
|XML|8|8|8|8|  
  
 <sup>1</sup> der `ntext`, `text`, und `image` Datentypen werden in einer zukünftigen Version von entfernt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vermeiden Sie die Verwendung dieser Datentypen bei neuen Entwicklungen, und planen Sie die Änderung von Anwendungen, in denen sie aktuell verwendet werden. Verwendung `nvarchar(max)`, `varchar(max)`, und `varbinary(max)` stattdessen.  
  
##  <a name="PrefixLengthsImport"></a> Präfixlängen für den Massenimport  
 Wenn Daten massenimportiert werden, entspricht die Präfixlänge dem Wert, der beim ursprünglichen Erstellen der Datendatei angegeben wurde. Wenn die Datendatei nicht mit einem **bcp** -Befehl erstellt wurde, sind wahrscheinlich keine Längenpräfixzeichen vorhanden. In diesem Fall sollten Sie 0 als Präfixlänge angeben.  
  
> [!NOTE]  
>  Verwenden Sie die weiter oben in diesem Thema unter **Präfixlängen für den Massenexport**bereitgestellten Präfixlängen, um die Präfixlänge in einer Datendatei anzugeben, die nicht mithilfe von [bcp](#PrefixLengthsExport)erstellt wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [bcp (Hilfsprogramm)](../../tools/bcp-utility.md)   
 [Datentypen &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Angeben der Feldlänge mithilfe von bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)   
 [Angeben von Feld- und Zeilenabschlusszeichen &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [Angeben des Dateispeichertyps mithilfe von bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
  
