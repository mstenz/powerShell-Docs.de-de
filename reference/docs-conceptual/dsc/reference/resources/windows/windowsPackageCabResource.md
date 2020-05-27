---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: WindowsPackageCab-Ressource in DSC
ms.openlocfilehash: 1b1b8b6d065882400608d26a991318fec9ad5747
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563945"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="71951-103">WindowsPackageCab-Ressource in DSC</span><span class="sxs-lookup"><span data-stu-id="71951-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="71951-104">Gilt für: Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="71951-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="71951-105">Die Ressource **WindowsPackageCab** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Installieren oder Deinstallieren von Windows-CAB-Paketen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="71951-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="71951-106">Auf dem Zielknoten muss das DISM-PowerShell-Modul installiert sein.</span><span class="sxs-lookup"><span data-stu-id="71951-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="71951-107">Weitere Informationen finden Sie unter [Verwenden von DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span><span class="sxs-lookup"><span data-stu-id="71951-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

## <a name="syntax"></a><span data-ttu-id="71951-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="71951-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="71951-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="71951-109">Properties</span></span>

|<span data-ttu-id="71951-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="71951-110">Property</span></span> |<span data-ttu-id="71951-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="71951-111">Description</span></span> |
|---|---|
|<span data-ttu-id="71951-112">Name</span><span class="sxs-lookup"><span data-stu-id="71951-112">Name</span></span> |<span data-ttu-id="71951-113">Gibt den Namen des Pakets an, für das Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="71951-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="71951-114">SourcePath</span><span class="sxs-lookup"><span data-stu-id="71951-114">SourcePath</span></span> |<span data-ttu-id="71951-115">Gibt den Pfad an, in dem das Paket gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="71951-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="71951-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="71951-116">LogPath</span></span> |<span data-ttu-id="71951-117">Gibt den vollständigen Pfad an, in dem der Anbieter eine Protokolldatei zum Installieren oder Deinstallieren des Pakets speichern soll.</span><span class="sxs-lookup"><span data-stu-id="71951-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="71951-118">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="71951-118">Common properties</span></span>

|<span data-ttu-id="71951-119">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="71951-119">Property</span></span> |<span data-ttu-id="71951-120">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="71951-120">Description</span></span> |
|---|---|
|<span data-ttu-id="71951-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="71951-121">DependsOn</span></span> |<span data-ttu-id="71951-122">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="71951-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="71951-123">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="71951-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="71951-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="71951-124">Ensure</span></span> |<span data-ttu-id="71951-125">Gibt an, ob das Paket installiert ist.</span><span class="sxs-lookup"><span data-stu-id="71951-125">Indicates if the package is installed.</span></span> <span data-ttu-id="71951-126">Legen Sie diese Eigenschaft auf **Absent** fest, um sicherzustellen, dass das Paket nicht installiert wird (oder deinstalliert wird, wenn es installiert ist).</span><span class="sxs-lookup"><span data-stu-id="71951-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="71951-127">Legen Sie sie auf **Present** fest, um sicherzustellen, dass das Paket installiert wird.</span><span class="sxs-lookup"><span data-stu-id="71951-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="71951-128">**Ensure** ist eine erforderliche Eigenschaft der **WindowsPackageCab**-Ressource.</span><span class="sxs-lookup"><span data-stu-id="71951-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="71951-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="71951-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="71951-130">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="71951-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="71951-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="71951-131">Example</span></span>

<span data-ttu-id="71951-132">In der folgenden Beispielkonfiguration werden Eingabeparameter verwendet, und es wird sichergestellt, dass die über den `$Name`-Parameter angegebene CAB-Datei installiert ist.</span><span class="sxs-lookup"><span data-stu-id="71951-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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
