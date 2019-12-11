---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Script“
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953067"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="129e1-103">DSC-Ressource „Script“</span><span class="sxs-lookup"><span data-stu-id="129e1-103">DSC Script Resource</span></span>

> <span data-ttu-id="129e1-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="129e1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="129e1-105">Die Ressource **Script** in Windows PowerShell DSC bietet einen Mechanismus zum Anwenden von Windows PowerShell-Skriptblöcken auf Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="129e1-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="129e1-106">Die Ressource **Script** verwendet die Eigenschaften **GetScript**, **SetScript** und **TestScript**, die von Ihnen definierte Skriptblöcke enthalten, um die entsprechenden DSC-Zustandsvorgänge auszuführen.</span><span class="sxs-lookup"><span data-stu-id="129e1-106">The **Script** resource uses **GetScript**, **SetScript**, and **TestScript** properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="129e1-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="129e1-107">Syntax</span></span>

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="129e1-108">Die Blöcke **GetScript**, **TestScript** und **SetScript** werden als Zeichenfolgen gespeichert.</span><span class="sxs-lookup"><span data-stu-id="129e1-108">**GetScript**, **TestScript**, and **SetScript** blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="129e1-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="129e1-109">Properties</span></span>

|<span data-ttu-id="129e1-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="129e1-110">Property</span></span> |<span data-ttu-id="129e1-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="129e1-111">Description</span></span> |
|---|---|
|<span data-ttu-id="129e1-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="129e1-112">GetScript</span></span> |<span data-ttu-id="129e1-113">Ein Skriptblock, der den aktuellen Zustand des Knotens zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="129e1-113">A script block that returns the current state of the Node.</span></span> |
|<span data-ttu-id="129e1-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="129e1-114">SetScript</span></span> |<span data-ttu-id="129e1-115">Ein Skriptblock, mit dem DSC die Konformität erzwingt, wenn der Knoten nicht im gewünschten Zustand ist.</span><span class="sxs-lookup"><span data-stu-id="129e1-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
|<span data-ttu-id="129e1-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="129e1-116">TestScript</span></span> |<span data-ttu-id="129e1-117">Ein Skriptblock, der bestimmt, ob der Knoten im gewünschten Zustand ist.</span><span class="sxs-lookup"><span data-stu-id="129e1-117">A script block that determines if the Node is in the desired state.</span></span> |
|<span data-ttu-id="129e1-118">Credential</span><span class="sxs-lookup"><span data-stu-id="129e1-118">Credential</span></span> |<span data-ttu-id="129e1-119">Gibt die Anmeldeinformationen zum Ausführen dieses Skripts an, falls Anmeldeinformationen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="129e1-119">Indicates the credentials to use for running this script, if credentials are required.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="129e1-120">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="129e1-120">Common properties</span></span>

|<span data-ttu-id="129e1-121">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="129e1-121">Property</span></span> |<span data-ttu-id="129e1-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="129e1-122">Description</span></span> |
|---|---|
|<span data-ttu-id="129e1-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="129e1-123">DependsOn</span></span> |<span data-ttu-id="129e1-124">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="129e1-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="129e1-125">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="129e1-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="129e1-126">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="129e1-126">PsDscRunAsCredential</span></span> |<span data-ttu-id="129e1-127">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="129e1-127">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="129e1-128">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="129e1-128">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="129e1-129">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="129e1-129">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="129e1-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="129e1-130">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="129e1-131">GetScript</span><span class="sxs-lookup"><span data-stu-id="129e1-131">GetScript</span></span>

<span data-ttu-id="129e1-132">DSC verwendet die Ausgabe von **GetScript** nicht.</span><span class="sxs-lookup"><span data-stu-id="129e1-132">DSC does not use the output from **GetScript**.</span></span> <span data-ttu-id="129e1-133">Das Cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) führt **GetScript** aus, um den aktuellen Zustand eines Knotens abzurufen.</span><span class="sxs-lookup"><span data-stu-id="129e1-133">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes **GetScript** to retrieve a node's current state.</span></span> <span data-ttu-id="129e1-134">Ein Rückgabewert von **GetScript** ist nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="129e1-134">A return value is not required from **GetScript**.</span></span> <span data-ttu-id="129e1-135">Wenn Sie einen Rückgabewert angeben, muss es eine Hashtabelle mit einem **Result**-Schlüssel sein, dessen Wert eine Zeichenfolge ist.</span><span class="sxs-lookup"><span data-stu-id="129e1-135">If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="129e1-136">TestScript</span><span class="sxs-lookup"><span data-stu-id="129e1-136">TestScript</span></span>

<span data-ttu-id="129e1-137">**TestScript** wird von DSC ausgeführt, um zu bestimmen, ob **SetScript** ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="129e1-137">**TestScript** is executed by DSC to determine if **SetScript** should be run.</span></span> <span data-ttu-id="129e1-138">Wenn **TestScript** den Wert `$false` zurückgibt, führt DSC **SetScript** aus, um den Knoten wieder in den gewünschten Zustand zu versetzen.</span><span class="sxs-lookup"><span data-stu-id="129e1-138">If **TestScript** returns `$false`, DSC executes **SetScript** to bring the node back to the desired state.</span></span> <span data-ttu-id="129e1-139">Es muss ein boolescher Wert zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="129e1-139">It must return a boolean value.</span></span> <span data-ttu-id="129e1-140">Das Ergebnis `$true` gibt an, dass der Knoten konform ist und **SetScript** nicht ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="129e1-140">A result of `$true` indicates that the node is compliant and **SetScript** should not executed.</span></span>

<span data-ttu-id="129e1-141">Das Cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) führt **TestScript** aus, um die Konformität der Knoten mit den **Script**-Ressourcen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="129e1-141">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes **TestScript** to retrieve the nodes compliance with the **Script** resources.</span></span>
<span data-ttu-id="129e1-142">In diesem Fall wird **SetScript** jedoch nicht ausgeführt, unabhängig davon, was vom **TestScript**-Block zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="129e1-142">However, in this case, **SetScript** does not run, no matter what **TestScript** block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="129e1-143">Die gesamte Ausgabe von **TestScript** ist Teil des Rückgabewerts.</span><span class="sxs-lookup"><span data-stu-id="129e1-143">All output from your **TestScript** is part of its return value.</span></span> <span data-ttu-id="129e1-144">PowerShell interpretiert nicht unterdrückte Ausgaben als ungleich null. Dies bedeutet, dass **TestScript** den Wert `$true` unabhängig vom Zustand des Knotens zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="129e1-144">PowerShell interprets unsuppressed output as non-zero, which means that your **TestScript** will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="129e1-145">Dies führt zu unvorhersehbaren Ergebnissen und zu falsch positiven Ergebnissen und erschwert so die Problembehandlung.</span><span class="sxs-lookup"><span data-stu-id="129e1-145">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="129e1-146">SetScript</span><span class="sxs-lookup"><span data-stu-id="129e1-146">SetScript</span></span>

<span data-ttu-id="129e1-147">**SetScript** ändert den Knoten, um den gewünschten Zustand zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="129e1-147">**SetScript** modifies the node to enforce the desired state.</span></span> <span data-ttu-id="129e1-148">Der Skriptblock wird von DSC aufgerufen, wenn der Skriptblock **TestScript** den Wert `$false` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="129e1-148">It is called by DSC if the **TestScript** script block returns `$false`.</span></span> <span data-ttu-id="129e1-149">**SetScript** sollte keinen Rückgabewert haben.</span><span class="sxs-lookup"><span data-stu-id="129e1-149">The **SetScript** should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="129e1-150">Beispiele</span><span class="sxs-lookup"><span data-stu-id="129e1-150">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="129e1-151">Beispiel 1: Schreiben von Beispieltext mit einer Skriptressource</span><span class="sxs-lookup"><span data-stu-id="129e1-151">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="129e1-152">Dieses Beispiel testet das Vorhandensein von `C:\TempFolder\TestFile.txt` auf jedem Knoten.</span><span class="sxs-lookup"><span data-stu-id="129e1-152">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="129e1-153">Wenn die Datei nicht vorhanden ist, wird sie mit `SetScript` erstellt.</span><span class="sxs-lookup"><span data-stu-id="129e1-153">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="129e1-154">`GetScript` gibt den Inhalt der Datei zurück, und der Rückgabewert wird nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="129e1-154">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="129e1-155">Beispiel 2: Vergleichen von Versionsinformationen mit einer Skriptressource</span><span class="sxs-lookup"><span data-stu-id="129e1-155">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="129e1-156">Dieses Beispiel ruft die Informationen zur *konformen* Version aus einer Textdatei auf dem zur Erstellung verwendeten Computer ab und speichert sie in der `$version`-Variablen.</span><span class="sxs-lookup"><span data-stu-id="129e1-156">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="129e1-157">Beim Generieren der MOF-Datei des Knotens ersetzt DSC die `$using:version`-Variablen in jedem Skriptblock durch den Wert der `$version`-Variablen.</span><span class="sxs-lookup"><span data-stu-id="129e1-157">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="129e1-158">Während der Ausführung wird die *konforme* Version in einer Textdatei auf jedem Knoten gespeichert und bei nachfolgenden Ausführungen verglichen und aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="129e1-158">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

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
}
```