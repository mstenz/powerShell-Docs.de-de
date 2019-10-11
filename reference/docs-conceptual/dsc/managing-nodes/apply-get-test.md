---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Anwenden, Abrufen und Testen von Konfigurationen auf einen Knoten
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953837"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Anwenden, Abrufen und Testen von Konfigurationen auf einen Knoten

In diesem Leitfaden erfahren Sie, wie Sie mit Konfigurationen für einen Zielknoten arbeiten. Diese Anleitung ist in die folgenden Schritte unterteilt:

## <a name="apply-a-configuration"></a>Anwenden einer Konfiguration

Um eine Konfiguration anwenden und verwalten zu können, müssen Sie eine MOF-Datei generieren. Der folgende Code stellt eine einfache Konfiguration dar, die in dieser Anleitung verwendet wird.

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

Bei der Kompilierung dieser Konfiguration werden zwei MOF-Dateien generiert.

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Um eine Konfiguration anzuwenden, verwenden Sie das Cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration). Der `-Path`-Parameter gibt ein Verzeichnis an, in dem MOF-Dateien gespeichert werden. Wenn kein `-Computername` angegeben wird, versucht `Start-DSCConfiguration`, jede Konfiguration auf den Computernamen anzuwenden, der durch den Namen der MOF-Datei (\<computername\>.mof) angegeben wird. Geben Sie `-Verbose` für `Start-DSCConfiguration` an, um eine ausführlichere Ausgabe zu erhalten.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Wenn `-Wait` nicht angegeben wird, erkennen Sie, dass ein Auftrag erstellt wurde. Der erstellte Auftrag enthält einen **ChildJob** für jede MOF-Datei, die von `Start-DSCConfiguration` verarbeitet wird.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Wenn eine Konfiguration lange dauert und Sie sie beenden möchten, können Sie mit [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) die Anwendung auf dem lokalen Knoten beenden.

```powershell
Stop-DSCConfiguration -Force
```

Nach der Fertigstellung können Sie den Status der Aufträge über das von [Get-Job](/powershell/module/microsoft.powershell.core/get-job) zurückgegebene Auftragsobjekt anzeigen.

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

Um die **Verbose**-Ausgabe anzuzeigen, verwenden Sie die folgenden Befehle, um den **Verbose**-Datenstrom für jeden **ChildJob** anzuzeigen. Weitere Informationen zu PowerShell-Aufträgen finden Sie unter [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

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

Ab PowerShell 5.0 wurde der `-UseExisting`-Parameter `Start-DSCConfiguration` hinzugefügt. Durch die Angabe von `-UseExisting` weisen Sie das Cmdlet an, die vorhandene angewandte Konfiguration anstelle der durch den Parameter `-Path` angegebenen zu verwenden.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Testen einer Konfiguration

Sie können eine aktuell angewendete Konfiguration mit [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) testen. `Test-DSCConfiguration` gibt `True` zurück, wenn der Knoten konform ist und `False`, wenn dies nicht der Fall ist.

```powershell
Test-DSCConfiguration
```

Ab PowerShell 5.0 wurde der Parameter `-Detailed` hinzugefügt, der ein Objekt mit Sammlungen für **ResourcesInDesiredState** und **ResourcesNotInDesiredState** zurückgibt.

```powershell
Test-DSCConfiguration -Detailed
```

Ab in PowerShell 5.0 können Sie eine Konfiguration testen, ohne sie anzuwenden. Der `-ReferenceConfiguration`-Parameter akzeptiert den Pfad einer MOF-Datei, anhand derer der Knoten getestet wird. Es werden keine **Set**-Aktionen für den Knoten ausgeführt. In PowerShell 4.0 gibt es Problemumgehungen, um eine Konfiguration zu testen, ohne sie anzuwenden, aber diese werden hier nicht behandelt.

## <a name="get-configuration-values"></a>Abrufen von Konfigurationswerten

Das Cmdlet [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) gibt die aktuellen Werte für alle konfigurierten Ressourcen in der aktuell angewendeten Konfiguration zurück.

```powershell
Get-DSCConfiguration
```

Die Ausgabe aus unserer Beispielkonfiguration würde bei erfolgreicher Anwendung folgendermaßen aussehen.

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

## <a name="get-configuration-status"></a>Abrufen des Konfigurationsstatus

Ab PowerShell 5.0 ermöglicht Ihnen das Cmdlet [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) das Anzeigen des Verlaufs der auf den Knoten angewendeten Konfigurationen. PowerShell DSC verfolgt die letzten {{N}} Konfigurationen nach, die im Modus **Push** oder **Pull** angewendet wurden. Dazu gehören auch alle *Konsistenzprüfungen*, die von LCM ausgeführt wurden. Standardmäßig zeigt `Get-DSCConfigurationStatus` nur den letzten Verlaufseintrag an.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Verwenden Sie den Parameter `-All`, um den gesamten Verlauf des Konfigurationsstatus anzuzeigen.

> [!NOTE]
> Aus Gründen der Übersichtlichkeit wird die Ausgabe abgeschnitten.

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

## <a name="manage-configuration-documents"></a>Verwalten von Konfigurationsdokumenten

Der LCM verwaltet die Konfiguration des Knotens, indem **Konfigurationsdokumente** verwendet werden. Diese MOF-Dateien befinden sich im Verzeichnis „C:\Windows\System32\Configuration“.

Ab PowerShell 5.0 ermöglicht Ihnen [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) das Entfernen der MOF-Dateien, um zukünftige Konsistenzprüfungen zu beenden oder eine Konfiguration zu entfernen, bei deren Anwendung Fehler auftreten. Der Parameter `-Stage` ermöglicht die Angabe, welche MOF-Datei entfernt werden soll.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> In PowerShell 4.0 können Sie diese MOF-Dateien weiterhin direkt mit [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) entfernen.

## <a name="publish-configurations"></a>Veröffentlichen von Konfigurationen

Ab PowerShell 5.0 wurde das Cmdlet [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) hinzugefügt. Mit diesem Cmdlet können Sie eine MOF-Datei für Remotecomputer veröffentlichen, ohne sie anzuwenden.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Siehe auch

- [Get, Test und Set](../resources/get-test-set.md)
