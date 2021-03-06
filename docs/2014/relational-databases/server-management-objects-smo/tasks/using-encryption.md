---
title: Verwenden der Verschlüsselung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- database master key [SMO]
- cryptography [SMO]
- cryptography [SQL Server], SMO
- encryption keys [SMO]
- encryption [SQL Server], SMO
- encryption [SMO]
- certificates [SMO]
- service master key [SMO]
ms.assetid: 405e0ed7-50a9-430e-a343-471f54b4af76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 233f5bc9decf5e8246f2aba6836ec5ecb650283b
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72781848"
---
# <a name="using-encryption"></a>Verwenden der Verschlüsselung
  In SMO wird der Diensthauptschlüssel durch das <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey>-Objekt dargestellt. Hierauf wird von der <xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A>-Eigenschaft des <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekts verwiesen. Er wird durch die Verwendung der <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A>-Methode erneut generiert.  
  
 Der Datenbank-Hauptschlüssel wird durch das <xref:Microsoft.SqlServer.Management.Smo.MasterKey>-Objekt dargestellt. Die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A>-Eigenschaft gibt an, ob der Datenbank-Hauptschlüssel durch den Diensthauptschlüssel verschlüsselt ist oder nicht. Die verschlüsselte Kopie in der Hauptdatenbank wird immer dann automatisch aktualisiert, wenn der Datenbank-Hauptschlüssel geändert wird.  
  
 Es ist möglich, die Verschlüsselung des Dienstschlüssels durch die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A>-Methode zu verwerfen und den Datenbank-Hauptschlüssel mit einem Kennwort zu verschlüsseln. In diesem Fall müssen Sie den Datenbank-Hauptschlüssel explizit öffnen, bevor Sie auf die privaten Schlüssel zugreifen, die von diesem gesichert wurden.  
  
 Wenn eine Datenbank an eine Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] angehängt wird, müssen Sie entweder das Kennwort für den Datenbank-Hauptschlüssel bereitstellen oder die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A>-Methode ausführen, um eine unverschlüsselte Kopie des Datenbank-Hauptschlüssels für die Verschlüsselung mit dem Diensthauptschlüssel verfügbar zu machen. Dieser Schritt wird empfohlen, um zu vermeiden, dass der Datenbank-Hauptschlüssel explizit geöffnet werden muss.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A>-Methode generiert den Datenbank-Hauptschlüssel neu. Wenn der Datenbank-Hauptschlüssel neu generiert wird, werden alle Schlüssel, die durch den Datenbank-Hauptschlüssel verschlüsselt wurden, entschlüsselt. Daraufhin werden diese mit dem neuen Datenbank-Hauptschlüssel verschlüsselt. Die <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A>-Methode entfernt die Verschlüsselung des Datenbankhauptschlüssels durch den Diensthauptschlüssel. Mit <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> wird eine Kopie des Hauptschlüssels mithilfe des Diensthauptschlüssels verschlüsselt und in der aktuellen Datenbank und in der Masterdatenbank gespeichert.  
  
 In SMO werden Zertifikate durch das <xref:Microsoft.SqlServer.Management.Smo.Certificate>-Objekt dargestellt. Das <xref:Microsoft.SqlServer.Management.Smo.Certificate>-Objekt verfügt über Eigenschaften, die den öffentlichen Schlüssel, den Namen des Betreffs, die Gültigkeitsdauer und Informationen über den Aussteller festlegen. Die Berechtigung, auf das Zertifikat zuzugreifen, wird über die Methoden `Grant`, `Revoke` und `Deny` gesteuert.  
  
## <a name="example"></a>Beispiel  
 Für das folgende Codebeispiel müssen Sie die Programmierungsumgebung, die Programmiervorlage und die Programmiersprache auswählen, um Ihre Anwendung zu erstellen. Weitere Informationen finden Sie unter [Erstellen eines Visual Basic SMO-Projekts in Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) und [Erstellen eines Visual&#35; C SMO-Projekts in Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="adding-a-certificate-in-visual-basic"></a>Hinzufügen eines Zertifikats in Visual Basic  
 Im Codebeispiel wird ein einfaches Zertifikat mit einem Verschlüsselungskennwort erstellt. Im Gegensatz zu anderen Objekten verfügt die <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A>-Methode über mehrere Überladungen. Die im Beispiel verwendete Überladung erstellt ein Zertifikat mit einem Verschlüsselungskennwort.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCertificate1](SMO How to#SMO_VBCertificate1)]  -->  
  
## <a name="adding-a-certificate-in-visual-c"></a>Hinzufügen eines Zertifikats in Visual C#  
 Im Codebeispiel wird ein einfaches Zertifikat mit einem Verschlüsselungskennwort erstellt. Im Gegensatz zu anderen Objekten verfügt die <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A>-Methode über mehrere Überladungen. Die im Beispiel verwendete Überladung erstellt ein Zertifikat mit einem Verschlüsselungskennwort.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            {  
                Server srv = new Server();  
  
                //Reference the AdventureWorks2012 database.   
                Database db = srv.Databases["AdventureWorks2012"];  
  
                //Define a Certificate object variable by supplying the parent database and name in the constructor.   
                Certificate c = new Certificate(db, "Test_Certificate");  
  
                //Set the start date, expiry date, and description.   
                System.DateTime dt;  
                DateTime.TryParse("January 01, 2010", out dt);  
                c.StartDate = dt;  
                DateTime.TryParse("January 01, 2015", out dt);  
                c.ExpirationDate = dt;  
                c.Subject = "This is a test certificate.";  
                //Create the certificate on the instance of SQL Server by supplying the certificate password argument.   
                c.Create("pGFD4bb925DGvbd2439587y");  
            }  
        }   
```  
  
## <a name="adding-a-certificate-in-powershell"></a>Hinzufügen eines Zertifikats in PowerShell  
 Im Codebeispiel wird ein einfaches Zertifikat mit einem Verschlüsselungskennwort erstellt. Im Gegensatz zu anderen Objekten verfügt die <xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A>-Methode über mehrere Überladungen. Die im Beispiel verwendete Überladung erstellt ein Zertifikat mit einem Verschlüsselungskennwort.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
#Create a certificate
$c = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Certificate -ArgumentList $db, "Test_Certificate"  
$c.StartDate = "January 01, 2010"  
$c.Subject = "This is a test certificate."  
$c.ExpirationDate = "January 01, 2015"  
  
#Create the certificate on the instance of SQL Server by supplying the certificate password argument.  
$c.Create("pGFD4bb925DGvbd2439587y")
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden von Verschlüsselungsschlüsseln](using-encryption.md)  
