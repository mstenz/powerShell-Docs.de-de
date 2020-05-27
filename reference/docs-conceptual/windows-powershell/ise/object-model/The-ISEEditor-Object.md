---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Das ISEEditor-Objekt
ms.openlocfilehash: cb63acebc1a8bb9fa6cc07199088ae0d5441bc91
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809696"
---
# <a name="the-iseeditor-object"></a>Das ISEEditor-Objekt

Ein **ISEEditor**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEEditor-Klasse. Der Konsolenbereich ist ein **ISEEditor**-Objekt. Jedes [ISEFile](The-ISEFile-Object.md)-Objekt verfügt über ein zugeordnetes **ISEEditor**-Objekt. In den folgenden Abschnitten werden die Methoden und Eigenschaften eines **ISEEditor**-Objekts aufgeführt.

## <a name="methods"></a>Methoden

### <a name="clear"></a>Clear\(\)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Löscht den Text im Editor.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Führt einen Bildlauf im Editor aus, sodass die Zeile, die dem angegebenen Wert des **lineNumber**-Parameters entspricht, angezeigt wird. Es wird eine Ausnahme ausgelöst, wenn die angegebene Zeilennummer nicht zwischen 1 und der Nummer der letzten Zeile liegt. Dieser Bereich definiert die gültigen Zeilennummern.

**lineNumber** Die Nummer der Zeile, die angezeigt werden soll.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Focus\(\)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Legt den Fokus auf den Editor fest.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Ruft für die durch die Zeilennummer angegebene Zeile die Länge der Zeile als ganze Zahl ab.

**lineNumber** Die Nummer der Zeile, deren Länge abgerufen werden soll.

**Returns** Die Zeilenlänge für die Zeile mit der angegebenen Zeilennummer.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Verschiebt den Textcursor zum entsprechenden Zeichen, wenn die Eigenschaft **CanGoToMatch** des Editorobjekts `$true` ist. Dies ist der Fall, wenn sich der Textcursor direkt vor einer öffnenden, eckigen oder geschweiften Klammer – `(`,`[`,`{` – oder unmittelbar nach einer schließenden, eckigen oder geschweiften Klammer befindet – `)`,`]`,`}`. Der Textcursor wird vor einer öffnenden bzw. nach einer schließenden Klammer platziert. Wenn die **CanGoToMatch**-Eigenschaft `$false` lautet, wird mit dieser Methode keine Aktion ausgeführt.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( Text \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Ersetzt die Markierung durch Text oder fügt Text an der aktuellen Position des Textcursors ein.

**text**: Zeichenfolge – der einzufügende Text.

Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Select\( startLine, startColumn, endLine, endColumn \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Wählt den Text anhand der Parameter **startLine**, **startColumn**, **endLine** und **endColumn** aus.

**startLine**: ganze Zahl – die Zeile, in der die Auswahl beginnt.

**startColumn**: ganze Zahl – die Spalte in der Startzeile, in der die Auswahl beginnt.

**endLine**: ganze Zahl – die Zeile, in der die Auswahl endet.

**endColumn**: ganze Zahl – die Spalte in der Endzeile, in der die Auswahl endet.

Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Wählt die gesamte Textzeile aus, in der sich der Textcursor gerade befindet.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Legt die Position des Textcursors auf die Zeilennummer und die Spaltennummer fest. Es wird eine Ausnahme ausgelöst, wenn die Zeilennummer des Textcursors oder die Spaltennummer des Textcursors außerhalb des jeweils gültigen Bereichs liegt.

**lineNumber**: ganze Zahl – die Zeilennummer des Textcursors.

**columnNumber**: ganze Zahl – die Spaltennummer des Textcursors.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Führt dazu, dass alle Gliederungsabschnitte erweitert oder reduziert werden.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Eigenschaften

### <a name="cangotomatch"></a>CanGoToMatch

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die schreibgeschützte boolesche Eigenschaft, die angibt, ob der Textcursor sich neben einer Klammer, eckigen Klammer oder geschweiften Klammer befindet – `()`, `[]`, `{}`. Wenn der Textcursor sich direkt vor der öffnenden Klammer oder unmittelbar nach der schließenden Klammer eines Klammerpaars befindet, lautet der Wert dieser Eigenschaft `$true`. Andernfalls lautet der Wert `$false`.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die Spaltennummer abruft, die der Position des Textcursors entspricht.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die Nummer der Zeile mit dem Textcursor abruft.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die vollständige Textzeile abruft, die den Textcursor enthält.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die Anzahl der Zeilen aus dem Editor abruft.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die den ausgewählten Text aus dem Editor abruft.

Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.

### <a name="text"></a>Text

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die Lese-/Schreibeigenschaft, die den Text im Editor abruft oder festlegt.

Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.

## <a name="scripting-example"></a>Beispielskript

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISEFile-Objekt](The-ISEFile-Object.md)
- [Das PowerShellTab-Objekt](The-PowerShellTab-Object.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
