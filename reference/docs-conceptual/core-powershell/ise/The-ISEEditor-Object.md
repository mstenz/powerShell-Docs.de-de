---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEEditor-Objekt
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="cb2a5-103">Das ISEEditor-Objekt</span><span class="sxs-lookup"><span data-stu-id="cb2a5-103">The ISEEditor Object</span></span>

<span data-ttu-id="cb2a5-104">Ein **ISEEditor**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEEditor-Klasse.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="cb2a5-105">Der Konsolenbereich ist ein **ISEEditor**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="cb2a5-106">Jedes [ISEFile](The-ISEFile-Object.md)-Objekt verfügt über ein zugeordnetes **ISEEditor**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="cb2a5-107">In den folgenden Abschnitten werden die Methoden und Eigenschaften eines **ISEEditor**-Objekts aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="cb2a5-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="cb2a5-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="cb2a5-109">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-109">Clear\(\)</span></span>

<span data-ttu-id="cb2a5-110">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-111">Löscht den Text im Editor.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="cb2a5-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="cb2a5-113">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-114">Führt einen Bildlauf im Editor aus, sodass die Zeile, die dem angegebenen Wert des **lineNumber**-Parameters entspricht, angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="cb2a5-115">Es wird eine Ausnahme ausgelöst, wenn die angegebene Zeilennummer nicht zwischen 1 und der Nummer der letzten Zeile liegt. Dieser Bereich definiert die gültigen Zeilennummern.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="cb2a5-116">**lineNumber** Die Nummer der Zeile, die angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="cb2a5-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-117">Focus\(\)</span></span>

<span data-ttu-id="cb2a5-118">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-119">Legt den Fokus auf den Editor fest.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="cb2a5-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="cb2a5-121">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-122">Ruft für die durch die Zeilennummer angegebene Zeile die Länge der Zeile als ganze Zahl ab.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="cb2a5-123">**lineNumber** Die Nummer der Zeile, deren Länge abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="cb2a5-124">**Returns** Die Zeilenlänge für die Zeile mit der angegebenen Zeilennummer.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="cb2a5-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-125">GoToMatch\(\)</span></span>

<span data-ttu-id="cb2a5-126">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cb2a5-127">Verschiebt den Textcursor zum entsprechenden Zeichen, wenn die Eigenschaft **CanGoToMatch** des Editorobjekts **$true** ist. Dies tritt ein, wenn sich der Textcursor direkt vor einer öffnenden, eckigen oder geschweiften Klammer – \(, \[, { – oder unmittelbar nach einer schließenden, eckigen oder geschweiften Klammer befindet – \), \], }.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="cb2a5-128">Der Textcursor wird vor einer öffnenden bzw. nach einer schließenden Klammer platziert.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="cb2a5-129">Wenn die **CanGoToMatch**-Eigenschaft **$false** ist, wird mit dieser Methode keine Aktion ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="cb2a5-130">InsertText\( Text \)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-130">InsertText\( text \)</span></span>

<span data-ttu-id="cb2a5-131">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-132">Ersetzt die Markierung durch Text oder fügt Text an der aktuellen Position des Textcursors ein.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="cb2a5-133">**text**: Zeichenfolge – der einzufügende Text.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="cb2a5-134">Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="cb2a5-135">Select\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="cb2a5-136">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-137">Wählt den Text anhand der Parameter **startLine**, **startColumn**, **endLine** und **endColumn** aus.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="cb2a5-138">**startLine**: ganze Zahl – die Zeile, in der die Auswahl beginnt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="cb2a5-139">**startColumn**: ganze Zahl – die Spalte in der Startzeile, in der die Auswahl beginnt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="cb2a5-140">**endLine**: ganze Zahl – die Zeile, in der die Auswahl endet.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="cb2a5-141">**endColumn**: ganze Zahl – die Spalte in der Endzeile, in der die Auswahl endet.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="cb2a5-142">Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="cb2a5-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="cb2a5-144">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-145">Wählt die gesamte Textzeile aus, in der sich der Textcursor gerade befindet.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="cb2a5-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="cb2a5-147">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-148">Legt die Position des Textcursors auf die Zeilennummer und die Spaltennummer fest.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="cb2a5-149">Es wird eine Ausnahme ausgelöst, wenn die Zeilennummer des Textcursors oder die Spaltennummer des Textcursors außerhalb des jeweils gültigen Bereichs liegt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="cb2a5-150">**lineNumber**: ganze Zahl – die Zeilennummer des Textcursors.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="cb2a5-151">**columnNumber**: ganze Zahl – die Spaltennummer des Textcursors.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="cb2a5-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="cb2a5-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="cb2a5-153">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cb2a5-154">Führt dazu, dass alle Gliederungsabschnitte erweitert oder reduziert werden.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="cb2a5-155">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="cb2a5-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="cb2a5-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="cb2a5-156">CanGoToMatch</span></span>

<span data-ttu-id="cb2a5-157">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cb2a5-158">Die schreibgeschützte boolesche Eigenschaft, die angibt, ob der Textcursor sich neben einer Klammer, eckigen Klammer oder geschweiften Klammer befindet – \(\), \[\], {}.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="cb2a5-159">Wenn der Textcursor sich direkt vor der öffnenden Klammer oder unmittelbar nach der schließenden Klammer eines Klammerpaars befindet, lautet der Wert dieser Eigenschaft **$true**.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="cb2a5-160">Andernfalls lautet er **$false**.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="cb2a5-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="cb2a5-161">CaretColumn</span></span>

<span data-ttu-id="cb2a5-162">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-163">Die schreibgeschützte Eigenschaft, die die Spaltennummer abruft, die der Position des Textcursors entspricht.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="cb2a5-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="cb2a5-164">CaretLine</span></span>

<span data-ttu-id="cb2a5-165">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-166">Die schreibgeschützte Eigenschaft, die die Nummer der Zeile mit dem Textcursor abruft.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="cb2a5-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="cb2a5-167">CaretLineText</span></span>

<span data-ttu-id="cb2a5-168">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-169">Die schreibgeschützte Eigenschaft, die die vollständige Textzeile abruft, die den Textcursor enthält.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="cb2a5-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="cb2a5-170">LineCount</span></span>

<span data-ttu-id="cb2a5-171">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-172">Die schreibgeschützte Eigenschaft, die die Anzahl der Zeilen aus dem Editor abruft.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="cb2a5-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="cb2a5-173">SelectedText</span></span>

<span data-ttu-id="cb2a5-174">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-175">Die schreibgeschützte Eigenschaft, die den ausgewählten Text aus dem Editor abruft.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="cb2a5-176">Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="cb2a5-177">Text</span><span class="sxs-lookup"><span data-stu-id="cb2a5-177">Text</span></span>

<span data-ttu-id="cb2a5-178">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cb2a5-179">Die Lese-/Schreibeigenschaft, die den Text im Editor abruft oder festlegt.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="cb2a5-180">Weitere Informationen finden Sie im [Beispielskript](#scripting-example) weiter unten in diesem Thema.</span><span class="sxs-lookup"><span data-stu-id="cb2a5-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="cb2a5-181">Beispielskript</span><span class="sxs-lookup"><span data-stu-id="cb2a5-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cb2a5-182">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cb2a5-182">See Also</span></span>

- [<span data-ttu-id="cb2a5-183">Das ISEFile-Objekt</span><span class="sxs-lookup"><span data-stu-id="cb2a5-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="cb2a5-184">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="cb2a5-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="cb2a5-185">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="cb2a5-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="cb2a5-186">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="cb2a5-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)