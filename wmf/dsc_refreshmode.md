# Zusätzlicher Wert für „RefreshMode“-Eigenschaft

Diese Version bietet den neuen `RefreshMode`-Wert **Disabled**. Wenn dieser Modus festgelegt ist, übernimmt der LCM keine Dokumentverwaltung. Dieser Modus kann verwendet werden, wenn ein Verwaltungstool eines Drittanbieters anstelle von DSC verwendet wird, während DSC-Ressourcen mit dem Cmdlet `Invoke-DscResource` weiterhin genutzt werden oder Sie aus einem beliebigen Grund die DSC-Verarbeitung anhalten müssen.

```powershell
Configuration LCMSettings
{
    Node localhost
    {
        LocalConfigurationManager
        {
           RefreshMode = 'Disabled'
        }
    }
}

LCMSettings -OutputPath .\LCMSettings
Set-DscLocalConfigurationManager -Path .\LCMSettings -Verbose -ComputerName localhost
```
<!--HONumber=Mar16_HO2-->
