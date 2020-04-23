---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Konfigurationen
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954497"
---
# <a name="dsc-configurations"></a><span data-ttu-id="c0681-103">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="c0681-103">DSC Configurations</span></span>

> <span data-ttu-id="c0681-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c0681-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c0681-105">DSC-Konfigurationen sind PowerShell-Skripts, die eine besondere Art von Funktion definieren.</span><span class="sxs-lookup"><span data-stu-id="c0681-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="c0681-106">Zum Definieren einer Konfiguration verwenden Sie das PowerShell-Schlüsselwort **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="c0681-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="c0681-107">Speichern Sie das Skript als `.ps1`-Datei.</span><span class="sxs-lookup"><span data-stu-id="c0681-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="c0681-108">Konfigurationssyntax</span><span class="sxs-lookup"><span data-stu-id="c0681-108">Configuration syntax</span></span>

<span data-ttu-id="c0681-109">Ein Konfigurationsskript besteht aus den folgenden Teilen:</span><span class="sxs-lookup"><span data-stu-id="c0681-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="c0681-110">Dem **Configuration**-Block.</span><span class="sxs-lookup"><span data-stu-id="c0681-110">The **Configuration** block.</span></span> <span data-ttu-id="c0681-111">Dies ist die äußerste Skriptblock.</span><span class="sxs-lookup"><span data-stu-id="c0681-111">This is the outermost script block.</span></span> <span data-ttu-id="c0681-112">Sie definieren ihn mithilfe des Schlüsselworts **Configuration** und der Angabe eines Namens.</span><span class="sxs-lookup"><span data-stu-id="c0681-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="c0681-113">In diesem Fall lautet der Name der Konfiguration „MyDscConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="c0681-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="c0681-114">Mindestens einem **Node**-Block.</span><span class="sxs-lookup"><span data-stu-id="c0681-114">One or more **Node** blocks.</span></span> <span data-ttu-id="c0681-115">Diese Blöcke definieren die Knoten (Computer oder VMs), die Sie konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c0681-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="c0681-116">Bei der obigen Konfiguration gibt es einen **Node**-Block für den Computer „TEST-PC1“.</span><span class="sxs-lookup"><span data-stu-id="c0681-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="c0681-117">Der Node-Block kann mehrere Computernamen akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="c0681-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="c0681-118">Mindestens einen Ressourcenblock.</span><span class="sxs-lookup"><span data-stu-id="c0681-118">One or more resource blocks.</span></span> <span data-ttu-id="c0681-119">In diesen Blöcken werden die Eigenschaften der Ressourcen festlegt, die konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="c0681-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="c0681-120">In diesem Fall gibt es zwei Ressourcenblöcke, die beide die Ressource „WindowsFeature“ aufrufen.</span><span class="sxs-lookup"><span data-stu-id="c0681-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="c0681-121">Innerhalb eines **Configuration**-Blocks sind alle Aktionen möglich, die Sie normalerweise mit einer PowerShell-Funktion ausführen.</span><span class="sxs-lookup"><span data-stu-id="c0681-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="c0681-122">Wenn Sie beispielsweise im vorherigen Beispiel den Namen des Zielcomputers nicht in der Konfiguration hart codieren möchten, können Sie einen Parameter für den Knotennamen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="c0681-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="c0681-123">In diesem Beispiel geben Sie den Namen des Knotens an, indem Sie ihn als **ComputerName**-Parameter übergeben, wenn Sie die Konfiguration kompilieren.</span><span class="sxs-lookup"><span data-stu-id="c0681-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="c0681-124">Der Standardname ist „localhost“.</span><span class="sxs-lookup"><span data-stu-id="c0681-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="c0681-125">Der **Node**-Block kann auch mehrere Computernamen akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="c0681-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="c0681-126">Im Beispiel oben können Sie entweder den `-ComputerName`-Parameter verwenden oder eine durch Trennzeichen getrennte Liste der Computer direkt an den **Node** Block übergeben.</span><span class="sxs-lookup"><span data-stu-id="c0681-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="c0681-127">Wenn Sie eine Liste von Computern für den **Node**-Block aus einer Konfiguration angeben, müssen Sie Arraynotation verwenden.</span><span class="sxs-lookup"><span data-stu-id="c0681-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="c0681-128">Kompilieren der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c0681-128">Compiling the configuration</span></span>

<span data-ttu-id="c0681-129">Bevor Sie eine Konfiguration anwenden können, müssen Sie sie in einem MOF-Dokument kompilieren.</span><span class="sxs-lookup"><span data-stu-id="c0681-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="c0681-130">Dazu rufen Sie die Konfiguration wie eine PowerShell-Funktion auf.</span><span class="sxs-lookup"><span data-stu-id="c0681-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="c0681-131">Die letzte Zeile des Beispiels, die nur den Namen der Konfiguration enthält, ruft die Konfiguration auf.</span><span class="sxs-lookup"><span data-stu-id="c0681-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="c0681-132">Damit eine Konfiguration aufgerufen werden kann, muss sie sich (wie jede andere PowerShell-Funktion) im globalen Bereich befinden.</span><span class="sxs-lookup"><span data-stu-id="c0681-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="c0681-133">Dies erfolgt, indem Sie das Skript mit „Dot-Sourcing“ ausführen oder das Konfigurationsskript durch Drücken von F5 oder Klicken auf die Schaltfläche **Skript ausführen** in der integrierte Skriptumgebung starten.</span><span class="sxs-lookup"><span data-stu-id="c0681-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="c0681-134">Um das Skript mit „Dot-Sourcing“ ausführen, rufen Sie den Befehl `. .\myConfig.ps1` auf, wobei `myConfig.ps1` der Name der Skriptdatei mit Ihrer Konfiguration ist.</span><span class="sxs-lookup"><span data-stu-id="c0681-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="c0681-135">Beim Aufruf der Konfiguration erfolgt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c0681-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="c0681-136">Alle Variablen werden aufgelöst.</span><span class="sxs-lookup"><span data-stu-id="c0681-136">Resolves all variables</span></span>
- <span data-ttu-id="c0681-137">Im aktuellen Verzeichnis wird ein Ordner mit dem Namen der Konfiguration erstellt.</span><span class="sxs-lookup"><span data-stu-id="c0681-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="c0681-138">Eine Datei namens _NodeName.mof_ wird im neuen Verzeichnis erstellt, wobei _NodeName_ der Name des Zielknotens der Konfiguration ist.</span><span class="sxs-lookup"><span data-stu-id="c0681-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="c0681-139">Wenn mehrere Knoten vorhanden sind, wird eine MOF-Datei für jeden Knoten erstellt.</span><span class="sxs-lookup"><span data-stu-id="c0681-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="c0681-140">Die MOF-Datei enthält alle Konfigurationsinformationen für den Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="c0681-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="c0681-141">Aus diesem Grund ist es wichtig, sie geschützt zu halten.</span><span class="sxs-lookup"><span data-stu-id="c0681-141">Because of this, it's important to keep it secure.</span></span>
> <span data-ttu-id="c0681-142">Weitere Informationen finden Sie unter [Schützen der MOF-Datei](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="c0681-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="c0681-143">Das Kompilieren der ersten oben gezeigten Konfiguration führt zur folgenden Ordnerstruktur:</span><span class="sxs-lookup"><span data-stu-id="c0681-143">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="c0681-144">Wenn die Konfiguration wie im zweiten Beispiel einen Parameter verwendet, muss dieser zur Kompilierungszeit angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c0681-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="c0681-145">Das sieht dann so aus:</span><span class="sxs-lookup"><span data-stu-id="c0681-145">Here's how that would look:</span></span>

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

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="c0681-146">Verwenden neuer Ressourcen in Ihrer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c0681-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="c0681-147">Wenn Sie die vorherigen Beispielen ausgeführt haben, werden Sie vielleicht die Warnung bemerkt haben, dass Sie eine Ressource verwendet haben, ohne sie explizit zu importieren.</span><span class="sxs-lookup"><span data-stu-id="c0681-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="c0681-148">Derzeit gehören 12 Ressourcen zum Funktionsumfang von DSC im „PSDesiredStateConfiguration“-Modul.</span><span class="sxs-lookup"><span data-stu-id="c0681-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="c0681-149">Das Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) kann verwendet werden, um zu bestimmen, welche Ressourcen im System installiert sind und dem LCM zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c0681-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="c0681-150">Nachdem diese Module in `$env:PSModulePath` abgelegt und von [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) ordnungsgemäß erkannt wurden, müssen sie dennoch in Ihre Konfiguration geladen werden.</span><span class="sxs-lookup"><span data-stu-id="c0681-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="c0681-151">**Import-DscResource** ist ein dynamisches Schlüsselwort, das nur in einem **Configuration**-Block erkannt werden kann. Es handelt sich nicht um ein Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0681-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="c0681-152">**Import-DscResource** unterstützt zwei Parameter:</span><span class="sxs-lookup"><span data-stu-id="c0681-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="c0681-153">**ModuleName** ist die empfohlene Methode der Verwendung von **Import DscResource**.</span><span class="sxs-lookup"><span data-stu-id="c0681-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="c0681-154">Dieser Parameter akzeptiert den Namen des Moduls mit den Ressourcen, die importiert werden sollen, (sowie einem Zeichenfolgenarray mit Modulnamen).</span><span class="sxs-lookup"><span data-stu-id="c0681-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="c0681-155">**Name** ist der Name der zu importierenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="c0681-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="c0681-156">Dies ist nicht der Anzeigename, der als „Name“ von [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zurückgegeben wird, sondern der Klassennamen, der verwendet wird, wenn Sie das Ressourcenschema definieren (wird als **ResourceType** von [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zurückgegeben).</span><span class="sxs-lookup"><span data-stu-id="c0681-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="c0681-157">Weitere Informationen zur Verwendung von `Import-DSCResource` finden Sie unter [Verwenden von „Import-DSCResource“](import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="c0681-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="c0681-158">Unterschiede zwischen PowerShell v4 und v5</span><span class="sxs-lookup"><span data-stu-id="c0681-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="c0681-159">Es gibt Unterschiede in Bezug darauf, wo DSC-Ressourcen in PowerShell 4.0 gespeichert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="c0681-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="c0681-160">Weitere Informationen finden Sie unter [Ressourcenspeicherort](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="c0681-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="c0681-161">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c0681-161">See Also</span></span>

- [<span data-ttu-id="c0681-162">Windows PowerShell DSC – Übersicht</span><span class="sxs-lookup"><span data-stu-id="c0681-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="c0681-163">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c0681-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="c0681-164">Konfigurieren des lokalen Konfigurations-Managers</span><span class="sxs-lookup"><span data-stu-id="c0681-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
