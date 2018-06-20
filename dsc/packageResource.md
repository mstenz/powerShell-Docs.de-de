---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Package“
ms.openlocfilehash: 16f7f1b8fa7b84bcfdeb09fdc46db9c93113e70c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188529"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="7db6f-103">DSC-Ressource „Package“</span><span class="sxs-lookup"><span data-stu-id="7db6f-103">DSC Package Resource</span></span>

> <span data-ttu-id="7db6f-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7db6f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7db6f-105">Die Ressource **Package** in Windows PowerShell DSC bietet einen Mechanismus zum Installieren oder Deinstallieren von Paketen, wie z. B. Windows Installer und „Setup.exe“-Pakete, auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="7db6f-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7db6f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7db6f-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7db6f-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="7db6f-107">Properties</span></span>
|  <span data-ttu-id="7db6f-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="7db6f-108">Property</span></span>  |  <span data-ttu-id="7db6f-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7db6f-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="7db6f-110">Name</span><span class="sxs-lookup"><span data-stu-id="7db6f-110">Name</span></span>| <span data-ttu-id="7db6f-111">Gibt den Namen des Pakets an, für das Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="7db6f-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="7db6f-112">Pfad</span><span class="sxs-lookup"><span data-stu-id="7db6f-112">Path</span></span>| <span data-ttu-id="7db6f-113">Gibt den Pfad an, in dem das Paket gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="7db6f-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="7db6f-114">ProductID</span><span class="sxs-lookup"><span data-stu-id="7db6f-114">ProductId</span></span>| <span data-ttu-id="7db6f-115">Gibt die Produkt-ID an, die das Paket eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="7db6f-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="7db6f-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="7db6f-116">Arguments</span></span>| <span data-ttu-id="7db6f-117">Führt eine Zeichenfolge mit Argumenten auf, die exakt wie angegeben an das Paket übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="7db6f-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="7db6f-118">Credential</span><span class="sxs-lookup"><span data-stu-id="7db6f-118">Credential</span></span>| <span data-ttu-id="7db6f-119">Ermöglicht den Zugriff auf das Paket für eine Remotequelle.</span><span class="sxs-lookup"><span data-stu-id="7db6f-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="7db6f-120">Diese Eigenschaft wird nicht verwendet, um das Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="7db6f-120">This property is not used to install the package.</span></span> <span data-ttu-id="7db6f-121">Das Paket wird immer auf dem lokalen System installiert.</span><span class="sxs-lookup"><span data-stu-id="7db6f-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="7db6f-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="7db6f-122">Ensure</span></span>| <span data-ttu-id="7db6f-123">Gibt an, ob das Paket installiert ist.</span><span class="sxs-lookup"><span data-stu-id="7db6f-123">Indicates if the package is installed.</span></span> <span data-ttu-id="7db6f-124">Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass das Paket nicht installiert wird (oder deinstalliert wird, wenn es installiert ist).</span><span class="sxs-lookup"><span data-stu-id="7db6f-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="7db6f-125">Legen Sie sie auf „Present“ (den Standardwert) fest, um sicherzustellen, dass das Paket installiert wird.</span><span class="sxs-lookup"><span data-stu-id="7db6f-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="7db6f-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="7db6f-126">LogPath</span></span>| <span data-ttu-id="7db6f-127">Gibt den vollständigen Pfad an, in dem der Anbieter eine Protokolldatei zum Installieren oder Deinstallieren des Pakets speichern soll.</span><span class="sxs-lookup"><span data-stu-id="7db6f-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="7db6f-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7db6f-128">DependsOn</span></span> | <span data-ttu-id="7db6f-129">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="7db6f-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7db6f-130">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.</span><span class="sxs-lookup"><span data-stu-id="7db6f-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|
| <span data-ttu-id="7db6f-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="7db6f-131">ReturnCode</span></span>| <span data-ttu-id="7db6f-132">Gibt den erwarteten Rückgabecode an.</span><span class="sxs-lookup"><span data-stu-id="7db6f-132">Indicates the expected return code.</span></span> <span data-ttu-id="7db6f-133">Wenn der tatsächliche Rückgabecode nicht dem erwarteten Wert entspricht, gibt die Konfiguration einen Fehler zurück.</span><span class="sxs-lookup"><span data-stu-id="7db6f-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="7db6f-134">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7db6f-134">Example</span></span>

<span data-ttu-id="7db6f-135">Bei diesem Beispiel wird das MSI-Installationsprogramm ausgeführt, das sich im angegebenen Pfad befindet und die angegebene Produkt-ID hat.</span><span class="sxs-lookup"><span data-stu-id="7db6f-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```