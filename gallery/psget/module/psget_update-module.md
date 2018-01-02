---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Update-Module
ms.openlocfilehash: 66535cd5b1f44e108c2bc47fa343c77c86bb21dc
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2017
---
# <a name="update-module"></a><span data-ttu-id="36f71-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="36f71-103">Update-Module</span></span>

<span data-ttu-id="36f71-104">Lädt die neueste Version der angegebenen Module aus einem Onlinekatalog auf den lokalen Computer herunter und installiert diese</span><span class="sxs-lookup"><span data-stu-id="36f71-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="36f71-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="36f71-105">Description</span></span>

<span data-ttu-id="36f71-106">Das Cmdlet „Update-Module“ installiert eine neuere Version des Windows PowerShell-Moduls, das durch das Ausführen von „Install-Module“ aus dem Onlinekatalog auf dem lokalen Computer installiert wurde.</span><span class="sxs-lookup"><span data-stu-id="36f71-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="36f71-107">Standardmäßig wird die neueste Version des im Onlinekatalog verfügbaren angegebenen Moduls installiert, sofern Sie nicht eine erforderliche Version angeben.</span><span class="sxs-lookup"><span data-stu-id="36f71-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="36f71-108">Sie können ein vorhandenes installiertes Modul aktualisieren, indem Sie den Namen des Moduls angeben. „Update-Module“ sucht nach „$env:PSModulePath“ für das zu aktualisierende Modul.</span><span class="sxs-lookup"><span data-stu-id="36f71-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="36f71-109">Durch das Ausführen von „Update-Module“ ohne den Name-Parameter werden alle Module aktualisiert, die auf dem lokalen Computer aktualisiert werden können.</span><span class="sxs-lookup"><span data-stu-id="36f71-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="36f71-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="36f71-110">Notes</span></span>

- <span data-ttu-id="36f71-111">Dieses Cmdlet wird unter Windows PowerShell 3.0 oder auf höheren Versionen von Windows PowerShell ausgeführt. Ebenso wird es unter Windows 7 oder Windows 2008 R2 und höheren Versionen von Windows ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="36f71-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="36f71-112">Wenn das Modul, das Sie mit dem Name-Parameter angeben, nicht mithilfe von „Install-Module“ installiert wurde, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="36f71-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="36f71-113">Sie können „Update-Module“ nur auf Modulen ausführen, die Sie durch Ausführen von „Install-Module“ aus dem Onlinekatalog installiert haben.</span><span class="sxs-lookup"><span data-stu-id="36f71-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="36f71-114">Wenn „Update-Module“ versucht, Binärdateien zu aktualisieren, die gerade verwendet werden, gibt „Update-Module“ einen Fehler zurück, der die Problemprozesse identifiziert und den Benutzer nach Beenden der Prozesse darüber informiert, „Update-Module“ erneut auszuführen.</span><span class="sxs-lookup"><span data-stu-id="36f71-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="36f71-115">Unter PowerShell 5.0 oder neueren Versionen fügt „Update-Module“ beim Aktualisieren eines Moduls die neueste (oder angegebene) Version des Moduls hinzu, damit sich die ältere und neuere Version nun im gleichen Verzeichnis befindet.</span><span class="sxs-lookup"><span data-stu-id="36f71-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="36f71-116">Es wäre hilfreich, den Benutzer darauf hinzuweisen und ein Beispiel der Ausgabe dieser Befehle anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="36f71-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="36f71-117">Cmdlet-Syntax</span><span class="sxs-lookup"><span data-stu-id="36f71-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="36f71-118">Cmdlet-Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="36f71-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="36f71-119">Update-Module</span><span class="sxs-lookup"><span data-stu-id="36f71-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="36f71-120">Beispiele für Befehle</span><span class="sxs-lookup"><span data-stu-id="36f71-120">Example commands</span></span>

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a><span data-ttu-id="36f71-121">Aktualisieren des Moduls mit einer Vorabversion mit dem erforderlichen -AllowPrerelease-Flag</span><span class="sxs-lookup"><span data-stu-id="36f71-121">Update the module with a prerelease version, requires -AllowPrerelease flag</span></span>
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="36f71-122">Aktualisieren Sie das Modul „TestDepWithNestedRequiredModules1“ mit Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="36f71-122">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```

