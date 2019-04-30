---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Anwenden, Abrufen und Testen von Konfigurationen auf einen Knoten
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079709"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="c1cc4-103">Anwenden, Abrufen und Testen von Konfigurationen auf einen Knoten</span><span class="sxs-lookup"><span data-stu-id="c1cc4-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="c1cc4-104">In diesem Leitfaden erfahren Sie, wie Sie mit Konfigurationen für einen Zielknoten arbeiten.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="c1cc4-105">Diese Anleitung ist in die folgenden Schritte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="c1cc4-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="c1cc4-106">Anwenden einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c1cc4-106">Apply a Configuration</span></span>

<span data-ttu-id="c1cc4-107">Um eine Konfiguration anwenden und verwalten zu können, müssen Sie eine MOF-Datei generieren.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="c1cc4-108">Der folgende Code stellt eine einfache Konfiguration dar, die in dieser Anleitung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="c1cc4-109">Bei der Kompilierung dieser Konfiguration werden zwei MOF-Dateien generiert.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="c1cc4-110">Um eine Konfiguration anzuwenden, verwenden Sie das Cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="c1cc4-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="c1cc4-111">Der `-Path`-Parameter gibt ein Verzeichnis an, in dem MOF-Dateien gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="c1cc4-112">Wenn kein `-Computername` angegeben wird, versucht `Start-DSCConfiguration`, jede Konfiguration auf den Computernamen anzuwenden, der durch den Namen der MOF-Datei (\<computername\>.mof) angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="c1cc4-113">Geben Sie `-Verbose` für `Start-DSCConfiguration` an, um eine ausführlichere Ausgabe zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="c1cc4-114">Wenn `-Wait` nicht angegeben wird, erkennen Sie, dass ein Auftrag erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="c1cc4-115">Der erstellte Auftrag enthält einen **ChildJob** für jede MOF-Datei, die von `Start-DSCConfiguration` verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="c1cc4-116">Wenn eine Konfiguration lange dauert und Sie sie beenden möchten, können Sie mit [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) die Anwendung auf dem lokalen Knoten beenden.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="c1cc4-117">Nach der Fertigstellung können Sie den Status der Aufträge über das von [Get-Job](/powershell/module/microsoft.powershell.core/get-job) zurückgegebene Auftragsobjekt anzeigen.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="c1cc4-118">Um die **Verbose**-Ausgabe anzuzeigen, verwenden Sie die folgenden Befehle, um den **Verbose**-Datenstrom für jeden **ChildJob** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="c1cc4-119">Weitere Informationen zu PowerShell-Aufträgen finden Sie unter [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="c1cc4-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="c1cc4-120">Ab PowerShell 5.0 wurde der `-UseExisting`-Parameter `Start-DSCConfiguration` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="c1cc4-121">Durch die Angabe von `-UseExisting` weisen Sie das Cmdlet an, die vorhandene angewandte Konfiguration anstelle der durch den Parameter `-Path` angegebenen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="c1cc4-122">Testen einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c1cc4-122">Test a Configuration</span></span>

<span data-ttu-id="c1cc4-123">Sie können eine aktuell angewendete Konfiguration mit [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) testen.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="c1cc4-124">`Test-DSCConfiguration` gibt `True` zurück, wenn der Knoten konform ist und `False`, wenn dies nicht der Fall ist.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="c1cc4-125">Ab PowerShell 5.0 wurde der Parameter `-Detailed` hinzugefügt, der ein Objekt mit Sammlungen für **ResourcesInDesiredState** und **ResourcesNotInDesiredState** zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="c1cc4-126">Ab in PowerShell 5.0 können Sie eine Konfiguration testen, ohne sie anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="c1cc4-127">Der `-ReferenceConfiguration`-Parameter akzeptiert den Pfad einer MOF-Datei, anhand derer der Knoten getestet wird.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="c1cc4-128">Es werden keine **Set**-Aktionen für den Knoten ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="c1cc4-129">In PowerShell 4.0 gibt es Problemumgehungen, um eine Konfiguration zu testen, ohne sie anzuwenden, aber diese werden hier nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="c1cc4-130">Abrufen von Konfigurationswerten</span><span class="sxs-lookup"><span data-stu-id="c1cc4-130">Get Configuration Values</span></span>

<span data-ttu-id="c1cc4-131">Das Cmdlet [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) gibt die aktuellen Werte für alle konfigurierten Ressourcen in der aktuell angewendeten Konfiguration zurück.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="c1cc4-132">Die Ausgabe aus unserer Beispielkonfiguration würde bei erfolgreicher Anwendung folgendermaßen aussehen.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="c1cc4-133">Abrufen des Konfigurationsstatus</span><span class="sxs-lookup"><span data-stu-id="c1cc4-133">Get Configuration Status</span></span>

<span data-ttu-id="c1cc4-134">Ab PowerShell 5.0 ermöglicht Ihnen das Cmdlet [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) das Anzeigen des Verlaufs der auf den Knoten angewendeten Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="c1cc4-135">PowerShell DSC verfolgt die letzten {{N}} Konfigurationen nach, die im Modus **Push** oder **Pull** angewendet wurden.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="c1cc4-136">Dazu gehören auch alle *Konsistenzprüfungen*, die von LCM ausgeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="c1cc4-137">Standardmäßig zeigt `Get-DSCConfigurationStatus` nur den letzten Verlaufseintrag an.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="c1cc4-138">Verwenden Sie den Parameter `-All`, um den gesamten Verlauf des Konfigurationsstatus anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="c1cc4-139">Aus Gründen der Übersichtlichkeit wird die Ausgabe abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="c1cc4-140">Verwalten von Konfigurationsdokumenten</span><span class="sxs-lookup"><span data-stu-id="c1cc4-140">Manage Configuration Documents</span></span>

<span data-ttu-id="c1cc4-141">Der LCM verwaltet die Konfiguration des Knotens, indem **Konfigurationsdokumente** verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="c1cc4-142">Diese MOF-Dateien befinden sich im Verzeichnis „C:\Windows\System32\Configuration“.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="c1cc4-143">Ab PowerShell 5.0 ermöglicht Ihnen [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) das Entfernen der MOF-Dateien, um zukünftige Konsistenzprüfungen zu beenden oder eine Konfiguration zu entfernen, bei deren Anwendung Fehler auftreten.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="c1cc4-144">Der Parameter `-Stage` ermöglicht die Angabe, welche MOF-Datei entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="c1cc4-145">In PowerShell 4.0 können Sie diese MOF-Dateien weiterhin direkt mit [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) entfernen.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="c1cc4-146">Veröffentlichen von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="c1cc4-146">Publish Configurations</span></span>

<span data-ttu-id="c1cc4-147">Ab PowerShell 5.0 wurde das Cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="c1cc4-148">Mit diesem Cmdlet können Sie eine MOF-Datei für Remotecomputer veröffentlichen, ohne sie anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="c1cc4-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="c1cc4-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c1cc4-149">See also</span></span>

- [<span data-ttu-id="c1cc4-150">Get, Test und Set</span><span class="sxs-lookup"><span data-stu-id="c1cc4-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
