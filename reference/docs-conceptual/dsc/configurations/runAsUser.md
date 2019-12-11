---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Verwenden von Anmeldeinformationen mit DSC-Ressourcen
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953977"
---
# <a name="use-credentials-with-dsc-resources"></a>Verwenden von Anmeldeinformationen mit DSC-Ressourcen

> Gilt für: Windows PowerShell 5.0, Windows PowerShell 5.1

Sie können eine DSC-Ressource unter einem angegebenen Satz von Anmeldeinformationen ausführen, indem Sie die automatische Eigenschaft **PsDscRunAsCredential** in der Konfiguration verwenden. Standardmäßig führt DSC jede Ressource unter dem Systemkonto aus. Es gibt Situationen, in denen DSC unter einem Benutzerkonto ausgeführt werden muss, z. B. beim Installieren von MSI-Paketen in einem bestimmten Benutzerkontext, beim Festlegen von Registrierungsschlüsseln eines Benutzers, beim Zugriff auf ein bestimmtes lokales Verzeichnis eines Benutzers oder beim Zugriff auf eine Netzwerkfreigabe. Das **SeInteractiveLogonRight** wird vom Zielcomputer für jedes Konto benötigt, das Sie für **PSDSCRunAsCredential** angeben. Weitere Informationen finden Sie unter [Konstanten für Kontorechte](/windows/desktop/secauthz/account-rights-constants).

Jede DSC-Ressource verfügt über eine **PsDscRunAsCredential**-Eigenschaft, die auf beliebige Anmeldeinformationen festgelegt werden kann (ein [PSCredential](/dotnet/api/system.management.automation.pscredential)-Objekt). Die Anmeldeinformationen können als Wert der Eigenschaft in der Konfiguration hartcodiert werden, oder Sie können den Wert auf [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) festlegen, wodurch der Benutzer beim Kompilieren der Konfiguration zur Eingabe der Anmeldeinformationen aufgefordert wird (Informationen zum Kompilieren von Konfigurationen finden Sie unter [Konfigurationen](configurations.md).

> [!NOTE]
> In PowerShell 5.0 wurde die Verwendung der Eigenschaft **PsDscRunAsCredential** in Konfigurationen, die zusammengesetzte Ressourcen aufrufen, nicht unterstützt. In PowerShell 5.1 wird die Eigenschaft **PsDscRunAsCredential** in Konfigurationen, die zusammengesetzte Ressourcen aufrufen, unterstützt. Die Eigenschaft **PsDscRunAsCredential** ist in PowerShell 4.0 nicht verfügbar.

Im folgenden Beispiel wird `Get-Credential` verwendet, um den Benutzer zur Eingabe von Anmeldeinformationen aufzufordern. Die Ressource **Registry** wird verwendet, um den Registrierungsschlüssel zu ändern, der die Hintergrundfarbe für das Windows-Eingabeaufforderungsfenster angibt.

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> In diesem Beispiel wird vorausgesetzt, dass Sie über ein gültiges Zertifikat unter `C:\publicKeys\targetNode.cer` verfügen und dass der Fingerabdruck dieses Zertifikats der angezeigte Wert ist. Informationen zum Verschlüsseln von Anmeldeinformationen in DSC MOF-Konfigurationsdateien finden Sie unter [Schützen der MOF-Datei](../pull-server/secureMOF.md).
