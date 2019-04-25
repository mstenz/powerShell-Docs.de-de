---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: WindowsPackageCab-Ressource in DSC
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076938"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="ddb08-103">WindowsPackageCab-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="ddb08-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="ddb08-104">Gilt für: Windows PowerShell 5.1 und höher</span><span class="sxs-lookup"><span data-stu-id="ddb08-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="ddb08-105">Die Ressource **WindowsPackageCab** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Installieren oder Deinstallieren von Windows-CAB-Paketen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="ddb08-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="ddb08-106">Auf dem Zielknoten muss das DISM-PowerShell-Modul installiert sein.</span><span class="sxs-lookup"><span data-stu-id="ddb08-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="ddb08-107">Weitere Informationen finden Sie unter [Verwenden von DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="ddb08-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="ddb08-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="ddb08-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="ddb08-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ddb08-109">Properties</span></span>

|  <span data-ttu-id="ddb08-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ddb08-110">Property</span></span>  |  <span data-ttu-id="ddb08-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ddb08-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="ddb08-112">Name</span><span class="sxs-lookup"><span data-stu-id="ddb08-112">Name</span></span>| <span data-ttu-id="ddb08-113">Gibt den Namen des Pakets an, für das Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="ddb08-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="ddb08-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="ddb08-114">Ensure</span></span>| <span data-ttu-id="ddb08-115">Gibt an, ob das Paket installiert ist.</span><span class="sxs-lookup"><span data-stu-id="ddb08-115">Indicates if the package is installed.</span></span> <span data-ttu-id="ddb08-116">Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass das Paket nicht installiert wird (oder deinstalliert wird, wenn es installiert ist).</span><span class="sxs-lookup"><span data-stu-id="ddb08-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="ddb08-117">Legen Sie sie auf „Present“ (den Standardwert) fest, um sicherzustellen, dass das Paket installiert wird.</span><span class="sxs-lookup"><span data-stu-id="ddb08-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="ddb08-118">Pfad</span><span class="sxs-lookup"><span data-stu-id="ddb08-118">Path</span></span>| <span data-ttu-id="ddb08-119">Gibt den Pfad an, in dem das Paket gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="ddb08-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="ddb08-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="ddb08-120">LogPath</span></span>| <span data-ttu-id="ddb08-121">Gibt den vollständigen Pfad an, in dem der Anbieter eine Protokolldatei zum Installieren oder Deinstallieren des Pakets speichern soll.</span><span class="sxs-lookup"><span data-stu-id="ddb08-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="ddb08-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ddb08-122">DependsOn</span></span> | <span data-ttu-id="ddb08-123">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="ddb08-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ddb08-124">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.</span><span class="sxs-lookup"><span data-stu-id="ddb08-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="ddb08-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ddb08-125">Example</span></span>

<span data-ttu-id="ddb08-126">In der folgenden Beispielkonfiguration werden Eingabeparameter verwendet, und es wird sichergestellt, dass die über den `$Name`-Parameter angegebene CAB-Datei installiert ist.</span><span class="sxs-lookup"><span data-stu-id="ddb08-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```