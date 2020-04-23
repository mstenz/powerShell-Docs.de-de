---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Das ISEFileCollection-Objekt
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736214"
---
# <a name="the-isefilecollection-object"></a>Das ISEFileCollection-Objekt

Das **ISEFileCollection**-Objekt ist eine Sammlung von **ISEFile**-Objekten. Ein Beispiel ist die `$psISE.CurrentPowerShellTab.Files`-Auflistung.

## <a name="methods"></a>Methoden

### <a name="add-fullpath-"></a>Add\( \[FullPath\] \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Erstellt eine neue unbenannte Datei, gibt diese zurück und fügt sie der Sammlung hinzu. Die **IsUntitled**-Eigenschaft der neu erstellten Datei lautet `$true`.

**\[FullPath\]** – Optionale Zeichenfolge – der vollständig angegebene Pfad der Datei. Es wird eine Ausnahme generiert, wenn Sie den **FullPath**-Parameter und den relativen Pfad angeben oder einen Dateinamen anstelle des vollständigen Pfads verwenden.

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a>Remove\( File, \[Force\] \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Entfernt eine angegebene Datei aus der aktuellen PowerShell-Registerkarte.

**File** – Zeichenfolge – Die ISEFile-Datei, die Sie aus der Sammlung entfernen möchten Falls die Datei nicht gespeichert wurde, löst diese Methode eine Ausnahme aus. Verwenden Sie den Schalter **Force**, um das Entfernen einer ungespeicherten Datei zu erzwingen.

**\[Force\]** – Optionaler boolescher Wert: Bei Festlegung auf `$true` wird die Berechtigung zum Entfernen von Dateien erteilt, auch wenn diese nach der letzten Verwendung nicht gespeichert wurde. Der Standardwert lautet `$false`.

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a>SetSelectedFile\( selectedFile \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Wählt die Datei aus, die durch den **SelectedFile**-Parameter angegeben wird.

**SelectedFile** – Microsoft.PowerShell.Host.ISE.ISEFile: Die ISEFile-Datei, die Sie auswählen möchten.

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISEFile-Objekt](The-ISEFile-Object.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
