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
# <a name="apply-get-and-test-configurations-on-a-node"></a>Anwenden, Abrufen und Testen von Konfigurationen auf einen Knoten

Diesem Leitfaden erfahren Sie, das Arbeiten mit Konfigurationen auf einem Ziel-Knoten. Dieses Handbuch ist in die folgenden Schritte unterteilt:

## <a name="apply-a-configuration"></a>Eine Konfiguration anwenden

Um anwenden und eine Konfiguration zu verwalten, müssen wir eine "MOF"-Datei zu generieren. Der folgende Code stellt eine einfache Konfiguration dar, die in dieser Anleitung verwendet werden.

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

Kompilieren diese Konfiguration führt zu zwei "MOF"-Dateien sich.

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Verwenden Sie zum Anwenden einer Konfigurations der [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet. Die `-Path` Parameter gibt ein Verzeichnis, in dem "MOF"-Dateien gespeichert. Wenn kein `-Computername` angegeben wird, `Start-DSCConfiguration` wird versucht, jede Konfiguration auf den Computernamen, angegeben durch den Namen der Datei "MOF" gelten (\<Computername\>.mof). Geben Sie `-Verbose` zu `Start-DSCConfiguration` ausführlicheren Ausgabe angezeigt.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Wenn `-Wait` nicht angegeben ist, werden Sie sehen, dass ein Auftrag erstellt. Der Auftrag erstellt haben, besitzt eine **ChildJob** für jede "MOF"-Datei verarbeitet, indem `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Wenn eine Konfiguration ist sehr lange dauert und Sie sie beenden möchten, können Sie [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) Anwendung auf dem lokalen Knoten zu beenden.

```powershell
Stop-DSCConfiguration -Force
```

Nach Abschluss des Vorgangs sehen Sie den Status der Aufträge über das von zurückgegebene Auftragsobjekt [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

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

Finden Sie unter der **ausführlich** Ausgaben, verwenden Sie die folgenden Befehle zum Anzeigen der **ausführlich** Stream für jeden **ChildJob**. Weitere Informationen zu PowerShell-Aufträgen finden Sie unter [About_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

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

In PowerShell 5.0 ab der `-UseExisting` Parameter wurde hinzugefügt, um `Start-DSCConfiguration`. Durch Angabe `-UseExisting`, weisen Sie das Cmdlet, um die vorhandenen angewendete Konfiguration anstelle von angegebene verwenden die `-Path` Parameter.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Eine Testkonfiguration

Sie können testen, eine aktuell angewendete Konfiguration mit [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` Gibt `True` Wenn der Knoten konform ist und `False` ist dies nicht.

```powershell
Test-DSCConfiguration
```

In PowerShell 5.0 ab der `-Detailed` -Parameter wurde hinzugefügt, womit ein Objekt mit Sammlungen für **ResourcesInDesiredState** und **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

Ab in PowerShell 5.0 kann eine Konfiguration testen, ohne es anzuwenden. Die `-ReferenceConfiguration` Parameter akzeptiert den Pfad einer Datei "MOF" So testen Sie den Knoten für. Keine **festgelegt** Aktionen für den Knoten ausgeführt werden. Klicken Sie in PowerShell 4.0 existieren aber problemumgehungen, um eine Konfiguration zu testen, ohne es anzuwenden, aber sie werden hier nicht behandelt.

## <a name="get-configuration-values"></a>Abrufen von Konfigurationswerten

Die ["Get-dscconfiguration"](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) Cmdlet gibt die aktuellen Werte für alle konfigurierten Ressourcen in der gerade angewendeten Konfiguration zurück.

```powershell
Get-DSCConfiguration
```

Aus diesem Beispiel Konfiguration würde wie folgt aussehen, wenn erfolgreich angewendet.

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

## <a name="get-configuration-status"></a>Abrufen des Status der Konfiguration

In PowerShell 5.0 ab der [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) Cmdlet können Sie den Verlauf der angewendeten Konfigurationen auf den Knoten anzuzeigen. PowerShell DSC verfolgt des zuletzt {{N}} vorgenommenen Konfigurationsänderungen angewendet **Push** oder **Pull** Modus. Dazu gehören alle *Konsistenz* Überprüfungen, die vom LCM ausgeführt. In der Standardeinstellung `Get-DSCConfigurationStatus` erfahren Sie, nur dem letzten Verlaufseintrag.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Verwenden der `-All` Parameter, um alle Konfigurationsstatus Verlauf anzuzeigen.

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

## <a name="manage-configuration-documents"></a>Verwalten von Dokumenten

Der LCM verwaltet die Konfiguration des Knotens durch die Arbeit mit **Konfigurationsdokumente**. Diese "MOF"-Dateien befinden sich im Verzeichnis "C:\Windows\System32\Configuration".

In PowerShell 5.0 ab der [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) ermöglicht es Ihnen, entfernen Sie die Dateien "MOF", um zukünftige konsistenzprüfungen beenden oder entfernen Sie eine Konfiguration, die Fehler, wenn angewendet wurde. Die `-Stage` Parameter können Sie die Datei "MOF" Geben Sie Sie entfernen möchten.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> In PowerShell 4.0 können Sie weiterhin diese "MOF"-Dateien, die direkt mit entfernen [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Veröffentlichen von Konfigurationen

In PowerShell 5.0 ab der [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) Cmdlet wurde hinzugefügt. Mit diesem Cmdlet können Sie eine "MOF"-Datei mit Remotecomputern zu veröffentlichen, ohne es anzuwenden.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Siehe auch

- [Get, Test und Set](../resources/get-test-set.md)
