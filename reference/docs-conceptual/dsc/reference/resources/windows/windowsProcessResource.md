---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „WindowsProcess“
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952837"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="1cc0b-103">DSC-Ressource „WindowsProcess“</span><span class="sxs-lookup"><span data-stu-id="1cc0b-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="1cc0b-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="1cc0b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1cc0b-105">Die Ressource **WindowsProcess** in Windows PowerShell DSC bietet einen Mechanismus zum Konfigurieren von Prozessen auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1cc0b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1cc0b-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1cc0b-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="1cc0b-107">Properties</span></span>

|<span data-ttu-id="1cc0b-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="1cc0b-108">Property</span></span> |<span data-ttu-id="1cc0b-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1cc0b-109">Description</span></span> |
|---|---|
|<span data-ttu-id="1cc0b-110">Argumente</span><span class="sxs-lookup"><span data-stu-id="1cc0b-110">Arguments</span></span> |<span data-ttu-id="1cc0b-111">Gibt eine Zeichenfolge von Argumenten an, die wie vorhanden an den Prozess übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="1cc0b-112">Wenn Sie mehrere Argumente übergeben müssen, fügen Sie sie alle dieser Zeichenfolge hinzu.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="1cc0b-113">Pfad</span><span class="sxs-lookup"><span data-stu-id="1cc0b-113">Path</span></span> |<span data-ttu-id="1cc0b-114">Der Pfad zur ausführbaren Prozessdatei.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-114">The path to the process executable.</span></span> <span data-ttu-id="1cc0b-115">Wenn es sich um den Namen der ausführbaren Datei (keinen vollqualifizierten Pfad) handelt, durchsucht die Ressource „DSC“ die Umgebungsvariable `$env:Path`, um die ausführbare Datei zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="1cc0b-116">Wenn der Werte dieser Eigenschaft ein vollqualifizierter Pfad ist, verwendet DSC nicht die Umgebungsvariable `$env:Path`, um die Dateien zu finden, und löst einen Fehler aus, wenn der Pfad nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="1cc0b-117">Relative Pfade sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="1cc0b-118">Credential</span><span class="sxs-lookup"><span data-stu-id="1cc0b-118">Credential</span></span> |<span data-ttu-id="1cc0b-119">Gibt die Anmeldeinformationen zum Starten des Prozesses an.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="1cc0b-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="1cc0b-120">StandardErrorPath</span></span> |<span data-ttu-id="1cc0b-121">Gibt den Verzeichnispfad an, in den der Standardfehler geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="1cc0b-122">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="1cc0b-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="1cc0b-123">StandardInputPath</span></span> |<span data-ttu-id="1cc0b-124">Gibt den Standardpfad für die Eingabe an.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="1cc0b-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="1cc0b-125">StandardOutputPath</span></span> |<span data-ttu-id="1cc0b-126">Gibt den Speicherort an, in den die Standardausgabe geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="1cc0b-127">Eine vorhandene Datei wird überschrieben.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="1cc0b-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="1cc0b-128">WorkingDirectory</span></span> |<span data-ttu-id="1cc0b-129">Gibt den Speicherort an, der als das aktuelle Arbeitsverzeichnis für den Prozess verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1cc0b-130">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="1cc0b-130">Common properties</span></span>

|<span data-ttu-id="1cc0b-131">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="1cc0b-131">Property</span></span> |<span data-ttu-id="1cc0b-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1cc0b-132">Description</span></span> |
|---|---|
|<span data-ttu-id="1cc0b-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1cc0b-133">DependsOn</span></span> |<span data-ttu-id="1cc0b-134">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1cc0b-135">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1cc0b-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="1cc0b-136">Ensure</span></span> |<span data-ttu-id="1cc0b-137">Gibt an, ob der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-137">Indicates if the process exists.</span></span> <span data-ttu-id="1cc0b-138">Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass der Prozess vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="1cc0b-139">Legen Sie sie andernfalls auf **Absent** fest.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="1cc0b-140">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="1cc0b-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1cc0b-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="1cc0b-142">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="1cc0b-142">Sets the credential for running the entire resource as.</span></span> |