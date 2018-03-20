---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „Script“"
ms.openlocfilehash: d65a89ceba0b641ccb0ac3dfcc6d5ec1a48dc92a
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-script-resource"></a><span data-ttu-id="8e39f-103">DSC-Ressource „Script“</span><span class="sxs-lookup"><span data-stu-id="8e39f-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="8e39f-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8e39f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8e39f-105">Die Ressource **Script** in Windows PowerShell DSC bietet einen Mechanismus zum Anwenden von Windows PowerShell-Skriptblöcken auf Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="8e39f-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="8e39f-106">Die Ressource `Script` hat die Eigenschaften `GetScript`, `SetScript` und `TestScript`.</span><span class="sxs-lookup"><span data-stu-id="8e39f-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="8e39f-107">Diese Eigenschaften sollten in Skriptblöcken festgelegt werden, die auf jedem Zielknoten ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8e39f-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="8e39f-108">Der Skriptblock `GetScript` sollte eine Hashtabelle zurückgeben, die den Zustand des aktuellen Knotens darstellt.</span><span class="sxs-lookup"><span data-stu-id="8e39f-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="8e39f-109">Die Hashtabelle darf nur den Schlüssel `Result` enthalten, dessen Wert den Typ `String` haben muss.</span><span class="sxs-lookup"><span data-stu-id="8e39f-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="8e39f-110">Es ist keine Rückgabe erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8e39f-110">It is not required to return anything.</span></span> <span data-ttu-id="8e39f-111">DSC macht nichts mit der Ausgabe dieses Skriptblocks.</span><span class="sxs-lookup"><span data-stu-id="8e39f-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="8e39f-112">Der Skriptblock `TestScript` sollte ermitteln, ob der aktuelle Knoten geändert werden muss.</span><span class="sxs-lookup"><span data-stu-id="8e39f-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="8e39f-113">Er sollte `$true` zurückgeben, wenn der Knoten auf dem neuesten Stand ist.</span><span class="sxs-lookup"><span data-stu-id="8e39f-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="8e39f-114">Er sollte `$false` zurückgeben, wenn die Konfiguration des Knotens veraltet ist und von dem Skriptblock `SetScript` aktualisiert werden sollte.</span><span class="sxs-lookup"><span data-stu-id="8e39f-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="8e39f-115">Der Skriptblock `TestScript` wird von DSC aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="8e39f-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="8e39f-116">Der Skriptblock `SetScript` sollte den Knoten ändern.</span><span class="sxs-lookup"><span data-stu-id="8e39f-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="8e39f-117">Er wird von DSC aufgerufen, wenn der Block `TestScript` `$false` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="8e39f-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="8e39f-118">Wenn Sie Variablen aus Ihrem Konfigurationsskript in den Skriptblöcken `GetScript`, `TestScript` oder `SetScript` verwenden müssen, verwenden Sie den Bereich `$using:` (ein Beispiel finden Sie weiter unten).</span><span class="sxs-lookup"><span data-stu-id="8e39f-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="8e39f-119">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e39f-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="8e39f-120">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="8e39f-120">Properties</span></span>

|  <span data-ttu-id="8e39f-121">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="8e39f-121">Property</span></span>  |  <span data-ttu-id="8e39f-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8e39f-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="8e39f-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="8e39f-123">GetScript</span></span>| <span data-ttu-id="8e39f-124">Bietet einen Windows PowerShell-Skriptblock, der beim Aufrufen des Cmdlets [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8e39f-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="8e39f-125">Dieser Block muss eine Hashtabelle zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="8e39f-125">This block must return a hashtable.</span></span> <span data-ttu-id="8e39f-126">Die Hashtabelle darf nur den Schlüssel **Result** enthalten, dessen Wert den Typ **String** haben muss.</span><span class="sxs-lookup"><span data-stu-id="8e39f-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="8e39f-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="8e39f-127">SetScript</span></span>| <span data-ttu-id="8e39f-128">Stellt einen Windows PowerShell-Skriptblock bereit.</span><span class="sxs-lookup"><span data-stu-id="8e39f-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="8e39f-129">Beim Aufruf des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) wird der **TestScript**-Block zuerst ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8e39f-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="8e39f-130">Wenn der **TestScript**-Block **$false** zurückgibt, wird der **SetScript**-Block ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8e39f-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="8e39f-131">Wenn der **TestScript**-Block **$true** zurückgibt, wird der **SetScript**-Block nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8e39f-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="8e39f-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="8e39f-132">TestScript</span></span>| <span data-ttu-id="8e39f-133">Stellt einen Windows PowerShell-Skriptblock bereit.</span><span class="sxs-lookup"><span data-stu-id="8e39f-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="8e39f-134">Beim Aufruf des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) wird dieser Block ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8e39f-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="8e39f-135">Wenn **$false** zurückgegeben wird, wird der „SetScript“-Block ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8e39f-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="8e39f-136">Wenn **$true** zurückgegeben wird, wird der „SetScript“-Block nicht ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8e39f-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="8e39f-137">Der **TestScript**-Block wird auch ausgeführt, wenn Sie das Cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) aufrufen.</span><span class="sxs-lookup"><span data-stu-id="8e39f-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="8e39f-138">In diesem Fall wird der **SetScript**-Block jedoch nicht ausgeführt, ganz gleich, welcher Exitcode vom „TestScript“-Block zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8e39f-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="8e39f-139">Der **TestScript**-Block muss „True“ zurückgeben, wenn die tatsächliche Konfiguration der Konfiguration des gewünschten Zustands entspricht. Falls nicht, muss „False“ zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8e39f-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="8e39f-140">(Die aktuelle Konfiguration des gewünschten Zustands ist die letzte Konfiguration, die auf den Knoten angewendet wurde, der DSC verwendet.)</span><span class="sxs-lookup"><span data-stu-id="8e39f-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="8e39f-141">Credential</span><span class="sxs-lookup"><span data-stu-id="8e39f-141">Credential</span></span>| <span data-ttu-id="8e39f-142">Gibt die Anmeldeinformationen zum Ausführen dieses Skripts an, falls Anmeldeinformationen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="8e39f-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="8e39f-143">DependsOn</span><span class="sxs-lookup"><span data-stu-id="8e39f-143">DependsOn</span></span>| <span data-ttu-id="8e39f-144">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="8e39f-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="8e39f-145">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="8e39f-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="8e39f-146">Beispiel 1</span><span class="sxs-lookup"><span data-stu-id="8e39f-146">Example 1</span></span>
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="8e39f-147">Beispiel 2</span><span class="sxs-lookup"><span data-stu-id="8e39f-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = { 
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="8e39f-148">Diese Ressource schreibt die Version der Konfiguration in eine Textdatei.</span><span class="sxs-lookup"><span data-stu-id="8e39f-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="8e39f-149">Diese Version ist auf dem Clientcomputer verfügbar, aber auf keinem der Knoten, weshalb sie an jeden der Skriptblöcke der `Script`-Ressource mit dem Bereich `using` der PowerShell übergeben werden muss.</span><span class="sxs-lookup"><span data-stu-id="8e39f-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="8e39f-150">Beim Generieren der MOF-Datei des Knotens wird der Wert der `$version`-Variablen aus einer Textdatei auf dem Clientcomputer gelesen.</span><span class="sxs-lookup"><span data-stu-id="8e39f-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="8e39f-151">DSC ersetzt die `$using:version`-Variablen in jedem Skriptblock durch den Wert der `$version`-Variablen.</span><span class="sxs-lookup"><span data-stu-id="8e39f-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

