---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „Package“
ms.openlocfilehash: ff2eae712b4117da9bca915f52e18caed7c4885d
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559929"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="d8378-103">DSC-Ressource „Package“</span><span class="sxs-lookup"><span data-stu-id="d8378-103">DSC Package Resource</span></span>

> <span data-ttu-id="d8378-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="d8378-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d8378-105">Die Ressource **Package** in Windows PowerShell DSC bietet einen Mechanismus zum Installieren oder Deinstallieren von Paketen, wie z. B. Windows Installer und „Setup.exe“-Pakete, auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="d8378-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8378-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8378-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="d8378-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="d8378-107">Properties</span></span>

|<span data-ttu-id="d8378-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="d8378-108">Property</span></span> |<span data-ttu-id="d8378-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="d8378-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d8378-110">Name</span><span class="sxs-lookup"><span data-stu-id="d8378-110">Name</span></span> |<span data-ttu-id="d8378-111">Gibt den Namen des Pakets an, für das Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="d8378-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="d8378-112">`Path`</span><span class="sxs-lookup"><span data-stu-id="d8378-112">Path</span></span> |<span data-ttu-id="d8378-113">Gibt den Pfad an, in dem das Paket gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="d8378-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="d8378-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="d8378-114">ProductId</span></span> |<span data-ttu-id="d8378-115">Gibt die Produkt-ID an, die das Paket eindeutig identifiziert.</span><span class="sxs-lookup"><span data-stu-id="d8378-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="d8378-116">Argumente</span><span class="sxs-lookup"><span data-stu-id="d8378-116">Arguments</span></span> |<span data-ttu-id="d8378-117">Führt eine Zeichenfolge mit Argumenten auf, die exakt wie angegeben an das Paket übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="d8378-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="d8378-118">Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="d8378-118">Credential</span></span> |<span data-ttu-id="d8378-119">Ermöglicht den Zugriff auf das Paket für eine Remotequelle.</span><span class="sxs-lookup"><span data-stu-id="d8378-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="d8378-120">Diese Eigenschaft wird nicht verwendet, um das Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="d8378-120">This property is not used to install the package.</span></span> <span data-ttu-id="d8378-121">Das Paket wird immer auf dem lokalen System installiert.</span><span class="sxs-lookup"><span data-stu-id="d8378-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="d8378-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="d8378-122">LogPath</span></span> |<span data-ttu-id="d8378-123">Gibt den vollständigen Pfad an, in dem der Anbieter eine Protokolldatei zum Installieren oder Deinstallieren des Pakets speichern soll.</span><span class="sxs-lookup"><span data-stu-id="d8378-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="d8378-124">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="d8378-124">ReturnCode</span></span> |<span data-ttu-id="d8378-125">Gibt den erwarteten Rückgabecode an.</span><span class="sxs-lookup"><span data-stu-id="d8378-125">Indicates the expected return code.</span></span> <span data-ttu-id="d8378-126">Wenn der tatsächliche Rückgabecode nicht dem erwarteten Wert entspricht, gibt die Konfiguration einen Fehler zurück.</span><span class="sxs-lookup"><span data-stu-id="d8378-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d8378-127">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="d8378-127">Common properties</span></span>

|<span data-ttu-id="d8378-128">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="d8378-128">Property</span></span> |<span data-ttu-id="d8378-129">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="d8378-129">Description</span></span> |
|---|---|
|<span data-ttu-id="d8378-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d8378-130">DependsOn</span></span> |<span data-ttu-id="d8378-131">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="d8378-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d8378-132">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d8378-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d8378-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="d8378-133">Ensure</span></span> |<span data-ttu-id="d8378-134">Gibt an, ob das Paket installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d8378-134">Indicates if the package is installed.</span></span> <span data-ttu-id="d8378-135">Legen Sie diese Eigenschaft auf **Absent** fest, um sicherzustellen, dass das Paket nicht installiert wird (oder deinstalliert wird, wenn es installiert ist).</span><span class="sxs-lookup"><span data-stu-id="d8378-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="d8378-136">Legen Sie sie auf **Present** fest, um sicherzustellen, dass das Paket installiert wird.</span><span class="sxs-lookup"><span data-stu-id="d8378-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="d8378-137">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="d8378-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="d8378-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d8378-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="d8378-139">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="d8378-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d8378-140">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="d8378-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d8378-141">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="d8378-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="d8378-142">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d8378-142">Example</span></span>

<span data-ttu-id="d8378-143">Bei diesem Beispiel wird das MSI-Installationsprogramm ausgeführt, das sich im angegebenen Pfad befindet und die angegebene Produkt-ID hat.</span><span class="sxs-lookup"><span data-stu-id="d8378-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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
