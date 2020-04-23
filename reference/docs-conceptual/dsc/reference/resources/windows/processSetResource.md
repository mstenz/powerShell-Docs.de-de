---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „ProcessSet“
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953127"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="f017b-103">DSC-Ressource „ProcessSet“</span><span class="sxs-lookup"><span data-stu-id="f017b-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="f017b-104">Gilt für: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="f017b-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="f017b-105">Die Ressource **ProcessSet** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="f017b-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f017b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f017b-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="f017b-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="f017b-107">Properties</span></span>

|<span data-ttu-id="f017b-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f017b-108">Property</span></span> |<span data-ttu-id="f017b-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="f017b-109">Description</span></span> |
|---|---|
|<span data-ttu-id="f017b-110">`Path`</span><span class="sxs-lookup"><span data-stu-id="f017b-110">Path</span></span> |<span data-ttu-id="f017b-111">Der Pfad zur ausführbaren Prozessdatei.</span><span class="sxs-lookup"><span data-stu-id="f017b-111">The path to the process executable.</span></span> <span data-ttu-id="f017b-112">Wenn es sich um die Namen der ausführbaren Dateien (keine vollqualifizierten Pfade) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable `$env:Path`, um die Dateien zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="f017b-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="f017b-113">Wenn die Werte dieser Eigenschaft vollqualifizierte Pfade sind, verwendet DSC nicht die Umgebungsvariable `$env:Path`, um die Dateien zu finden, und löst einen Fehler aus, wenn beliebige der Pfade nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="f017b-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="f017b-114">Relative Pfade sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="f017b-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="f017b-115">Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="f017b-115">Credential</span></span> |<span data-ttu-id="f017b-116">Gibt die Anmeldeinformationen zum Starten des Prozesses an.</span><span class="sxs-lookup"><span data-stu-id="f017b-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="f017b-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="f017b-117">StandardErrorPath</span></span> |<span data-ttu-id="f017b-118">Der Pfad, in den der Prozess Standardfehler schreibt.</span><span class="sxs-lookup"><span data-stu-id="f017b-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="f017b-119">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="f017b-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="f017b-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="f017b-120">StandardInputPath</span></span> |<span data-ttu-id="f017b-121">Der Datenstrom, aus dem der Prozess die Standardeingabe empfängt.</span><span class="sxs-lookup"><span data-stu-id="f017b-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="f017b-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="f017b-122">StandardOutputPath</span></span> |<span data-ttu-id="f017b-123">Der Pfad der Datei, in die der Prozess die Standardausgabe schreibt.</span><span class="sxs-lookup"><span data-stu-id="f017b-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="f017b-124">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="f017b-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="f017b-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="f017b-125">WorkingDirectory</span></span> |<span data-ttu-id="f017b-126">Der Speicherort, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f017b-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f017b-127">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="f017b-127">Common properties</span></span>

|<span data-ttu-id="f017b-128">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f017b-128">Property</span></span> |<span data-ttu-id="f017b-129">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="f017b-129">Description</span></span> |
|---|---|
|<span data-ttu-id="f017b-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f017b-130">DependsOn</span></span> |<span data-ttu-id="f017b-131">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="f017b-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f017b-132">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f017b-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f017b-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="f017b-133">Ensure</span></span> |<span data-ttu-id="f017b-134">Gibt an, ob der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="f017b-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="f017b-135">Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="f017b-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="f017b-136">Legen Sie sie andernfalls auf **Absent** fest.</span><span class="sxs-lookup"><span data-stu-id="f017b-136">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="f017b-137">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="f017b-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="f017b-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f017b-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="f017b-139">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="f017b-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f017b-140">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f017b-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f017b-141">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="f017b-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>