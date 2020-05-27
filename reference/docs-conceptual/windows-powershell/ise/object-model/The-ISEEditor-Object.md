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
# <a name="the-iseeditor-object"></a><span data-ttu-id="71c8d-103">Das ISEEditor-Objekt</span><span class="sxs-lookup"><span data-stu-id="71c8d-103">The ISEEditor Object</span></span>

<span data-ttu-id="71c8d-104">Ein **ISEEditor**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEEditor-Klasse.</span><span class="sxs-lookup"><span data-stu-id="71c8d-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="71c8d-105">Der Konsolenbereich ist ein **ISEEditor**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="71c8d-106">Jedes [ISEFile](The-ISEFile-Object.md)-Objekt verfügt über ein zugeordnetes **ISEEditor**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="71c8d-107">In den folgenden Abschnitten werden die Methoden und Eigenschaften eines **ISEEditor**-Objekts aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="71c8d-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="71c8d-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="71c8d-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="71c8d-109">Clear\(\)</span></span>

<span data-ttu-id="71c8d-110">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-111">Löscht den Text im Editor.</span><span class="sxs-lookup"><span data-stu-id="71c8d-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="71c8d-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="71c8d-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="71c8d-113">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-114">Führt einen Bildlauf im Editor aus, sodass die Zeile, die dem angegebenen Wert des **lineNumber**-Parameters entspricht, angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="71c8d-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="71c8d-115">Es wird eine Ausnahme ausgelöst, wenn die angegebene Zeilennummer nicht zwischen 1 und der Nummer der letzten Zeile liegt. Dieser Bereich definiert die gültigen Zeilennummern.</span><span class="sxs-lookup"><span data-stu-id="71c8d-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="71c8d-116">**lineNumber** Die Nummer der Zeile, die angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="71c8d-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="71c8d-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="71c8d-117">Focus\(\)</span></span>

<span data-ttu-id="71c8d-118">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-119">Legt den Fokus auf den Editor fest.</span><span class="sxs-lookup"><span data-stu-id="71c8d-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="71c8d-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="71c8d-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="71c8d-121">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-122">Ruft für die durch die Zeilennummer angegebene Zeile die Länge der Zeile als ganze Zahl ab.</span><span class="sxs-lookup"><span data-stu-id="71c8d-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="71c8d-123">**lineNumber** Die Nummer der Zeile, deren Länge abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="71c8d-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="71c8d-124">**Returns** Die Zeilenlänge für die Zeile mit der angegebenen Zeilennummer.</span><span class="sxs-lookup"><span data-stu-id="71c8d-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="71c8d-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="71c8d-125">GoToMatch\(\)</span></span>

<span data-ttu-id="71c8d-126">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="71c8d-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71c8d-127">Verschiebt den Textcursor zum entsprechenden Zeichen, wenn die Eigenschaft **CanGoToMatch** des Editorobjekts `$true` ist. Dies ist der Fall, wenn sich der Textcursor direkt vor einer öffnenden, eckigen oder geschweiften Klammer – `(`,`[`,`{` – oder unmittelbar nach einer schließenden, eckigen oder geschweiften Klammer befindet – `)`,`]`,`}`.</span><span class="sxs-lookup"><span data-stu-id="71c8d-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is `$true`, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - `(`,`[`,`{` - or immediately after a closing parenthesis, bracket, or brace - `)`,`]`,`}`.</span></span> <span data-ttu-id="71c8d-128">Der Textcursor wird vor einer öffnenden bzw. nach einer schließenden Klammer platziert.</span><span class="sxs-lookup"><span data-stu-id="71c8d-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="71c8d-129">Wenn die **CanGoToMatch**-Eigenschaft `$false` lautet, wird mit dieser Methode keine Aktion ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-129">If the **CanGoToMatch** property is `$false`, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="71c8d-130">InsertText\( Text \)</span><span class="sxs-lookup"><span data-stu-id="71c8d-130">InsertText\( text \)</span></span>

<span data-ttu-id="71c8d-131">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-132">Ersetzt die Markierung durch Text oder fügt Text an der aktuellen Position des Textcursors ein.</span><span class="sxs-lookup"><span data-stu-id="71c8d-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="71c8d-133">**text**: Zeichenfolge – der einzufügende Text.</span><span class="sxs-lookup"><span data-stu-id="71c8d-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="71c8d-134">Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="71c8d-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="71c8d-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="71c8d-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="71c8d-136">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-137">Wählt den Text anhand der Parameter **startLine**, **startColumn**, **endLine** und **endColumn** aus.</span><span class="sxs-lookup"><span data-stu-id="71c8d-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="71c8d-138">**startLine**: ganze Zahl – die Zeile, in der die Auswahl beginnt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="71c8d-139">**startColumn**: ganze Zahl – die Spalte in der Startzeile, in der die Auswahl beginnt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="71c8d-140">**endLine**: ganze Zahl – die Zeile, in der die Auswahl endet.</span><span class="sxs-lookup"><span data-stu-id="71c8d-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="71c8d-141">**endColumn**: ganze Zahl – die Spalte in der Endzeile, in der die Auswahl endet.</span><span class="sxs-lookup"><span data-stu-id="71c8d-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="71c8d-142">Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="71c8d-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="71c8d-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="71c8d-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="71c8d-144">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-145">Wählt die gesamte Textzeile aus, in der sich der Textcursor gerade befindet.</span><span class="sxs-lookup"><span data-stu-id="71c8d-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="71c8d-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="71c8d-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="71c8d-147">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-148">Legt die Position des Textcursors auf die Zeilennummer und die Spaltennummer fest.</span><span class="sxs-lookup"><span data-stu-id="71c8d-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="71c8d-149">Es wird eine Ausnahme ausgelöst, wenn die Zeilennummer des Textcursors oder die Spaltennummer des Textcursors außerhalb des jeweils gültigen Bereichs liegt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-149">It throws an exception if either the caret line number or the caret column number are out of their respective valid ranges.</span></span>

<span data-ttu-id="71c8d-150">**lineNumber**: ganze Zahl – die Zeilennummer des Textcursors.</span><span class="sxs-lookup"><span data-stu-id="71c8d-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="71c8d-151">**columnNumber**: ganze Zahl – die Spaltennummer des Textcursors.</span><span class="sxs-lookup"><span data-stu-id="71c8d-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="71c8d-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="71c8d-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="71c8d-153">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="71c8d-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71c8d-154">Führt dazu, dass alle Gliederungsabschnitte erweitert oder reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="71c8d-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="71c8d-155">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="71c8d-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="71c8d-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="71c8d-156">CanGoToMatch</span></span>

<span data-ttu-id="71c8d-157">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="71c8d-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71c8d-158">Die schreibgeschützte boolesche Eigenschaft, die angibt, ob der Textcursor sich neben einer Klammer, eckigen Klammer oder geschweiften Klammer befindet – `()`, `[]`, `{}`.</span><span class="sxs-lookup"><span data-stu-id="71c8d-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - `()`, `[]`, `{}`.</span></span> <span data-ttu-id="71c8d-159">Wenn der Textcursor sich direkt vor der öffnenden Klammer oder unmittelbar nach der schließenden Klammer eines Klammerpaars befindet, lautet der Wert dieser Eigenschaft `$true`.</span><span class="sxs-lookup"><span data-stu-id="71c8d-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is `$true`.</span></span> <span data-ttu-id="71c8d-160">Andernfalls lautet der Wert `$false`.</span><span class="sxs-lookup"><span data-stu-id="71c8d-160">Otherwise, it is `$false`.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="71c8d-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="71c8d-161">CaretColumn</span></span>

<span data-ttu-id="71c8d-162">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-163">Die schreibgeschützte Eigenschaft, die die Spaltennummer abruft, die der Position des Textcursors entspricht.</span><span class="sxs-lookup"><span data-stu-id="71c8d-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="71c8d-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="71c8d-164">CaretLine</span></span>

<span data-ttu-id="71c8d-165">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-166">Die schreibgeschützte Eigenschaft, die die Nummer der Zeile mit dem Textcursor abruft.</span><span class="sxs-lookup"><span data-stu-id="71c8d-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="71c8d-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="71c8d-167">CaretLineText</span></span>

<span data-ttu-id="71c8d-168">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-169">Die schreibgeschützte Eigenschaft, die die vollständige Textzeile abruft, die den Textcursor enthält.</span><span class="sxs-lookup"><span data-stu-id="71c8d-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="71c8d-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="71c8d-170">LineCount</span></span>

<span data-ttu-id="71c8d-171">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-172">Die schreibgeschützte Eigenschaft, die die Anzahl der Zeilen aus dem Editor abruft.</span><span class="sxs-lookup"><span data-stu-id="71c8d-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="71c8d-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="71c8d-173">SelectedText</span></span>

<span data-ttu-id="71c8d-174">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-175">Die schreibgeschützte Eigenschaft, die den ausgewählten Text aus dem Editor abruft.</span><span class="sxs-lookup"><span data-stu-id="71c8d-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="71c8d-176">Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="71c8d-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="71c8d-177">Text</span><span class="sxs-lookup"><span data-stu-id="71c8d-177">Text</span></span>

<span data-ttu-id="71c8d-178">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71c8d-179">Die Lese-/Schreibeigenschaft, die den Text im Editor abruft oder festlegt.</span><span class="sxs-lookup"><span data-stu-id="71c8d-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="71c8d-180">Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="71c8d-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="71c8d-181">Beispielskript</span><span class="sxs-lookup"><span data-stu-id="71c8d-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="71c8d-182">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="71c8d-182">See Also</span></span>

- [<span data-ttu-id="71c8d-183">Das ISEFile-Objekt</span><span class="sxs-lookup"><span data-stu-id="71c8d-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="71c8d-184">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="71c8d-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="71c8d-185">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="71c8d-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="71c8d-186">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="71c8d-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
