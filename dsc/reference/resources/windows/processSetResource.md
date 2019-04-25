---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „ProcessSet“
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077108"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="5a169-103">DSC-Ressource „WindowsProcess“</span><span class="sxs-lookup"><span data-stu-id="5a169-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="5a169-104">_Gilt für: Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="5a169-104">_Applies To: Windows PowerShell 5.0_</span></span>

<span data-ttu-id="5a169-105">Die Ressource **ProcessSet** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="5a169-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="5a169-106">Diese Ressource ist eine [zusammengesetzte Ressource](../../../resources/authoringResourceComposite.md), die die Ressource [WindowsProcess](windowsProcessResource.md) für jede Gruppe aufruft, die im `GroupName`-Parameter angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="5a169-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a169-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5a169-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5a169-108">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="5a169-108">Properties</span></span>

| <span data-ttu-id="5a169-109">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="5a169-109">Property</span></span> | <span data-ttu-id="5a169-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5a169-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5a169-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="5a169-111">Arguments</span></span>| <span data-ttu-id="5a169-112">Eine Zeichenfolge mit Argumenten, die wie vorhanden an den Prozess übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="5a169-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="5a169-113">Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu.</span><span class="sxs-lookup"><span data-stu-id="5a169-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="5a169-114">Path</span><span class="sxs-lookup"><span data-stu-id="5a169-114">Path</span></span>| <span data-ttu-id="5a169-115">Die Pfade zu den ausführbaren Prozessdateien.</span><span class="sxs-lookup"><span data-stu-id="5a169-115">The paths to the process executables.</span></span> <span data-ttu-id="5a169-116">Wenn es sich um die Namen der ausführbaren Dateien (keine vollqualifizierten Pfade) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable **Path** (`$env:Path`), um die Dateien zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="5a169-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="5a169-117">Wenn die Werte dieser Eigenschaft vollqualifizierte Pfade sind, verwendet DSC nicht die Umgebungsvariable **Path**, um die Dateien zu finden, und löst einen Fehler aus, wenn beliebige der Pfade nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5a169-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="5a169-118">Relative Pfade sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="5a169-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="5a169-119">Credential</span><span class="sxs-lookup"><span data-stu-id="5a169-119">Credential</span></span>| <span data-ttu-id="5a169-120">Gibt die Anmeldeinformationen zum Starten des Prozesses an.</span><span class="sxs-lookup"><span data-stu-id="5a169-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="5a169-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="5a169-121">Ensure</span></span>| <span data-ttu-id="5a169-122">Gibt an, ob der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="5a169-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="5a169-123">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="5a169-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="5a169-124">Legen Sie sie andernfalls auf „Absent“ fest.</span><span class="sxs-lookup"><span data-stu-id="5a169-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="5a169-125">Die Standardeinstellung ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="5a169-125">The default is "Present".</span></span>|
| <span data-ttu-id="5a169-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="5a169-126">StandardErrorPath</span></span>| <span data-ttu-id="5a169-127">Der Pfad, in den der Prozess Standardfehler schreibt.</span><span class="sxs-lookup"><span data-stu-id="5a169-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="5a169-128">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="5a169-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="5a169-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="5a169-129">StandardInputPath</span></span>| <span data-ttu-id="5a169-130">Der Datenstrom, aus dem der Prozess die Standardeingabe empfängt.</span><span class="sxs-lookup"><span data-stu-id="5a169-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="5a169-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="5a169-131">StandardOutputPath</span></span>| <span data-ttu-id="5a169-132">Der Pfad der Datei, in die der Prozess die Standardausgabe schreibt.</span><span class="sxs-lookup"><span data-stu-id="5a169-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="5a169-133">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="5a169-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="5a169-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="5a169-134">WorkingDirectory</span></span>| <span data-ttu-id="5a169-135">Der Speicherort, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5a169-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="5a169-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5a169-136">DependsOn</span></span> | <span data-ttu-id="5a169-137">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="5a169-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5a169-138">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **_ResourceType** ist, lautet die Syntax für die Verwendung dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5a169-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
