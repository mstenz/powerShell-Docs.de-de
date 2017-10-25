---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „Script“"
ms.openlocfilehash: 81718de0b0c8463189e33e565dc9ff39692dbe8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-script-resource"></a>DSC-Ressource „Script“

 
> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **Script** in Windows PowerShell DSC bietet einen Mechanismus zum Anwenden von Windows PowerShell-Skriptblöcken auf Zielknoten. Die Ressource `Script` hat die Eigenschaften `GetScript`, `SetScript` und `TestScript`. Diese Eigenschaften sollten in Skriptblöcken festgelegt werden, die auf jedem Zielknoten ausgeführt werden. 

Der Skriptblock `GetScript` sollte eine Hashtabelle zurückgeben, die den Zustand des aktuellen Knotens darstellt. Die Hashtabelle darf nur den Schlüssel `Result` enthalten, dessen Wert den Typ `String` haben muss. Es ist keine Rückgabe erforderlich. DSC macht nichts mit der Ausgabe dieses Skriptblocks.

Der Skriptblock `TestScript` sollte ermitteln, ob der aktuelle Knoten geändert werden muss. Er sollte `$true` zurückgeben, wenn der Knoten auf dem neuesten Stand ist. Er sollte `$false` zurückgeben, wenn die Konfiguration des Knotens veraltet ist und von dem Skriptblock `SetScript` aktualisiert werden sollte. Der Skriptblock `TestScript` wird von DSC aufgerufen.

Der Skriptblock `SetScript` sollte den Knoten ändern. Er wird von DSC aufgerufen, wenn der Block `TestScript` `$false` zurückgibt.

Wenn Sie Variablen aus Ihrem Konfigurationsskript in den Skriptblöcken `GetScript`, `TestScript` oder `SetScript` verwenden müssen, verwenden Sie den Bereich `$using:` (ein Beispiel finden Sie weiter unten).


## <a name="syntax"></a>Syntax

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

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| GetScript| Bietet einen Windows PowerShell-Skriptblock, der beim Aufrufen des Cmdlets [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) ausgeführt wird. Dieser Block muss eine Hashtabelle zurückgeben. Die Hashtabelle darf nur den Schlüssel **Result** enthalten, dessen Wert den Typ **String** haben muss.| 
| SetScript| Stellt einen Windows PowerShell-Skriptblock bereit. Beim Aufruf des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) wird der **TestScript**-Block zuerst ausgeführt. Wenn der **TestScript**-Block **$false** zurückgibt, wird der **SetScript**-Block ausgeführt. Wenn der **TestScript**-Block **$true** zurückgibt, wird der **SetScript**-Block nicht ausgeführt.| 
| TestScript| Stellt einen Windows PowerShell-Skriptblock bereit. Beim Aufruf des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) wird dieser Block ausgeführt. Wenn **$false** zurückgegeben wird, wird der „SetScript“-Block ausgeführt. Wenn **$true** zurückgegeben wird, wird der „SetScript“-Block nicht ausgeführt. Der **TestScript**-Block wird auch ausgeführt, wenn Sie das Cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) aufrufen. In diesem Fall wird der **SetScript**-Block jedoch nicht ausgeführt, ganz gleich, welcher Exitcode vom „TestScript“-Block zurückgegeben wird. Der **TestScript**-Block muss „True“ zurückgeben, wenn die tatsächliche Konfiguration der Konfiguration des gewünschten Zustands entspricht. Falls nicht, muss „False“ zurückgegeben werden. (Die aktuelle Konfiguration des gewünschten Zustands ist die letzte Konfiguration, die auf den Knoten angewendet wurde, der DSC verwendet.)| 
| Credential| Gibt die Anmeldeinformationen zum Ausführen dieses Skripts an, falls Anmeldeinformationen erforderlich sind.| 
| DependsOn| Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.

## <a name="example-1"></a>Beispiel 1
```powershell
$version = Get-Content 'version.txt'

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

## <a name="example-2"></a>Beispiel 2
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Version' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Version'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
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

Diese Ressource schreibt die Version der Konfiguration in eine Textdatei. Diese Version ist auf dem Clientcomputer verfügbar, aber auf keinem der Knoten, weshalb sie an jeden der Skriptblöcke der `Script`-Ressource mit dem Bereich `using` der PowerShell übergeben werden muss. Beim Generieren der MOF-Datei des Knotens wird der Wert der `$version`-Variablen aus einer Textdatei auf dem Clientcomputer gelesen. DSC ersetzt die `$using:version`-Variablen in jedem Skriptblock durch den Wert der `$version`-Variablen.

