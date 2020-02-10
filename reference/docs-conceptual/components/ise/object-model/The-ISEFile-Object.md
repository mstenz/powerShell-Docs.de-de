---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Das ISEFile-Objekt
ms.openlocfilehash: 1069e46aa586b8df2050129194a909b90f77b745
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736997"
---
# <a name="the-isefile-object"></a>Das ISEFile-Objekt

Ein **ISEFile**-Objekt stellt eine Datei in Windows-PowerShell® Integrated Scripting Environment (ISE) dar Es handelt sich um eine Instanz der **Microsoft.PowerShell.Host.ISE.ISEFile**-Klasse. In diesem Thema werden die Elementmethoden und -eigenschaften aufgeführt. `$psISE.CurrentFile` und die Dateien in der Dateisammlung auf einer PowerShell-Registerkarte sind Instanzen der \*\***Microsoft.PowerShell.Host.ISE.ISEFile**-Klasse.

## <a name="methods"></a>Methoden

### <a name="save-saveencoding-"></a>Save\( \[saveEncoding\] \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Speichert die Datei auf dem Datenträger.

**\[saveEncoding\]** – Optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll. Der Standardwert lautet **UTF8**.

### <a name="exceptions"></a>Ausnahmen

- **System.IO.IOException**: Die Datei konnte nicht gespeichert werden.

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a>SaveAs\(Dateiname, \[saveEncoding\]\)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Speichert die Datei mit dem angegebenen Namen und der angegebenen Codierung.

**Dateiname**: Zeichenfolge – der Name, der zum Speichern der Datei verwendet werden soll.

**\[saveEncoding\]** – Optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll. Der Standardwert lautet **UTF8**.

### <a name="exceptions"></a>Ausnahmen

- **System.ArgumentNullException**: Der Parameter **Filename** ist NULL.
- **System.ArgumentException**: Der Parameter **filename** ist leer.
- **System.IO.IOException**: Die Datei konnte nicht gespeichert werden.

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a>Eigenschaften

### <a name="displayname"></a>DisplayName

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die Zeichenfolge mit dem Anzeigenamen dieser Datei abruft. Der Name wird auf der Registerkarte **Datei** oben im Editor angezeigt. Ein Sternchen `(*)` am Ende des Namens zeigt an, dass die Datei nicht gespeicherte Änderungen enthält.

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a>Editor

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die das für die angegebene Datei verwendete [Editor-Objekt](The-ISEEditor-Object.md) abruft.

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a>Codieren

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die ursprüngliche Dateicodierung abruft. Dies ist ein **System.Text.Encoding**-Objekt.

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a>FullPath

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die Zeichenfolge abruft, die den vollständigen Pfad der geöffneten Datei angibt.

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a>IsSaved

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte boolesche Eigenschaft, die `$true` zurückgibt, wenn die Datei nach der letzten Änderung gespeichert wurde.

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a>IsUntitled

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die `$true` zurückgibt, wenn für die Datei nie ein Titel festgelegt wurde.

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISEFileCollection-Objekt](The-ISEFileCollection-Object.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
