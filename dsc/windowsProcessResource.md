---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „WindowsProcess“"
ms.openlocfilehash: c34d3cb1d4d9b899b45fba7b4b148a7c977f5365
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="b5673-103">DSC-Ressource „WindowsProcess“</span><span class="sxs-lookup"><span data-stu-id="b5673-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="b5673-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b5673-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b5673-105">Die Ressource **WindowsProcess** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="b5673-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5673-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5673-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="b5673-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="b5673-107">Properties</span></span>
|  <span data-ttu-id="b5673-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b5673-108">Property</span></span>  |  <span data-ttu-id="b5673-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b5673-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="b5673-110">Argumente</span><span class="sxs-lookup"><span data-stu-id="b5673-110">Arguments</span></span>| <span data-ttu-id="b5673-111">Gibt eine Zeichenfolge von Argumenten an, die wie vorhanden an den Prozess übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="b5673-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="b5673-112">Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu.</span><span class="sxs-lookup"><span data-stu-id="b5673-112">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="b5673-113">Path</span><span class="sxs-lookup"><span data-stu-id="b5673-113">Path</span></span>| <span data-ttu-id="b5673-114">Der Pfad zur ausführbaren Prozessdatei.</span><span class="sxs-lookup"><span data-stu-id="b5673-114">The path to the process executable.</span></span> <span data-ttu-id="b5673-115">Wenn es sich um den Namen der ausführbaren Datei (keinen vollqualifizierten Pfad) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable **Path** (`$env:Path`), um die ausführbare Datei zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="b5673-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="b5673-116">Wenn der Werte dieser Eigenschaft ein vollqualifizierter Pfad ist, verwendet DSC nicht die Umgebungsvariable **Path**, um die Dateien zu finden, und löst einen Fehler aus, wenn der Pfad nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b5673-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="b5673-117">Relative Pfade sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="b5673-117">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="b5673-118">Credential</span><span class="sxs-lookup"><span data-stu-id="b5673-118">Credential</span></span>| <span data-ttu-id="b5673-119">Gibt die Anmeldeinformationen zum Starten des Prozesses an.</span><span class="sxs-lookup"><span data-stu-id="b5673-119">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="b5673-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="b5673-120">Ensure</span></span>| <span data-ttu-id="b5673-121">Gibt an, ob der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b5673-121">Indicates if the process exists.</span></span> <span data-ttu-id="b5673-122">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b5673-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="b5673-123">Legen Sie sie andernfalls auf „Absent“ fest.</span><span class="sxs-lookup"><span data-stu-id="b5673-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="b5673-124">Die Standardeinstellung ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="b5673-124">The default is "Present".</span></span>| 
| <span data-ttu-id="b5673-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b5673-125">DependsOn</span></span> | <span data-ttu-id="b5673-126">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="b5673-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b5673-127">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.</span><span class="sxs-lookup"><span data-stu-id="b5673-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\` .</span></span>| 
| <span data-ttu-id="b5673-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="b5673-128">StandardErrorPath</span></span>| <span data-ttu-id="b5673-129">Gibt den Verzeichnispfad an, in den der Standardfehler geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="b5673-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="b5673-130">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="b5673-130">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="b5673-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="b5673-131">StandardInputPath</span></span>| <span data-ttu-id="b5673-132">Gibt den Standardpfad für die Eingabe an.</span><span class="sxs-lookup"><span data-stu-id="b5673-132">Indicates the standard input location.</span></span>| 
| <span data-ttu-id="b5673-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="b5673-133">StandardOutputPath</span></span>| <span data-ttu-id="b5673-134">Gibt den Speicherort an, in den die Standardausgabe geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="b5673-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="b5673-135">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="b5673-135">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="b5673-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="b5673-136">WorkingDirectory</span></span>| <span data-ttu-id="b5673-137">Gibt den Speicherort an, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b5673-137">Indicates the location that will be used as the current working directory for the process.</span></span>| 

