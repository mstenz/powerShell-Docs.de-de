---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Ausführen von DSC mit Benutzeranmeldeinformationen"
ms.openlocfilehash: 7b57732679e4fb29112a3ca7fe64cba2bda67207
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="c34a7-103">Ausführen von DSC mit Benutzeranmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="c34a7-103">Running DSC with user credentials</span></span> 

> <span data-ttu-id="c34a7-104">Gilt für: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="c34a7-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="c34a7-105">Sie können eine DSC-Ressource unter einem angegebenen Satz von Anmeldeinformationen ausführen, indem Sie die automatische Eigenschaft **PsDscRunAsCredential** in der Konfiguration verwenden.</span><span class="sxs-lookup"><span data-stu-id="c34a7-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="c34a7-106">Standardmäßig führt DSC jede Ressource unter dem Systemkonto aus.</span><span class="sxs-lookup"><span data-stu-id="c34a7-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="c34a7-107">Es gibt Situationen, in denen DSC unter einem Benutzerkonto ausgeführt werden muss, z. B. beim Installieren von MSI-Paketen in einem bestimmten Benutzerkontext, beim Festlegen von Registrierungsschlüsseln eines Benutzers, beim Zugriff auf ein bestimmtes lokales Verzeichnis eines Benutzers oder beim Zugriff auf eine Netzwerkfreigabe.</span><span class="sxs-lookup"><span data-stu-id="c34a7-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="c34a7-108">Jede DSC-Ressource verfügt über eine **PsDscRunAsCredential**-Eigenschaft, die auf beliebige Anmeldeinformationen festgelegt werden kann (ein [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx)-Objekt).</span><span class="sxs-lookup"><span data-stu-id="c34a7-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="c34a7-109">Die Anmeldeinformationen können als Wert der Eigenschaft in der Konfiguration hartcodiert werden, oder Sie können den Wert auf [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx) festlegen, wodurch der Benutzer beim Kompilieren der Konfiguration zur Eingabe der Anmeldeinformationen aufgefordert wird (Informationen zum Kompilieren von Konfigurationen finden Sie unter [Konfigurationen](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c34a7-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="c34a7-110">**Hinweis:** In PowerShell 5.0 wurde die Verwendung der Eigenschaft **PsDscRunAsCredential** in Konfigurationen, die zusammengesetzte Ressourcen aufrufen, nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c34a7-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> 
><span data-ttu-id="c34a7-111">In PowerShell 5.1 wird die Eigenschaft **PsDscRunAsCredential** in Konfigurationen, die zusammengesetzte Ressourcen aufrufen, unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c34a7-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="c34a7-112">**Hinweis**: Die Eigenschaft **PsDscRunAsCredential** ist in PowerShell 4.0 nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c34a7-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="c34a7-113">Im folgenden Beispiel wird **Get-Credential** verwendet, um den Benutzer zur Eingabe von Anmeldeinformationen aufzufordern.</span><span class="sxs-lookup"><span data-stu-id="c34a7-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span> <span data-ttu-id="c34a7-114">Die Ressource [Registry](registryResource.md) wird verwendet, um den Registrierungsschlüssel zu ändern, der die Hintergrundfarbe für das Windows-Eingabeaufforderungsfenster angibt.</span><span class="sxs-lookup"><span data-stu-id="c34a7-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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
><span data-ttu-id="c34a7-115">**Hinweis**: In diesem Beispiel wird vorausgesetzt, dass Sie über ein gültiges Zertifikat unter `C:\publicKeys\targetNode.cer` verfügen und dass der Fingerabdruck dieses Zertifikats der angezeigte Wert ist.</span><span class="sxs-lookup"><span data-stu-id="c34a7-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="c34a7-116">Informationen zum Verschlüsseln von Anmeldeinformationen in DSC MOF-Konfigurationsdateien finden Sie unter [Schützen der MOF-Datei](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="c34a7-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>

