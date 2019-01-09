---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Anwenden, Abrufen und Testen von Konfigurationen auf einen Knoten
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401724"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="4ef25-103">Anwenden, Abrufen und Testen von Konfigurationen auf einen Knoten</span><span class="sxs-lookup"><span data-stu-id="4ef25-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="4ef25-104">Diesem Leitfaden erfahren Sie, das Arbeiten mit Konfigurationen auf einem Ziel-Knoten.</span><span class="sxs-lookup"><span data-stu-id="4ef25-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="4ef25-105">Dieses Handbuch ist in die folgenden Schritte unterteilt:</span><span class="sxs-lookup"><span data-stu-id="4ef25-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="4ef25-106">Eine Konfiguration anwenden</span><span class="sxs-lookup"><span data-stu-id="4ef25-106">Apply a Configuration</span></span>

<span data-ttu-id="4ef25-107">Um anwenden und eine Konfiguration zu verwalten, müssen wir eine "MOF"-Datei zu generieren.</span><span class="sxs-lookup"><span data-stu-id="4ef25-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="4ef25-108">Der folgende Code stellt eine einfache Konfiguration dar, die in dieser Anleitung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4ef25-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

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

<span data-ttu-id="4ef25-109">Kompilieren diese Konfiguration führt zu zwei "MOF"-Dateien sich.</span><span class="sxs-lookup"><span data-stu-id="4ef25-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="4ef25-110">Verwenden Sie zum Anwenden einer Konfigurations der [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4ef25-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="4ef25-111">Die `-Path` Parameter gibt ein Verzeichnis, in dem "MOF"-Dateien gespeichert.</span><span class="sxs-lookup"><span data-stu-id="4ef25-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="4ef25-112">Wenn kein `-Computername` angegeben wird, `Start-DSCConfiguration` wird versucht, jede Konfiguration auf den Computernamen, angegeben durch den Namen der Datei "MOF" gelten (\<Computername\>.mof).</span><span class="sxs-lookup"><span data-stu-id="4ef25-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="4ef25-113">Geben Sie `-Verbose` zu `Start-DSCConfiguration` ausführlicheren Ausgabe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ef25-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="4ef25-114">Wenn `-Wait` nicht angegeben ist, werden Sie sehen, dass ein Auftrag erstellt.</span><span class="sxs-lookup"><span data-stu-id="4ef25-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="4ef25-115">Der Auftrag erstellt haben, besitzt eine **ChildJob** für jede "MOF"-Datei verarbeitet, indem `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="4ef25-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="4ef25-116">Wenn eine Konfiguration ist sehr lange dauert und Sie sie beenden möchten, können Sie [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) Anwendung auf dem lokalen Knoten zu beenden.</span><span class="sxs-lookup"><span data-stu-id="4ef25-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="4ef25-117">Nach Abschluss des Vorgangs sehen Sie den Status der Aufträge über das von zurückgegebene Auftragsobjekt [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="4ef25-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

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

<span data-ttu-id="4ef25-118">Finden Sie unter der **ausführlich** Ausgaben, verwenden Sie die folgenden Befehle zum Anzeigen der **ausführlich** Stream für jeden **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="4ef25-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="4ef25-119">Weitere Informationen zu PowerShell-Aufträgen finden Sie unter [About_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="4ef25-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

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

<span data-ttu-id="4ef25-120">In PowerShell 5.0 ab der `-UseExisting` Parameter wurde hinzugefügt, um `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="4ef25-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="4ef25-121">Durch Angabe `-UseExisting`, weisen Sie das Cmdlet, um die vorhandenen angewendete Konfiguration anstelle von angegebene verwenden die `-Path` Parameter.</span><span class="sxs-lookup"><span data-stu-id="4ef25-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="4ef25-122">Eine Testkonfiguration</span><span class="sxs-lookup"><span data-stu-id="4ef25-122">Test a Configuration</span></span>

<span data-ttu-id="4ef25-123">Sie können testen, eine aktuell angewendete Konfiguration mit [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="4ef25-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="4ef25-124">`Test-DSCConfiguration` Gibt `True` Wenn der Knoten konform ist und `False` ist dies nicht.</span><span class="sxs-lookup"><span data-stu-id="4ef25-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="4ef25-125">In PowerShell 5.0 ab der `-Detailed` -Parameter wurde hinzugefügt, womit ein Objekt mit Sammlungen für **ResourcesInDesiredState** und **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="4ef25-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="4ef25-126">Ab in PowerShell 5.0 kann eine Konfiguration testen, ohne es anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="4ef25-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="4ef25-127">Die `-ReferenceConfiguration` Parameter akzeptiert den Pfad einer Datei "MOF" So testen Sie den Knoten für.</span><span class="sxs-lookup"><span data-stu-id="4ef25-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="4ef25-128">Keine **festgelegt** Aktionen für den Knoten ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="4ef25-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="4ef25-129">Klicken Sie in PowerShell 4.0 existieren aber problemumgehungen, um eine Konfiguration zu testen, ohne es anzuwenden, aber sie werden hier nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="4ef25-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="4ef25-130">Abrufen von Konfigurationswerten</span><span class="sxs-lookup"><span data-stu-id="4ef25-130">Get Configuration Values</span></span>

<span data-ttu-id="4ef25-131">Die ["Get-dscconfiguration"](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) Cmdlet gibt die aktuellen Werte für alle konfigurierten Ressourcen in der gerade angewendeten Konfiguration zurück.</span><span class="sxs-lookup"><span data-stu-id="4ef25-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="4ef25-132">Aus diesem Beispiel Konfiguration würde wie folgt aussehen, wenn erfolgreich angewendet.</span><span class="sxs-lookup"><span data-stu-id="4ef25-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

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

## <a name="get-configuration-status"></a><span data-ttu-id="4ef25-133">Abrufen des Status der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="4ef25-133">Get Configuration Status</span></span>

<span data-ttu-id="4ef25-134">In PowerShell 5.0 ab der [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) Cmdlet können Sie den Verlauf der angewendeten Konfigurationen auf den Knoten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4ef25-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="4ef25-135">PowerShell DSC verfolgt des zuletzt {{N}} vorgenommenen Konfigurationsänderungen angewendet **Push** oder **Pull** Modus.</span><span class="sxs-lookup"><span data-stu-id="4ef25-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="4ef25-136">Dazu gehören alle *Konsistenz* Überprüfungen, die vom LCM ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4ef25-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="4ef25-137">In der Standardeinstellung `Get-DSCConfigurationStatus` erfahren Sie, nur dem letzten Verlaufseintrag.</span><span class="sxs-lookup"><span data-stu-id="4ef25-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="4ef25-138">Verwenden der `-All` Parameter, um alle Konfigurationsstatus Verlauf anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4ef25-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="4ef25-139">Aus Gründen der Übersichtlichkeit wird die Ausgabe abgeschnitten.</span><span class="sxs-lookup"><span data-stu-id="4ef25-139">Output is truncated for brevity.</span></span>

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

## <a name="manage-configuration-documents"></a><span data-ttu-id="4ef25-140">Verwalten von Dokumenten</span><span class="sxs-lookup"><span data-stu-id="4ef25-140">Manage Configuration Documents</span></span>

<span data-ttu-id="4ef25-141">Der LCM verwaltet die Konfiguration des Knotens durch die Arbeit mit **Konfigurationsdokumente**.</span><span class="sxs-lookup"><span data-stu-id="4ef25-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="4ef25-142">Diese "MOF"-Dateien befinden sich im Verzeichnis "C:\Windows\System32\Configuration".</span><span class="sxs-lookup"><span data-stu-id="4ef25-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="4ef25-143">In PowerShell 5.0 ab der [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) ermöglicht es Ihnen, entfernen Sie die Dateien "MOF", um zukünftige konsistenzprüfungen beenden oder entfernen Sie eine Konfiguration, die Fehler, wenn angewendet wurde.</span><span class="sxs-lookup"><span data-stu-id="4ef25-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="4ef25-144">Die `-Stage` Parameter können Sie die Datei "MOF" Geben Sie Sie entfernen möchten.</span><span class="sxs-lookup"><span data-stu-id="4ef25-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="4ef25-145">In PowerShell 4.0 können Sie weiterhin diese "MOF"-Dateien, die direkt mit entfernen [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="4ef25-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="4ef25-146">Veröffentlichen von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4ef25-146">Publish Configurations</span></span>

<span data-ttu-id="4ef25-147">In PowerShell 5.0 ab der [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) Cmdlet wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4ef25-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="4ef25-148">Mit diesem Cmdlet können Sie eine "MOF"-Datei mit Remotecomputern zu veröffentlichen, ohne es anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="4ef25-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="4ef25-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4ef25-149">See also</span></span>

- [<span data-ttu-id="4ef25-150">Get, Test und Set</span><span class="sxs-lookup"><span data-stu-id="4ef25-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
