# Übermitteln des Konfigurationsdokuments, ohne es anzuwenden

Das Cmdlet **Publish-DscConfiguration** kopiert eine MOF-Konfigurationsdatei auf einen Zielknoten, ohne die Konfiguration anzuwenden. Diese Konfiguration wird während des nächsten Konsistenzdurchlaufs oder bei Ausführen des Cmdlets `Update-DscConfiguration` angewendet.

```powershell
Publish-DscConfiguration [-Path] <string> [[-ComputerName] <string[]>] [-Force] [-Credential <pscredential>] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]

Publish-DscConfiguration [-Path] <string> -CimSession <CimSession[]> [-Force] [-ThrottleLimit <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<!--HONumber=Mar16_HO2-->
