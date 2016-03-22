# DSC-Ressource „Log“ 

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource __Log__ in Windows PowerShell DSC bietet einen Mechanismus zum Schreiben von Meldungen in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

## Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Message| Gibt die Meldung an, die Sie in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ schreiben möchten.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Protokollmeldung geschrieben wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 

## Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie eine Meldung in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ einschließen.

> **Hinweis**: Wenn Sie [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) mit dieser konfigurierten Ressource ausführen, wird stets **$false** zurückgegeben.

```powershell 
Log LogExample
{
    Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
} 
```

<!--HONumber=Feb16_HO4-->
