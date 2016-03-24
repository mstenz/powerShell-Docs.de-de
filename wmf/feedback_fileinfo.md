# Aktualisierungen beim „FileInfo“-Objekt
Dateiversionsinformationen können irreführend sein, insbesondere in Fällen, bei denen die Datei geändert wurde. Diese WMF Production Preview-Version fügt „FileInfo“-Objekten die neuen Skripteigenschaften **FileVersionRaw** und **ProductVersionRaw** hinzu. Es folgen die für „powershell.exe“ angezeigten Eigenschaften:

PS C:\\&gt; Get-Process -Id $pid -FileVersionInfo | fl \*version\* -Force

FileVersionRaw : 10.0.10055.0

ProductVersionRaw : 10.0.10055.0

FileVersion : 10.0.10055.0 (fbl\_srv2.150402-1826)

ProductVersion : 10.0.10055.0
<!--HONumber=Mar16_HO2-->
