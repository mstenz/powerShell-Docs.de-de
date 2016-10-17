# Save-Script

Mit dem Cmdlet „Save-Script“ können Sie die Skriptdatei überprüfen, indem Sie sie an einem angegebenen Speicherort speichern.

## Beschreibung

Das Cmdlet „Save-Script“ speichert das angegebene Skript.

## Cmdlet-Syntax

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## Cmdlet-Onlinehilfe

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## Beispiele für Befehle

### Beispiel 1: Speichern eines Skripts aus einem Repository
Dieser Befehl speichert die neueste Version des Skripts „Fabrikam-ClientScript“ aus dem Repository „GalleryINT“ im lokalen Ordner „C:\ScriptSharingDemo“.

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### Beispiel 2: Speichern einer Version eines Skripts durch Weiterreichen vom Cmdlet „Find-Script“

Der erste Befehl sucht nach Version 1.5 von „Fabrikam-ClientScript“ vom Repository „GalleryINT“ und speichert sie im Ordner „C:\ScriptSharingDemo“.

Der zweite Befehl überprüft die Metadaten des gespeicherten Skripts.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```


<!--HONumber=Aug16_HO3-->


