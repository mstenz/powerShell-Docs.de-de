---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Konfigurationen
ms.openlocfilehash: d98bf0e85c12103d9b1eeded155bab1af364bd4c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-configurations"></a><span data-ttu-id="37e8c-103">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="37e8c-103">DSC Configurations</span></span>

><span data-ttu-id="37e8c-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="37e8c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="37e8c-105">DSC-Konfigurationen sind PowerShell-Skripts, die eine besondere Art von Funktion definieren.</span><span class="sxs-lookup"><span data-stu-id="37e8c-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="37e8c-106">Zum Definieren einer Konfiguration verwenden Sie das PowerShell-Schlüsselwort **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="37e8c-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="37e8c-107">Speichern Sie das Skript als PS1-Datei.</span><span class="sxs-lookup"><span data-stu-id="37e8c-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="37e8c-108">Konfigurationssyntax</span><span class="sxs-lookup"><span data-stu-id="37e8c-108">Configuration syntax</span></span>

<span data-ttu-id="37e8c-109">Ein Konfigurationsskript besteht aus den folgenden Teilen:</span><span class="sxs-lookup"><span data-stu-id="37e8c-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="37e8c-110">Dem **Configuration**-Block.</span><span class="sxs-lookup"><span data-stu-id="37e8c-110">The **Configuration** block.</span></span> <span data-ttu-id="37e8c-111">Dies ist die äußerste Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="37e8c-111">This is the outermost script block.</span></span> <span data-ttu-id="37e8c-112">Sie definieren ihn mithilfe des Schlüsselworts **Configuration** und der Angabe eines Namens.</span><span class="sxs-lookup"><span data-stu-id="37e8c-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="37e8c-113">In diesem Fall lautet der Name der Konfiguration „MyDscConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="37e8c-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="37e8c-114">Mindestens einem **Node**-Block.</span><span class="sxs-lookup"><span data-stu-id="37e8c-114">One or more **Node** blocks.</span></span> <span data-ttu-id="37e8c-115">Diese Blöcke definieren die Knoten (Computer oder VMs), die Sie konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="37e8c-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="37e8c-116">Bei der obigen Konfiguration gibt es einen **Node**-Block für den Computer „TEST-PC1“.</span><span class="sxs-lookup"><span data-stu-id="37e8c-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="37e8c-117">Mindestens einen Ressourcenblock.</span><span class="sxs-lookup"><span data-stu-id="37e8c-117">One or more resource blocks.</span></span> <span data-ttu-id="37e8c-118">In diesen Blöcken werden die Eigenschaften der Ressourcen festlegt, die konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="37e8c-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="37e8c-119">In diesem Fall gibt es zwei Ressourcenblöcke, die beide die Ressource „WindowsFeature“ aufrufen.</span><span class="sxs-lookup"><span data-stu-id="37e8c-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="37e8c-120">Innerhalb eines **Configuration**-Blocks sind alle Aktionen möglich, die Sie normalerweise mit einer PowerShell-Funktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="37e8c-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="37e8c-121">Wenn Sie beispielsweise im vorherigen Beispiel den Namen des Zielcomputers nicht in der Konfiguration hart codieren möchten, können Sie einen Parameter für den Knotennamen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="37e8c-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName

```

<span data-ttu-id="37e8c-122">In diesem Beispiel geben Sie den Namen des Knotens an, indem Sie ihn als **ComputerName**-Parameter übergeben, wenn Sie die Konfiguration kompilieren.</span><span class="sxs-lookup"><span data-stu-id="37e8c-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="37e8c-123">Der Standardname ist „localhost“.</span><span class="sxs-lookup"><span data-stu-id="37e8c-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="37e8c-124">Kompilieren der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="37e8c-124">Compiling the configuration</span></span>

<span data-ttu-id="37e8c-125">Bevor Sie eine Konfiguration anwenden können, müssen Sie sie in einem MOF-Dokument kompilieren.</span><span class="sxs-lookup"><span data-stu-id="37e8c-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="37e8c-126">Dazu rufen Sie die Konfiguration wie eine PowerShell-Funktion auf.</span><span class="sxs-lookup"><span data-stu-id="37e8c-126">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="37e8c-127">Die letzte Zeile des Beispiels, die nur den Namen der Konfiguration enthält, ruft die Konfiguration auf.</span><span class="sxs-lookup"><span data-stu-id="37e8c-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="37e8c-128">**Hinweis:** Damit eine Konfiguration aufgerufen werden kann, muss sie sich (wie jede andere PowerShell-Funktion) im globalen Bereich befinden.</span><span class="sxs-lookup"><span data-stu-id="37e8c-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
><span data-ttu-id="37e8c-129">Dies erfolgt, indem Sie das Skript mit „Dot-Sourcing“ ausführen oder das Konfigurationsskript durch Drücken von F5 oder Klicken auf die Schaltfläche **Skript ausführen** in der integrierte Skriptumgebung starten.</span><span class="sxs-lookup"><span data-stu-id="37e8c-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
><span data-ttu-id="37e8c-130">Um das Skript mit „Dot-Sourcing“ ausführen, rufen Sie den Befehl `. .\myConfig.ps1` auf, wobei `myConfig.ps1` der Name der Skriptdatei mit Ihrer Konfiguration ist.</span><span class="sxs-lookup"><span data-stu-id="37e8c-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="37e8c-131">Beim Aufruf der Konfiguration erfolgt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="37e8c-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="37e8c-132">Alle Variablen werden aufgelöst.</span><span class="sxs-lookup"><span data-stu-id="37e8c-132">Resolves all variables</span></span>
- <span data-ttu-id="37e8c-133">Im aktuellen Verzeichnis wird ein Ordner mit dem Namen der Konfiguration erstellt.</span><span class="sxs-lookup"><span data-stu-id="37e8c-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="37e8c-134">Eine Datei namens _NodeName.mof_ wird im neuen Verzeichnis erstellt, wobei _NodeName_ der Name des Zielknotens der Konfiguration ist.</span><span class="sxs-lookup"><span data-stu-id="37e8c-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
    <span data-ttu-id="37e8c-135">Wenn mehrere Knoten vorhanden sind, wird eine MOF-Datei für jeden Knoten erstellt.</span><span class="sxs-lookup"><span data-stu-id="37e8c-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="37e8c-136">**Hinweis:**: Die MOF-Datei enthält alle Konfigurationsinformationen für den Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="37e8c-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="37e8c-137">Aus diesem Grund ist es wichtig, sie geschützt zu halten.</span><span class="sxs-lookup"><span data-stu-id="37e8c-137">Because of this, it’s important to keep it secure.</span></span>
><span data-ttu-id="37e8c-138">Weitere Informationen finden Sie unter [Schützen der MOF-Datei](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="37e8c-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="37e8c-139">Das Kompilieren der ersten oben gezeigten Konfiguration führt zur folgenden Ordnerstruktur:</span><span class="sxs-lookup"><span data-stu-id="37e8c-139">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="37e8c-140">Wenn die Konfiguration wie im zweiten Beispiel einen Parameter verwendet, muss dieser zur Kompilierungszeit angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="37e8c-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="37e8c-141">Das sieht dann so aus:</span><span class="sxs-lookup"><span data-stu-id="37e8c-141">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-dependson"></a><span data-ttu-id="37e8c-142">Verwenden von „DependsOn“</span><span class="sxs-lookup"><span data-stu-id="37e8c-142">Using DependsOn</span></span>

<span data-ttu-id="37e8c-143">Eine nützliches DSC-Schlüsselwort ist **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="37e8c-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="37e8c-144">In der Regel (jedoch nicht unbedingt immer) wendet DSC die Ressourcen in der Reihenfolge an, die der sie in der Konfiguration angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="37e8c-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="37e8c-145">**DependsOn** gibt hingegen an, welche Ressourcen von anderen Ressourcen abhängig sind. Der LCM stellt sicher, dass sie in der richtigen Reihenfolge angewendet werden, und zwar unabhängig von der Reihenfolge, in der Ressourceninstanzen definiert sind.</span><span class="sxs-lookup"><span data-stu-id="37e8c-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="37e8c-146">Eine Konfiguration kann z. B. angeben, dass eine Instanz der Ressource **User** vom Vorhandensein einer **Group**-Instanz abhängig ist:</span><span class="sxs-lookup"><span data-stu-id="37e8c-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="37e8c-147">Verwenden neuer Ressourcen in Ihrer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="37e8c-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="37e8c-148">Wenn Sie die vorherigen Beispielen ausgeführt haben, werden Sie vielleicht die Warnung bemerkt haben, dass Sie eine Ressource verwendet haben, ohne sie explizit zu importieren.</span><span class="sxs-lookup"><span data-stu-id="37e8c-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="37e8c-149">Derzeit gehören 12 Ressourcen zum Funktionsumfang von DSC im „PSDesiredStateConfiguration“-Modul.</span><span class="sxs-lookup"><span data-stu-id="37e8c-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="37e8c-150">Andere Ressourcen in externen Modulen müssen in `$env:PSModulePath` eingefügt werden, damit sie vom lokalen Konfigurations-Manager (LCM) erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="37e8c-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="37e8c-151">Das neue Cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) kann verwendet werden, um zu bestimmen, welche Ressourcen im System installiert sind und dem LCM zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="37e8c-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="37e8c-152">Nachdem diese Module in `$env:PSModulePath` abgelegt und von [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) ordnungsgemäß erkannt wurden, müssen sie dennoch in Ihre Konfiguration geladen werden.</span><span class="sxs-lookup"><span data-stu-id="37e8c-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="37e8c-153">**Import-DscResource** ist ein dynamisches Schlüsselwort, das nur in einem **Configuration**-Block erkannt werden kann (d. h. es ist kein Cmdlet).</span><span class="sxs-lookup"><span data-stu-id="37e8c-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="37e8c-154">**Import-DscResource** unterstützt zwei Parameter:</span><span class="sxs-lookup"><span data-stu-id="37e8c-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="37e8c-155">**ModuleName** ist die empfohlene Methode der Verwendung von **Import DscResource**.</span><span class="sxs-lookup"><span data-stu-id="37e8c-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="37e8c-156">Dieser Parameter akzeptiert den Namen des Moduls mit den Ressourcen, die importiert werden sollen, (sowie einem Zeichenfolgenarray mit Modulnamen).</span><span class="sxs-lookup"><span data-stu-id="37e8c-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="37e8c-157">**Name** ist der Name der zu importierenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="37e8c-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="37e8c-158">Dies ist nicht der Anzeigename, der als „Name“ von [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) zurückgegeben wird, sondern der Klassennamen, der verwendet wird, wenn Sie das Ressourcenschema definieren (wird als **ResourceType** von [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) zurückgegeben).</span><span class="sxs-lookup"><span data-stu-id="37e8c-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="37e8c-159">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="37e8c-159">See Also</span></span>
* [<span data-ttu-id="37e8c-160">Windows PowerShell DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="37e8c-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="37e8c-161">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="37e8c-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="37e8c-162">Konfigurieren des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="37e8c-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)
