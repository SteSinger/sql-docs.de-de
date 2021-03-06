---
title: Übersicht über Transact-SQL-Anweisungen für AlwaysOn-Verfügbarkeitsgruppen (SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: 184d0a81-2259-4db9-9d0d-01aac0b502c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f635faa05d7d77a50d31491b1bab9b16875e728c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62813810"
---
# <a name="overview-of-transact-sql-statements-for-alwayson-availability-groups-sql-server"></a>Übersicht über Transact-SQL-Anweisungen für AlwaysOn-Verfügbarkeitsgruppen (SQL Server)
  Dieses Thema bietet eine Einführung in die [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen, die das Bereitstellen von [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] und das Erstellen und Verwalten einer bestimmten Verfügbarkeitsgruppe, eines Verfügbarkeitsreplikats und einer Verfügbarkeitsdatenbank unterstützen.  
  
  
##  <a name="CreateEndpoint"></a> CREATE ENDPOINT  
 [CREATE ENDPOINT ... FOR DATABASE_MIRRORING](/sql/t-sql/statements/create-endpoint-transact-sql) erstellt einen Datenbankspiegelungsendpunkt, wenn keiner auf der Serverinstanz vorhanden ist. Für jede Serverinstanz, auf der Sie [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] oder eine Datenbankspiegelung bereitstellen möchten, ist ein Datenbankspiegelungs-Endpunkt erforderlich.  
  
 Führen Sie diese Anweisung auf der Serverinstanz aus, auf der Sie den Endpunkt erstellen. Sie können auf einer angegebenen Serverinstanz nur einen Datenbankspiegelungs-Endpunkt erstellen. Weitere Informationen finden Sie unter [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)aktiviert sind, eine Always On-Verfügbarkeitsgruppe zu erstellen.  
  
##  <a name="CreateAG"></a> CREATE AVAILABILITY GROUP  
 Mit[CREATE AVAILABILITY GROUP](/sql/t-sql/statements/create-availability-group-transact-sql) kann eine neue Verfügbarkeitsgruppe und optional ein Verfügbarkeitsgruppenlistener erstellt werden. Sie müssen mindestens die lokale Serverinstanz angeben, die das ursprüngliche primäre Replikat wird. Optional können Sie auch bis zu vier sekundäre Replikate angeben.  
  
 Führen Sie CREATE AVAILABILITY GROUP für die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aus, die das ursprüngliche primäre Replikat der neuen Verfügbarkeitsgruppe hosten soll. Diese Serverinstanz muss sich auf einem Knoten eines Windows Server Failover Cluster (WSFC) befinden (Weitere Informationen finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="AlterAG"></a> ALTER AVAILABILITY GROUP  
 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) unterstützt das Ändern einer vorhandenen Verfügbarkeitsgruppe oder eines Verfügbarkeitsgruppenlisteners und das Durchführen eines Failovers für eine Verfügbarkeitsgruppe.  
  
 Führen Sie ALTER AVAILABILITY GROUP für die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aus, die das aktuelle primäre Replikat hostet.  
  
##  <a name="AlterDb"></a> ALTER DATABASE ... SET HADR ...  
 Die Optionen der [SET HADR](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) -Klausel der ALTER DATABASE-Anweisung ermöglichen es Ihnen, eine sekundäre Datenbank mit der Verfügbarkeitsgruppe der entsprechenden primären Datenbank zu verknüpfen, eine verknüpfte Datenbank zu entfernen und die Datensynchronisierung für eine verknüpfte Datenbank anzuhalten und die Datensynchronisierung fortzusetzen.  
  
##  <a name="DropAG"></a> DROP AVAILABILITY GROUP  
 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) entfernt eine bestimmte Verfügbarkeitsgruppe und alle Replikate. DROP AVAILABILITY GROUP kann von einem beliebigen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Knoten im WSFC-Failovercluster ausgeführt werden.  
  
##  <a name="Restrictions"></a> Einschränkungen bei den AVAILABILITY GROUP-Transact-SQL-Anweisungen  
 Die CREATE AVAILABILITY GROUP-, ALTER AVAILABILITY GROUP- und DROP AVAILABILITY GROUP-Anweisungen in [!INCLUDE[tsql](../../../includes/tsql-md.md)] weisen die folgenden Einschränkungen auf:  
  
-   Mit Ausnahme von DROP AVAILABILITY GROUP ist für die Ausführung dieser Anweisungen die Aktivierung des HADR-Diensts auf der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erforderlich. Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren von AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Diese Anweisungen können nicht innerhalb von Transaktionen oder Batches ausgeführt werden.  
  
-   Trotz der Bereinigung nach einem Fehler wird mit diesen Anweisungen nicht sichergestellt, dass bei einem Fehler ein Rollback aller Änderungen ausgeführt wird. Systeme sollten Teilfehler jedoch sauber verarbeiten und dann ignorieren können.  
  
-   Diese Anweisungen unterstützen keine Ausdrücke oder Variablen.  
  
-   Wenn eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung während der Ausführung einer anderen Verfügbarkeitsgruppenaktion oder einer Wiederherstellung ausgeführt wird, gibt die Anweisung einen Fehler zurück. Warten Sie, bis die Aktion oder die Wiederherstellung abgeschlossen ist, und wiederholen Sie ggf. die Anweisung.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
