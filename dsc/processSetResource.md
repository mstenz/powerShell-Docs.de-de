---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „ProcessSet“
ms.openlocfilehash: d3c7383da5fd10580612527465ab621004ee7269
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="b709a-103">DSC-Ressource „WindowsProcess“</span><span class="sxs-lookup"><span data-stu-id="b709a-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="b709a-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b709a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b709a-105">Die Ressource **ProcessSet** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="b709a-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="b709a-106">Diese Ressource ist eine [zusammengesetzte Ressource](authoringResourceComposite.md), die die Ressource [WindowsProcess](windowsProcessResource.md) für jede Gruppe aufruft, die im `GroupName`-Parameter angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="b709a-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b709a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b709a-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="b709a-108">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="b709a-108">Properties</span></span>
|  <span data-ttu-id="b709a-109">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b709a-109">Property</span></span>  |  <span data-ttu-id="b709a-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b709a-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="b709a-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="b709a-111">Arguments</span></span>| <span data-ttu-id="b709a-112">Eine Zeichenfolge mit Argumenten, die wie vorhanden an den Prozess übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="b709a-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="b709a-113">Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu.</span><span class="sxs-lookup"><span data-stu-id="b709a-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="b709a-114">Path</span><span class="sxs-lookup"><span data-stu-id="b709a-114">Path</span></span>| <span data-ttu-id="b709a-115">Die Pfade zu den ausführbaren Prozessdateien.</span><span class="sxs-lookup"><span data-stu-id="b709a-115">The paths to the process executables.</span></span> <span data-ttu-id="b709a-116">Wenn es sich um die Namen der ausführbaren Dateien (keine vollqualifizierten Pfade) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable **Path** (`$env:Path`), um die Dateien zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="b709a-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="b709a-117">Wenn die Werte dieser Eigenschaft vollqualifizierte Pfade sind, verwendet DSC nicht die Umgebungsvariable **Path**, um die Dateien zu finden, und löst einen Fehler aus, wenn beliebige der Pfade nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b709a-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="b709a-118">Relative Pfade sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="b709a-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="b709a-119">Credential</span><span class="sxs-lookup"><span data-stu-id="b709a-119">Credential</span></span>| <span data-ttu-id="b709a-120">Gibt die Anmeldeinformationen zum Starten des Prozesses an.</span><span class="sxs-lookup"><span data-stu-id="b709a-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="b709a-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="b709a-121">Ensure</span></span>| <span data-ttu-id="b709a-122">Gibt an, ob der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b709a-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="b709a-123">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b709a-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="b709a-124">Legen Sie sie andernfalls auf „Absent“ fest.</span><span class="sxs-lookup"><span data-stu-id="b709a-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="b709a-125">Die Standardeinstellung ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="b709a-125">The default is "Present".</span></span>|
| <span data-ttu-id="b709a-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="b709a-126">StandardErrorPath</span></span>| <span data-ttu-id="b709a-127">Der Pfad, in den der Prozess Standardfehler schreibt.</span><span class="sxs-lookup"><span data-stu-id="b709a-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="b709a-128">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="b709a-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="b709a-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="b709a-129">StandardInputPath</span></span>| <span data-ttu-id="b709a-130">Der Datenstrom, aus dem der Prozess die Standardeingabe empfängt.</span><span class="sxs-lookup"><span data-stu-id="b709a-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="b709a-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="b709a-131">StandardOutputPath</span></span>| <span data-ttu-id="b709a-132">Der Pfad der Datei, in die der Prozess die Standardausgabe schreibt.</span><span class="sxs-lookup"><span data-stu-id="b709a-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="b709a-133">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="b709a-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="b709a-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="b709a-134">WorkingDirectory</span></span>| <span data-ttu-id="b709a-135">Der Speicherort, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b709a-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="b709a-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b709a-136">DependsOn</span></span> | <span data-ttu-id="b709a-137">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="b709a-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b709a-138">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **_ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft so: DependsOn = "[ResourceType]ResourceName".</span><span class="sxs-lookup"><span data-stu-id="b709a-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|