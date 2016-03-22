# DSC-Ressource „Script“

 
> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **Script** in Windows PowerShell DSC bietet einen Mechanismus zum Anwenden von Windows PowerShell-Skriptblöcken auf Zielknoten.

## Syntax

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

## Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| GetScript| Bietet einen Windows PowerShell-Skriptblock, der beim Aufrufen des Cmdlets [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) ausgeführt wird. Dieser Block muss eine Hashtabelle zurückgeben.| 
| SetScript| Stellt einen Windows PowerShell-Skriptblock bereit. Beim Aufruf des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) wird der **TestScript**-Block zuerst ausgeführt. Wenn der **TestScript**-Block **$false** zurückgibt, wird der **SetScript**-Block ausgeführt. Wenn der **TestScript**-Block **$true** zurückgibt, wird der **SetScript**-Block nicht ausgeführt.| 
| TestScript| Stellt einen Windows PowerShell-Skriptblock bereit. Beim Aufruf des Cmdlets [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) wird dieser Block ausgeführt. Wenn **$false** zurückgegeben wird, wird der „SetScript“-Block ausgeführt. Wenn **$true** zurückgegeben wird, wird der „SetScript“-Block nicht ausgeführt. Der **TestScript**-Block wird auch ausgeführt, wenn Sie das Cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) aufrufen. In diesem Fall wird der **SetScript**-Block jedoch nicht ausgeführt, ganz gleich, welcher Exitcode vom „TestScript“-Block zurückgegeben wird. Der **TestScript**-Block muss „True“ zurückgeben, wenn die tatsächliche Konfiguration der Konfiguration des gewünschten Zustands entspricht. Falls nicht, muss „False“ zurückgegeben werden. (Die aktuelle Konfiguration des gewünschten Zustands ist die letzte Konfiguration, die auf den Knoten angewendet wurde, der DSC verwendet.)| 
| Credential| Gibt die Anmeldeinformationen zum Ausführen dieses Skripts an, falls Anmeldeinformationen erforderlich sind.| 
| DependsOn| Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.

## Beispiel
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { <# This must return a hash table #> }          
}
```

<!--HONumber=Feb16_HO4-->
