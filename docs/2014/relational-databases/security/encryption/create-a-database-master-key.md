---
title: Erstellen eines Datenbank-Hauptschlüssels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.reviewer: carlrab
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.openlocfilehash: 86f74710e99079d0acd28db09bcf1e4ba7c57865
ms.sourcegitcommit: 39ea690996a7390e3d13d6fb8f39d8641cd5f710
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "74957244"
---
# <a name="create-a-database-master-key"></a>Erstellen eines Datenbank-Hauptschlüssels

In diesem Thema wird beschrieben, wie Sie in `master` [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe [!INCLUDE[tsql](../../../includes/tsql-md.md)]von einen Datenbank-Hauptschlüssel in der-Datenbank erstellen.

**In diesem Thema**

- **Bevor Sie beginnen:**

  [Sicherung](#Security)

- [So erstellen Sie einen Datenbank-Hauptschlüssel mithilfe von Transact-SQL](#TsqlProcedure)

## <a name="BeforeYouBegin"></a>Bevor Sie beginnen

### <a name="Security"></a>Sicherung

#### <a name="Permissions"></a>Griff

Erfordert die CONTROL-Berechtigung für die Datenbank.

## <a name="TsqlProcedure"></a>Verwenden von Transact-SQL

### <a name="to-create-a-database-master-key"></a>So erstellen Sie einen Datenbank-Hauptschlüssel

1. Wählen Sie ein Kennwort aus, mit dem die in der Datenbank gespeicherte Kopie des Datenbank-Hauptschlüssels verschlüsselt wird.
2. Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.
3. Erweitern Sie **Systemdatenbanken**, klicken Sie mit der rechten Maustaste auf `master`, und klicken Sie anschließend auf **Neue Abfrage**.
4. Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

Weitere Informationen finden Sie unter [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql).
