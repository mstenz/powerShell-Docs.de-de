---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Das ISEFile-Objekt
ms.technology: powershell
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: fe0b2396de747bf88e780df505f5f7991e3e0b6f
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isefile-object"></a>Das ISEFile-Objekt
  Ein **ISEFile**-Objekt stellt eine Datei in Windows-PowerShell® Integrated Scripting Environment (ISE) dar Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEFile-Klasse. In diesem Thema werden die Elementmethoden und -eigenschaften aufgeführt. **$psISE.CurrentFile** und die Dateien in der DateiSammlung auf einer PowerShell-Registerkarte sind Instanzen der Microsoft.PowerShell.Host.ISE.ISEFile-Klasse.

## <a name="methods"></a>Methoden

###  <a name="a-namesave-overridea-save-saveencoding-"></a><a name="save-override"></a> Save\( \[saveEncoding\] \)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Speichert die Datei auf dem Datenträger.

 **\[saveEncoding\]** – Optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 – Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll Der Standardwert lautet **UTF8**.

 **Ausnahmen**
 -   **System.IO.IOException**: Die Datei konnte nicht gespeichert werden.

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <a name="a-namesaveasa-saveasfilename-saveencoding"></a><a name="saveas"></a> SaveAs\(Dateiname, \[saveEncoding\]\)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Speichert die Datei mit dem angegebenen Namen und der angegebenen Codierung.

 **Dateiname**: Zeichenfolge – der Name, der zum Speichern der Datei verwendet werden soll.

 **\[saveEncoding\]** – Optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 – Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll Der Standardwert lautet **UTF8**.

 **Ausnahmen**
 -   **System.ArgumentNullException**: Der **filename**-Parameter ist NULL.

-   **System.ArgumentException**: Der **filename**-Parameter ist leer.

-   **System.IO.IOException**: Die Datei konnte nicht gespeichert werden.

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a>Eigenschaften

###  <a name="a-namedisplaynamea-displayname"></a><a name="Displayname"></a> DisplayName
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die die Zeichenfolge mit dem Anzeigenamen dieser Datei abruft. Der Name wird auf der Registerkarte **Datei** oben im Editor angezeigt. Ein Sternchen \(\*\) am Ende des Namens zeigt an, dass die Datei nicht gespeicherte Änderungen enthält.

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <a name="a-nameeditora-editor"></a><a name="Editor"></a> Editor
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die das für die angegebene Datei verwendete [Editor-Objekt](The-ISEEditor-Object.md) abruft.

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <a name="a-nameencodinga-encoding"></a><a name="Encoding"></a> Encoding
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die die ursprüngliche Dateicodierung abruft. Dies ist ein **System.Text.Encoding**-Objekt.

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <a name="a-namefullpatha-fullpath"></a><a name="FullPath"></a> FullPath
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die die Zeichenfolge abruft, die den vollständigen Pfad der geöffneten Datei angibt.

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <a name="a-nameissaveda-issaved"></a><a name="IsSaved"></a> IsSaved
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte boolesche Eigenschaft, die **$true** zurückgibt, wenn die Datei nach der letzten Änderung gespeichert wurde.

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <a name="a-nameisuntitleda-isuntitled"></a><a name="IsUntitled"></a> IsUntitled
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die **$true** zurückgibt, wenn für die Datei nie ein Titel festgelegt wurde.

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a>Weitere Informationen
- [Das ISEFileCollection-Objekt](The-ISEFileCollection-Object.md) 
- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)

  
