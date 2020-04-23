---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „Script“
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953067"
---
# <a name="dsc-script-resource"></a>DSC-Ressource „Script“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x

Die Ressource **Script** in Windows PowerShell DSC bietet einen Mechanismus zum Anwenden von Windows PowerShell-Skriptblöcken auf Zielknoten. Die Ressource **Script** verwendet die Eigenschaften **GetScript**, **SetScript** und **TestScript**, die von Ihnen definierte Skriptblöcke enthalten, um die entsprechenden DSC-Zustandsvorgänge auszuführen.

## <a name="syntax"></a>Syntax

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
> Die Blöcke **GetScript**, **TestScript** und **SetScript** werden als Zeichenfolgen gespeichert.

## <a name="properties"></a>Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|GetScript |Ein Skriptblock, der den aktuellen Zustand des Knotens zurückgibt. |
|SetScript |Ein Skriptblock, mit dem DSC die Konformität erzwingt, wenn der Knoten nicht im gewünschten Zustand ist. |
|TestScript |Ein Skriptblock, der bestimmt, ob der Knoten im gewünschten Zustand ist. |
|Anmeldeinformationen |Gibt die Anmeldeinformationen zum Ausführen dieses Skripts an, falls Anmeldeinformationen erforderlich sind. |

## <a name="common-properties"></a>Allgemeine Eigenschaften

|Eigenschaft |BESCHREIBUNG |
|---|---|
|DependsOn |Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest. |

> [!NOTE]
> Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen. Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).

### <a name="additional-information"></a>Zusätzliche Informationen

#### <a name="getscript"></a>GetScript

DSC verwendet die Ausgabe von **GetScript** nicht. Das Cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) führt **GetScript** aus, um den aktuellen Zustand eines Knotens abzurufen. Ein Rückgabewert von **GetScript** ist nicht erforderlich. Wenn Sie einen Rückgabewert angeben, muss es eine Hashtabelle mit einem **Result**-Schlüssel sein, dessen Wert eine Zeichenfolge ist.

#### <a name="testscript"></a>TestScript

**TestScript** wird von DSC ausgeführt, um zu bestimmen, ob **SetScript** ausgeführt werden soll. Wenn **TestScript** den Wert `$false` zurückgibt, führt DSC **SetScript** aus, um den Knoten wieder in den gewünschten Zustand zu versetzen. Es muss ein boolescher Wert zurückgegeben werden. Das Ergebnis `$true` gibt an, dass der Knoten konform ist und **SetScript** nicht ausgeführt werden soll.

Das Cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) führt **TestScript** aus, um die Konformität der Knoten mit den **Script**-Ressourcen abzurufen.
In diesem Fall wird **SetScript** jedoch nicht ausgeführt, unabhängig davon, was vom **TestScript**-Block zurückgegeben wird.

> [!NOTE]
> Die gesamte Ausgabe von **TestScript** ist Teil des Rückgabewerts. PowerShell interpretiert nicht unterdrückte Ausgaben als ungleich null. Dies bedeutet, dass **TestScript** den Wert `$true` unabhängig vom Zustand des Knotens zurückgibt. Dies führt zu unvorhersehbaren Ergebnissen und zu falsch positiven Ergebnissen und erschwert so die Problembehandlung.

#### <a name="setscript"></a>SetScript

**SetScript** ändert den Knoten, um den gewünschten Zustand zu erzwingen. Der Skriptblock wird von DSC aufgerufen, wenn der Skriptblock **TestScript** den Wert `$false` zurückgibt. **SetScript** sollte keinen Rückgabewert haben.

## <a name="examples"></a>Beispiele

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Beispiel 1: Schreiben von Beispieltext mit einer Script-Ressource

Dieses Beispiel testet das Vorhandensein von `C:\TempFolder\TestFile.txt` auf jedem Knoten. Wenn die Datei nicht vorhanden ist, wird sie mit `SetScript` erstellt. `GetScript` gibt den Inhalt der Datei zurück, und der Rückgabewert wird nicht verwendet.

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Beispiel 2: Vergleichen von Versionsinformationen mit einer Script-Ressource

Dieses Beispiel ruft die Informationen zur *konformen* Version aus einer Textdatei auf dem zur Erstellung verwendeten Computer ab und speichert sie in der `$version`-Variablen. Beim Generieren der MOF-Datei des Knotens ersetzt DSC die `$using:version`-Variablen in jedem Skriptblock durch den Wert der `$version`-Variablen.
Während der Ausführung wird die *konforme* Version in einer Textdatei auf jedem Knoten gespeichert und bei nachfolgenden Ausführungen verglichen und aktualisiert.

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