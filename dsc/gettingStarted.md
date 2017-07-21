---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Erste Schritte mit Windows PowerShell DSC
ms.openlocfilehash: 403badd11749cfa5c6a5d07e1b537fa3a5f954da
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="2492f-103">Erste Schritte mit Windows PowerShell DSC</span><span class="sxs-lookup"><span data-stu-id="2492f-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="2492f-104">In dieser Anleitung wird erläutert, wie PowerShell DSC-Dokumente erstellt und auf Computer angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="2492f-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="2492f-105">Grundkenntnisse von PowerShell-Cmdlets, Modulen und Funktionen werden vorausgesetzt.</span><span class="sxs-lookup"><span data-stu-id="2492f-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span> 


## <a name="create-a-configuration"></a><span data-ttu-id="2492f-106">Erstellen einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="2492f-106">Create a Configuration</span></span> ##

<span data-ttu-id="2492f-107">[**Konfigurationen**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) sind Dokumente, die eine Umgebung beschreiben.</span><span class="sxs-lookup"><span data-stu-id="2492f-107">[**Configurations**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="2492f-108">Umgebungen bestehen aus **Knoten**, bei denen es sich um virtuelle oder physische Computer handelt.</span><span class="sxs-lookup"><span data-stu-id="2492f-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span> 

<span data-ttu-id="2492f-109">Konfigurationen können verschiedene Formen haben.</span><span class="sxs-lookup"><span data-stu-id="2492f-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="2492f-110">Die einfachste Möglichkeit zum Erstellen einer neuen Konfiguration ist die Erstellung einer PS1-Datei (PowerShell-Skript).</span><span class="sxs-lookup"><span data-stu-id="2492f-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="2492f-111">Öffnen Sie hierfür den Editor Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="2492f-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="2492f-112">Die PowerShell ISE ist eine gute Wahl, da sie DSC nativ versteht.</span><span class="sxs-lookup"><span data-stu-id="2492f-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="2492f-113">Speichern Sie Folgendes in einer PS1-Datei:</span><span class="sxs-lookup"><span data-stu-id="2492f-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="2492f-114">Teile einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="2492f-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="2492f-115">**Configuration** ist ein Schlüsselwort, das PowerShell 4.0 hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="2492f-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="2492f-116">Es bezeichnet eine spezielle Art von PowerShell-Funktion, die von DSC verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2492f-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="2492f-117">In diesem Beispiel heißt die Funktion „myFirstConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="2492f-117">In this example, the function is named myFirstConfiguration.</span></span> 

<span data-ttu-id="2492f-118">Die nächste Zeile ist eine Importanweisung wie zum Importieren eines Moduls.</span><span class="sxs-lookup"><span data-stu-id="2492f-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="2492f-119">Sie wird weiter unten besprochen.</span><span class="sxs-lookup"><span data-stu-id="2492f-119">It will be discussed later on.</span></span>

<span data-ttu-id="2492f-120">„Node“ definiert den Namen des Computers, auf den diese Konfiguration angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="2492f-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="2492f-121">Obwohl diese Konfiguration lokal bearbeitet wird, können Konfigurationen auch für Remoteknoten gelten.</span><span class="sxs-lookup"><span data-stu-id="2492f-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span> 

<span data-ttu-id="2492f-122">Knoten können Computernamen oder IP-Adressen haben.</span><span class="sxs-lookup"><span data-stu-id="2492f-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="2492f-123">Ein einzelnes Konfigurationsdokument kann mehrere Knoten enthalten.</span><span class="sxs-lookup"><span data-stu-id="2492f-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="2492f-124">Mithilfe von [Konfigurationsdaten](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) können Sie die gleiche Konfiguration auch auf mehrere Knoten anwenden.</span><span class="sxs-lookup"><span data-stu-id="2492f-124">Using [configuration data](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="2492f-125">In diesem Fall heißt der Knoten „localhost“, was sich auf den lokalen Computer bezieht.</span><span class="sxs-lookup"><span data-stu-id="2492f-125">In this case, the node is "localhost" - which means the local computer.</span></span> 

<span data-ttu-id="2492f-126">Das nächste Element ist eine [**Ressource**](https://msdn.microsoft.com/en-us/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="2492f-126">The next item is a [**resource**](https://msdn.microsoft.com/en-us/powershell/dsc/resources).</span></span> <span data-ttu-id="2492f-127">Ressourcen sind Bausteine von Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2492f-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="2492f-128">Jede Ressource ist ein Modul, das die Implementierungslogik eines einzelnen Aspekts eines Computers definiert.</span><span class="sxs-lookup"><span data-stu-id="2492f-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="2492f-129">Durch Ausführen von **Get-DscResource** in PowerShell können Sie alle Ressourcen auf Ihrem Computer anzeigen.</span><span class="sxs-lookup"><span data-stu-id="2492f-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="2492f-130">Ressourcen müssen auf dem lokalen Computer vorhanden sein und importiert werden, ehe sie in einer Konfiguration mit **Import-DscResource** in der zweiten Zeile dieser Konfiguration verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="2492f-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span> 

<span data-ttu-id="2492f-131">**Anwenden einer Konfiguration**</span><span class="sxs-lookup"><span data-stu-id="2492f-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="2492f-132">Wenn das obige Skript gespeichert und ausgeführt wird, erfolgt keine Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="2492f-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="2492f-133">Das liegt daran, dass eine Konfiguration bloß eine Funktion ist und dass das obige Skript die Funktion zwar definiert, sie aber noch nicht ausgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="2492f-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="2492f-134">Nachdem die Funktion definiert wurde, muss sie aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="2492f-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="2492f-135">Bei ihrer Ausführung überprüfen Konfigurationsfunktionen, ob die Konfiguration gültig ist.</span><span class="sxs-lookup"><span data-stu-id="2492f-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="2492f-136">Sie darf keine Syntaxfehler aufweisen, für Ressourcen müssen alle Pflichtparameter definiert sein, und alle Ressourcen müssen vor der Ausführung importiert werden.</span><span class="sxs-lookup"><span data-stu-id="2492f-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="2492f-137">Nachdem die Konfiguration ausgeführt wurde, wird ein Ordner mit dem Namen der Konfiguration und einer **MOF-Datei** für jeden Knoten in der Konfiguration erstellt.</span><span class="sxs-lookup"><span data-stu-id="2492f-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="2492f-138">Die MOF-Datei ist ein auf Standards basierendes Verwaltungsformat, das von PowerShell DSC für die Kommunikation über das Netzwerk verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2492f-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="2492f-139">So wenden Sie eine Konfiguration an:</span><span class="sxs-lookup"><span data-stu-id="2492f-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="2492f-140">Dadurch wird ein PowerShell-Auftrag erstellt, der auf den Knoten in der Konfiguration ausgeführt wird, um diese zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="2492f-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="2492f-141">Rufen Sie „-Wait“ auf, um die Ausgabe des Auftrags anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="2492f-141">To see the output of the job, use -Wait.</span></span> 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```

