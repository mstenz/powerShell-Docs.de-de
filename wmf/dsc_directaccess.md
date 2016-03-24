# Direkter Zugriff auf DSC-Ressourcenmethoden


Das Cmdlet `Invoke-DscResource` wurde hinzugefügt und bietet direkten Zugriff auf DSC-Ressourcen und ihre Methoden (Get, Set, Test). Es kann von Drittanbietern verwendet werden, die DSC-Ressourcen nutzen möchten. Dieses Cmdlet wird in der Regel in Kombination mit `refreshMode = ‘Disabled’` verwendet, kann aber unabhängig davon verwendet werden, auf was die „RefreshMode“-Eigenschaft festgelegt ist. Nachstehend finden Sie einige Beispiele für die Verwendung des neuen Cmdlets:

## Sicherstellen, dass eine Datei vorhanden ist

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Testen, ob eine Datei vorhanden ist

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Abrufen des Inhalts einer Datei

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```
<!--HONumber=Mar16_HO2-->
