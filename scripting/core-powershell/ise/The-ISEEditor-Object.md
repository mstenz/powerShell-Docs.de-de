---
title: Das ISEEditor-Objekt
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0101daf8-4e31-4e4c-ab89-01d95dcb8f46
---
# Das ISEEditor-Objekt
  Ein **ISEEditor**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEEditor-Klasse. Der Konsolenbereich ist ein **ISEEditor**-Objekt. Jedes [ISEFile](The-ISEFile-Object.md)-Objekt verfügt über ein zugeordnetes **ISEEditor**-Objekt. In den folgenden Abschnitten werden die Methoden und Eigenschaften eines **ISEEditor**-Objekts aufgeführt.

## Methoden

### Clear()
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Löscht den Text im Editor.

```
# Clears the text in the Console pane.
$psIse.CurrentPowerShellTab.ConsolePane.Clear()

```

### EnsureVisible(int lineNumber)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Führt einen Bildlauf im Editor aus, sodass die Zeile, die dem angegebenen Wert des **lineNumber**-Parameters entspricht, angezeigt wird. Es wird eine Ausnahme ausgelöst, wenn die angegebene Zeilennummer nicht zwischen 1 und der Nummer der letzten Zeile liegt. Dieser Bereich definiert die gültigen Zeilennummern.

 **lineNumber**
 Die Nummer der Zeile, die angezeigt werden soll.

```
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psIse.CurrentFile.Editor.EnsureVisible(5)

```

### Focus()
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Legt den Fokus auf den Editor fest.

```
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### GetLineLength(int lineNumber)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Ruft für die durch die Zeilennummer angegebene Zeile die Länge der Zeile als ganze Zahl ab.

 **lineNumber**
 Die Nummer der Zeile, deren Länge abgerufen werden soll.

 **Rückgabe**
 Die Zeilenlänge für die Zeile mit der angegebenen Zeilennummer.

```
# Gets the length of the first line in the text of the Command pane. 
$psIse.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### GoToMatch()
  In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten. 

 Verschiebt den Textcursor zum entsprechenden Zeichen, wenn die **CanGoToMatch**-Eigenschaft des Editor-Objekts **$true** ist. Dies tritt ein, wenn sich der Textcursor direkt vor einer öffnenden Klammer, eckigen Klammer oder geschweiften Klammer ((,[,{) oder nach einer schließenden Klammer, eckigen Klammer oder geschweiften Klammer (),],}) befindet.  Der Textcursor wird vor einer öffnenden bzw. nach einer schließenden Klammer platziert. Wenn die **CanGoToMatch**-Eigenschaft **$false** ist, wird mit dieser Methode keine Aktion ausgeführt. Siehe [CanGoToMatch](#cangotomatch).

```
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### InsertText( text )
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Ersetzt die Markierung durch Text oder fügt Text an der aktuellen Position des Textcursors ein.

 **text** – Zeichenfolge
 Der einzufügende Text.

 Weitere Informationen finden Sie im [Beispielskript](#example) weiter unten in diesem Thema.

### Select( startLine, startColumn, endLine, endColumn )
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Wählt den Text anhand der Parameter **startLine**, **startColumn**, **endLine** und **endColumn** aus.

 **startLine** – ganze Zahl
 Die Zeile, in der die Auswahl beginnt.

 **startColumn** – ganze Zahl
 Die Spalte in die Startzeile, in der die Auswahl beginnt.

 **endLine** – ganze Zahl
 Die Zeile, in der die Auswahl endet.

 **endColumn** – ganze Zahl
 Die Spalte in die Endzeile, in der die Auswahl endet.

 Weitere Informationen finden Sie im [Beispielskript](#example) weiter unten in diesem Thema.

### SelectCaretLine()
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Wählt die gesamte Textzeile aus, in der sich der Textcursor gerade befindet.

```
# First, set the caret position on line 5.
$psIse.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psIse.CurrentFile.Editor.SelectCaretLine()

```

### SetCaretPosition( lineNumber, columnNumber )
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Legt die Position des Textcursors auf die Zeilennummer und die Spaltennummer fest. Es wird eine Ausnahme ausgelöst, wenn die Zeilennummer des Textcursors oder die Spaltennummer des Textcursors außerhalb des jeweils gültigen Bereichs liegt.

 **lineNumber** – ganze Zahl
 Die Zeilennummer des Textcursors.

 **columnNumber** – ganze Zahl
 Die Spaltennummer des Textcursors.

```
# Set the CaretPosition.
$psIse.CurrentFile.Editor.SetCaretPosition(5,1)
```

### ToggleOutliningExpansion()
  In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten. 

 Führt dazu, dass alle Gliederungsabschnitte erweitert oder reduziert werden.

```
# Toggle the outlining expansion
$psIse.CurrentFile.Editor.ToggleOutliningExpansion()

```

## Eigenschaften

###  <a name="CanGoToMatch"></a> CanGoToMatch
  In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten. 

 Die schreibgeschützte boolesche Eigenschaft, die angibt, ob der Textcursor sich neben einer Klammer, eckigen Klammer oder geschweiften Klammer befindet: (), [], {}. Wenn der Textcursor sich direkt vor der öffnenden Klammer oder unmittelbar nach der schließenden Klammer eines Klammerpaars befindet, lautet der Wert dieser Eigenschaft **$true**. Andernfalls lautet er **$false**.

```
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psIse.CurrentFile.Editor.CanGoToMatch

```

###  <a name="CaretColumn"></a> CaretColumn
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die die Spaltennummer abruft, die der Position des Textcursors entspricht.

```
# Get the CaretColumn.
$psIse.CurrentFile.Editor.CaretColumn

```

###  <a name="CaretLine"></a> CaretLine
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die der Nummer der Zeile mit dem Textcursor abruft.

```
# Get the CaretLine.
$psIse.CurrentFile.Editor.CaretLine

```

###  <a name="caretlinetext"></a> CaretLineText
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die die Nummer der Zeile mit dem Textcursor abruft.

```
# Get all of the text on the line that contains the caret.
$psIse.CurrentFile.Editor.CaretLineText

```

###  <a name="LineCount"></a> LineCount
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die die Anzahl der Zeilen aus dem Editor abruft.

```
# Get the LineCount.
$psIse.CurrentFile.Editor.LineCount

```

###  <a name="SelectedText"></a> SelectedText
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die schreibgeschützte Eigenschaft, die den ausgewählten Text aus dem Editor abruft.

 Weitere Informationen finden Sie im [Beispielskript](#example) weiter unten in diesem Thema.

###  <a name="Text"></a> Text
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Die Lese-/Schreibeigenschaft, die den Text im Editor abruft oder festlegt.

 Weitere Informationen finden Sie im [Beispielskript](#example) weiter unten in diesem Thema.

##  <a name="example"></a> Beispielskript

```

# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase. 
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor=$psIse.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line. 
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## Weitere Informationen
 [Das ISEFile-Objekt](The-ISEFile-Object.md) 
 [Das PowerShellTab-Objekt](The-PowerShellTab-Object.md) 
 [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
 [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
 [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)

  


<!--HONumber=May16_HO2-->


