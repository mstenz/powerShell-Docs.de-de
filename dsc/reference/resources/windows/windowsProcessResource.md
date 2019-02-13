---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „WindowsProcess“
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678011"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="00ec3-103">DSC-Ressource „WindowsProcess“</span><span class="sxs-lookup"><span data-stu-id="00ec3-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="00ec3-104">_Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="00ec3-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="00ec3-105">Die Ressource **WindowsProcess** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="00ec3-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="00ec3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="00ec3-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="00ec3-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="00ec3-107">Properties</span></span>

| <span data-ttu-id="00ec3-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="00ec3-108">Property</span></span> | <span data-ttu-id="00ec3-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="00ec3-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="00ec3-110">Argumente</span><span class="sxs-lookup"><span data-stu-id="00ec3-110">Arguments</span></span>| <span data-ttu-id="00ec3-111">Gibt eine Zeichenfolge von Argumenten an, die wie vorhanden an den Prozess übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="00ec3-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="00ec3-112">Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu.</span><span class="sxs-lookup"><span data-stu-id="00ec3-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="00ec3-113">Pfad</span><span class="sxs-lookup"><span data-stu-id="00ec3-113">Path</span></span>| <span data-ttu-id="00ec3-114">Der Pfad zur ausführbaren Prozessdatei.</span><span class="sxs-lookup"><span data-stu-id="00ec3-114">The path to the process executable.</span></span> <span data-ttu-id="00ec3-115">Wenn es sich um den Namen der ausführbaren Datei (keinen vollqualifizierten Pfad) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable **Path** (`$env:Path`), um die ausführbare Datei zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="00ec3-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="00ec3-116">Wenn der Werte dieser Eigenschaft ein vollqualifizierter Pfad ist, verwendet DSC nicht die Umgebungsvariable **Path**, um die Dateien zu finden, und löst einen Fehler aus, wenn der Pfad nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="00ec3-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="00ec3-117">Relative Pfade sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="00ec3-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="00ec3-118">Credential</span><span class="sxs-lookup"><span data-stu-id="00ec3-118">Credential</span></span>| <span data-ttu-id="00ec3-119">Gibt die Anmeldeinformationen zum Starten des Prozesses an.</span><span class="sxs-lookup"><span data-stu-id="00ec3-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="00ec3-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="00ec3-120">Ensure</span></span>| <span data-ttu-id="00ec3-121">Gibt an, ob der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="00ec3-121">Indicates if the process exists.</span></span> <span data-ttu-id="00ec3-122">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="00ec3-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="00ec3-123">Legen Sie sie andernfalls auf „Absent“ fest.</span><span class="sxs-lookup"><span data-stu-id="00ec3-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="00ec3-124">Die Standardeinstellung ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="00ec3-124">The default is "Present".</span></span>|
| <span data-ttu-id="00ec3-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="00ec3-125">DependsOn</span></span> | <span data-ttu-id="00ec3-126">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="00ec3-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="00ec3-127">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für die Verwendung dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="00ec3-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
| <span data-ttu-id="00ec3-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="00ec3-128">StandardErrorPath</span></span>| <span data-ttu-id="00ec3-129">Gibt den Verzeichnispfad an, in den der Standardfehler geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="00ec3-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="00ec3-130">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="00ec3-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="00ec3-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="00ec3-131">StandardInputPath</span></span>| <span data-ttu-id="00ec3-132">Gibt den Standardpfad für die Eingabe an.</span><span class="sxs-lookup"><span data-stu-id="00ec3-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="00ec3-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="00ec3-133">StandardOutputPath</span></span>| <span data-ttu-id="00ec3-134">Gibt den Speicherort an, in den die Standardausgabe geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="00ec3-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="00ec3-135">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="00ec3-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="00ec3-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="00ec3-136">WorkingDirectory</span></span>| <span data-ttu-id="00ec3-137">Gibt den Speicherort an, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="00ec3-137">Indicates the location that will be used as the current working directory for the process.</span></span>|