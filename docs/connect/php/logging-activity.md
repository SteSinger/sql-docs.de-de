---
title: Protokollierungs Aktivität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- logging activity
ms.assetid: a777b3d9-2262-4e82-bc82-b62ad60d0e55
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 29c7c1e3b536e237e2c61a8e3303313ec53fe679
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993331"
---
# <a name="logging-activity"></a>Protokollieren von Aktivitäten
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Standardmäßig werden Fehler und Warnungen, die von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] generiert werden, nicht protokolliert. Dieses Thema erläutert, wie Protokollierungsaktivitäten konfiguriert werden.  
  
## <a name="logging-activity-using-the-pdosqlsrv-driver"></a>Protokollieren von Aktivitäten mit dem PDO_SQLSRV-Treiber  
Die einzige Konfiguration, die für den PDO_SQLSRV-Treiber verfügbar ist, ist der pdo_sqlsrv.log_severity-Eintrag in der Datei „php.ini“.  
  
Fügen Sie am Ende der Datei „php.ini“ Folgendes ein:  
  
```  
[pdo_sqlsrv]  
pdo_sqlsrv.log_severity = <number>  
```  
  
Für**log_severity** sind die folgenden Werte möglich.  
  
|value|und Beschreibung|  
|---------|---------------|  
|0|Die Protokollierung ist deaktiviert (Standardeinstellung, wenn nichts definiert ist).|  
|-1|Gibt an, dass Fehler, Warnungen und Hinweise protokolliert werden.|  
|1|Gibt an, dass Fehler protokolliert werden.|  
|2|Gibt an, dass Warnungen protokolliert werden.|  
|4|Gibt an, dass Benachrichtigungen protokolliert werden.|  
  
Protokollierungsinformationen werden der „phperrors.log“-Datei hinzugefügt.  
  
PHP liest die Konfigurationsdatei bei der Initialisierung und speichert die Daten in einem Cache. Außerdem stellt es eine API bereit, um die Einstellungen, die in die Konfigurationsdatei geschrieben werden, zu updaten und sofort zu verwenden. Mit dieser API können Anwendungsskripts die Einstellungen auch nach der PHP-Initialisierung ändern.  
  
## <a name="logging-activity-using-the-sqlsrv-driver"></a>Protokollieren von Aktivitäten mit dem SQLSRV-Treiber  
Um die Protokollierung zu aktivieren, können Sie die [sqlsrv_configure](../../connect/php/sqlsrv-configure.md)-Funktion verwenden oder die „php.ini“-Datei ändern. Sie können Aktivitäten protokollieren, die in Initialisierungen, Verbindungen, Anweisungen oder Fehlerfunktionen auftreten. Sie können auch angeben, ob Fehler, Warnungen, Hinweise oder alle drei protokolliert werden sollen.  
  
> [!NOTE]  
> Sie können den Speicherort der Protokolldatei in der Datei „php.ini“ konfigurieren.  
  
### <a name="turning-logging-on"></a>Aktivieren der Protokollierung  
Sie können die Protokollierung mit der [sqlsrv_configure](../../connect/php/sqlsrv-configure.md)-Funktion aktivieren, um einen Wert für die **LogSubsystems**-Einstellung anzugeben. Zum Beispiel konfiguriert die folgende Codezeile den Treiber zur Protokollierung von Aktivitäten bei Verbindungen:  
  
`sqlsrv_configure("LogSubsystems", SQLSRV_LOG_SYSTEM_CONN);`  
  
Die folgende Tabelle beschreibt die Konstanten, die als Wert für die **LogSubsystems** -Einstellung verwendet werden können:  
  
|Wert (entsprechende ganze Zahl in Klammern)|und Beschreibung|  
|-----------------------------------------------|---------------|  
|SQLSRV_LOG_SYSTEM_ALL (-1)|Aktiviert die Protokollierung aller Subsysteme.|  
|SQLSRV_LOG_SYSTEM_OFF(0)|Deaktiviert die Protokollierung. Dies ist die Standardeinstellung.|  
|SQLSRV_LOG_SYSTEM_INIT (1)|Aktiviert die Protokollierung der Initialisierungsaktivität.|  
|SQLSRV_LOG_SYSTEM_CONN (2)|Aktiviert die Protokollierung der Verbindungsaktivität.|  
|SQLSRV_LOG_SYSTEM_STMT (4)|Aktiviert die Protokollierung der Anweisungsaktivität.|  
|SQLSRV_LOG_SYSTEM_UTIL (8)|Aktiviert die Protokollierung der Fehlerfunktionsaktivität (z. B. Handle_error und Handle_warning).|  
  
Sie können mehr als einen Wert gleichzeitig für die **LogSubsystems**-Einstellung mithilfe des logischen OR-Operators (|) festlegen. Die folgende Codezeile aktiviert z. B. die Protokollierung der Aktivität für Verbindungen und Anweisungen:  
  
`sqlsrv_configure("LogSubsystems", SQLSRV_LOG_SYSTEM_CONN | SQLSRV_LOG_SYSTEM_STMT);`  
  
Sie können auch die Protokollierung durch Angeben eines ganzzahligen Werts für die **LogSubsystems**-Einstellung in der Datei „php.ini“ aktivieren. Zum Beispiel wird durch Hinzufügen der folgenden Zeile des `[sqlsrv]`-Abschnitts der „php.ini“-Datei die Protokollierung der Verbindungsaktivität aktiviert.  
  
`sqlsrv.LogSubsystems = 2`  
  
Durch die Addition von ganzzahligen Werten können Sie mehrere Optionen gleichzeitig angeben. Zum Beispiel wird durch Hinzufügen der folgenden Zeile des `[sqlsrv]`-Abschnitts der „php.ini“-Datei die Protokollierung der Verbindungs- und Anweisungsaktivität aktiviert.  
  
`sqlsrv.LogSubsystems = 6`  
  
### <a name="logging-errors-warnings-and-notices"></a>Protokollieren von Fehlern, Warnungen und Hinweisen  
Nachdem die Protokollierung aktiviert wurde, müssen Sie angeben, was protokolliert werden soll. Sie können eine oder mehrere der folgenden Möglichkeiten protokollieren: Fehler, Warnungen und Hinweise. Die folgende Codezeile gibt z. B. an, dass nur Warnungen protokolliert werden:  
  
`sqlsrv_configure("LogSeverity", SQLSRV_LOG_SEVERITY_WARNING);`  
  
> [!NOTE]  
> Die Standardeinstellung für **LogSeverity** ist **SQLSRV_LOG_SEVERITY_ERROR**. Wenn die Protokollierung aktiviert ist und keine Einstellung für die **LogSeverity** angegeben ist, werden nur Fehler protokolliert.  
  
Die folgende Tabelle beschreibt die Konstanten, die als Wert für die **LogSeverity** -Einstellung verwendet werden können:  
  
|Wert (entsprechende ganze Zahl in Klammern)|und Beschreibung|  
|-----------------------------------------------|---------------|  
|SQLSRV_LOG_SEVERITY_ALL (-1)|Gibt an, dass Fehler, Warnungen und Hinweise protokolliert werden.|  
|SQLSRV_LOG_SEVERITY_ERROR (1)|Gibt an, dass Fehler protokolliert werden. Dies ist die Standardeinstellung.|  
|SQLSRV_LOG_SEVERITY_WARNING (2)|Gibt an, dass Warnungen protokolliert werden.|  
|SQLSRV_LOG_SEVERITY_NOTICE (4)|Gibt an, dass Benachrichtigungen protokolliert werden.|  
  
Sie können mehr als einen Wert gleichzeitig für die **LogSeverity**-Einstellung mithilfe des logischen OR-Operators (|) festlegen. Die folgende Codezeile gibt z. B. an, dass Fehler und Warnungen protokolliert werden sollten:  
  
`sqlsrv_configure("LogSeverity", SQLSRV_LOG_SEVERITY_ERROR | SQLSRV_LOG_SEVERITY_WARNING);`  
  
> [!NOTE]  
> Die Angabe eines Werts für die **LogSeverity**-Einstellung aktiviert nicht die Protokollierung. Aktivieren Sie die Protokollierung durch Angabe eines Werts für die **LogSubsystems**-Einstellung und geben Sie dann den Schweregrad an, der protokolliert werden soll, indem Sie einen Wert für **LogSeverity** angeben.  
  
Sie können auch eine Einstellung für die **LogSeverity** -Einstellung mithilfe von ganzzahligen Werten in der Datei „php.ini“ festlegen. Zum Beispiel wird durch Hinzufügen der folgende Zeile des `[sqlsrv]` -Abschnitts der „php.ini“-Datei nur die Protokollierung von Warnungen aktiviert.  
  
`sqlsrv.LogSeverity = 2`  
  
Durch die Addition von ganzzahligen Werten können Sie mehrere Optionen gleichzeitig angeben. Zum Beispiel wird durch Hinzufügen der folgende Zeile des `[sqlsrv]`-Abschnitts der „php.ini“-Datei nur die Protokollierung von Fehlern und Warnungen aktiviert.  
  
`sqlsrv.LogSeverity = 3`  
  
## <a name="see-also"></a>Weitere Informationen  
[Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)

[sqlsrv_get_config](../../connect/php/sqlsrv-get-config.md)

[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  
  
