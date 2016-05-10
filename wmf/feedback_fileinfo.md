# Aktualisierungen beim „FileInfo“-Objekt
Dateiversionsinformationen können irreführend sein, insbesondere in Fällen, bei denen die Datei geändert wurde. Diese Version von WMF 5.0 fügt die neuen Skripteigenschaften **FileVersionRaw** und **ProductVersionRaw** 
zu „FileInfo“-Objekten hinzu. Es folgen die für „powershell.exe“ angezeigten Eigenschaften (vorausgesetzt wird, dass „$pid“ die ID des PowerShell-Prozesses ist):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117


<!--HONumber=Apr16_HO3-->


