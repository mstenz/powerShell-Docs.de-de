---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Schreiben und Ausführen von Skripts in der Windows PowerShell ISE
ms.openlocfilehash: 2e3122a3b436ba878d2c5f9d72d4f9e024d4d031
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737065"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="88137-103">Schreiben und Ausführen von Skripts in der Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="88137-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="88137-104">In diesem Artikel ist beschrieben, wie Skripts im Skriptbereich erstellt, bearbeitet, ausgeführt und gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="88137-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="88137-105">Erstellen und Ausführen von Skripts</span><span class="sxs-lookup"><span data-stu-id="88137-105">How to create and run scripts</span></span>

<span data-ttu-id="88137-106">Sie können Windows PowerShell-Dateien im Skriptbereich öffnen und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="88137-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="88137-107">Bestimmte Dateitypen, die in Windows PowerShell von Interesse sind, sind Skriptdateien (`.ps1`), Skriptdatendateien (`.psd1`) und Skriptmoduldateien (`.psm1`).</span><span class="sxs-lookup"><span data-stu-id="88137-107">Specific file types of interest in Windows PowerShell are script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`).</span></span> <span data-ttu-id="88137-108">Diese Dateitypen werden mit Syntaxfärbung im Skriptbereichs-Editor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="88137-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="88137-109">Andere gängige Dateitypen, die Sie möglicherweise im Skriptbereich öffnen möchten, sind Konfigurationsdateien (`.ps1xml`), XML-Dateien und Textdateien.</span><span class="sxs-lookup"><span data-stu-id="88137-109">Other common file types you may open in the Script Pane are configuration files (`.ps1xml`), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="88137-110">Die Windows PowerShell-Ausführungsrichtlinie bestimmt, ob Sie Skripts ausführen sowie Windows PowerShell-Profile und -Konfigurationsdateien laden können.</span><span class="sxs-lookup"><span data-stu-id="88137-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="88137-111">Die Standardausführungsrichtlinie, „Restricted“, verhindert sowohl das Ausführen jeglicher Skripts als auch das Laden von Profilen.</span><span class="sxs-lookup"><span data-stu-id="88137-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="88137-112">Wenn Sie die Ausführungsrichtlinie ändern möchten, sodass sie das Laden und Verwenden von Profilen zulässt, lesen Sie [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) und [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="88137-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="88137-113">So erstellen Sie eine neue Skriptdatei</span><span class="sxs-lookup"><span data-stu-id="88137-113">To create a new script file</span></span>

<span data-ttu-id="88137-114">Klicken Sie auf der Symbolleiste auf **Neu**, oder klicken Sie im Menü **Datei** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="88137-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="88137-115">Die erstellte Datei wird in einer neuen Dateiregisterkarte unter der aktuellen PowerShell-Registerkarte angezeigt. Denken Sie daran, dass die PowerShell-Registerkarten nur angezeigt werden, wenn mehrere vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="88137-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="88137-116">Standardmäßig wird eine Datei des Typs Skript (`.ps1`) erstellt, diese kann aber mit einem neuen Namen und einer neuen Erweiterung gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="88137-116">By default a file of type script (`.ps1`) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="88137-117">Es können mehrere Skriptdateien auf derselben PowerShell-Registerkarte erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="88137-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="88137-118">So öffnen Sie ein vorhandenes Skript</span><span class="sxs-lookup"><span data-stu-id="88137-118">To open an existing script</span></span>

<span data-ttu-id="88137-119">Klicken Sie auf der Symbolleiste auf **Öffnen**, oder klicken Sie im Menü **Datei** auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="88137-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="88137-120">Wählen Sie im Dialogfeld **Öffnen** die Datei aus, die Sie öffnen möchten.</span><span class="sxs-lookup"><span data-stu-id="88137-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="88137-121">Die geöffnete Datei wird auf einer neuen Registerkarte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="88137-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="88137-122">So schließen Sie eine Skriptregisterkarte</span><span class="sxs-lookup"><span data-stu-id="88137-122">To close a script tab</span></span>

<span data-ttu-id="88137-123">Klicken Sie für die Dateiregisterkarte, die Sie schließen möchten, auf das Symbol **Schließen** (**X**), oder wählen Sie das Menü **Datei** aus, und klicken Sie auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="88137-123">Click the **Close** icon (**X**) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="88137-124">Wurde die Datei seit ihrer letzten Speicherung geändert, werden Sie aufgefordert, die Datei zu speichern oder zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="88137-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="88137-125">So zeigen Sie den Dateipfad an</span><span class="sxs-lookup"><span data-stu-id="88137-125">To display the file path</span></span>

<span data-ttu-id="88137-126">Zeigen Sie auf der Registerkarte der Datei auf den Dateinamen an.</span><span class="sxs-lookup"><span data-stu-id="88137-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="88137-127">Der vollqualifizierte Pfad der Skriptdatei wird als QuickInfo angezeigt.</span><span class="sxs-lookup"><span data-stu-id="88137-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="88137-128">So führen Sie ein Skript aus</span><span class="sxs-lookup"><span data-stu-id="88137-128">To run a script</span></span>

<span data-ttu-id="88137-129">Klicken Sie auf der Symbolleiste auf **Skript ausführen**, oder klicken Sie im Menü **Datei** auf **Ausführen**.</span><span class="sxs-lookup"><span data-stu-id="88137-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="88137-130">So führen Sie einen Abschnitt eines Skripts aus</span><span class="sxs-lookup"><span data-stu-id="88137-130">To run a portion of a script</span></span>

1. <span data-ttu-id="88137-131">Wählen Sie Skriptbereich einen Abschnitt eines Skripts aus.</span><span class="sxs-lookup"><span data-stu-id="88137-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="88137-132">Klicken Sie im Menü **Datei** auf **Auswahl ausführen**, oder klicken Sie auf der Symbolleiste auf **Auswahl ausführen**.</span><span class="sxs-lookup"><span data-stu-id="88137-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="88137-133">So beenden Sie ein Skript, das ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="88137-133">To stop a running script</span></span>

<span data-ttu-id="88137-134">Es gibt mehrere Möglichkeiten, die Ausführung eines Skripts zu beenden.</span><span class="sxs-lookup"><span data-stu-id="88137-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="88137-135">Klicken Sie auf der Symbolleiste auf **Vorgang beenden**.</span><span class="sxs-lookup"><span data-stu-id="88137-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="88137-136">Drücken Sie <kbd>STRG</kbd>+<kbd>UNTBR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88137-136">Press <kbd>CTRL</kbd>+<kbd>BREAK</kbd></span></span>
- <span data-ttu-id="88137-137">Wählen Sie das Menü **Datei** aus, und klicken Sie auf **Vorgang beenden**.</span><span class="sxs-lookup"><span data-stu-id="88137-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="88137-138">Das Drücken von <kbd>STRG</kbd>+<kbd>C</kbd> funktioniert ebenfalls, sofern aktuell kein Text ausgewählt ist. Ist dies der Fall, wird <kbd>STRG</kbd>+<kbd>C</kbd> der Kopierfunktion für den ausgewählten Text zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="88137-138">Pressing <kbd>CTRL</kbd>+<kbd>C</kbd> also works unless some text is currently selected, in which case <kbd>CTRL</kbd>+<kbd>C</kbd> maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="88137-139">Schreiben und Bearbeiten von Text im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="88137-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="88137-140">Sie können im Skriptbereich Text kopieren, ausschneiden, einfügen, suchen und ersetzen.</span><span class="sxs-lookup"><span data-stu-id="88137-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="88137-141">Sie können außerdem die letzte von Ihnen ausgeführte Aktion rückgängig machen und wiederholen.</span><span class="sxs-lookup"><span data-stu-id="88137-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="88137-142">Die Tastenkombinationen für diese Aktionen sind mit denen identisch, die für alle Windows-Anwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="88137-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="88137-143">So geben Sie Text im Skriptbereich ein</span><span class="sxs-lookup"><span data-stu-id="88137-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="88137-144">Bewegen Sie den Cursor in den Skriptbereich, indem Sie auf eine beliebige Stelle im Skriptbereich oder im Menü **Ansicht** auf **Zum Skriptbereich gehen** klicken.</span><span class="sxs-lookup"><span data-stu-id="88137-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="88137-145">Erstellen Sie ein Skript.</span><span class="sxs-lookup"><span data-stu-id="88137-145">Create a script.</span></span> <span data-ttu-id="88137-146">Farbliche Syntaxkennzeichnung und Vervollständigung mit der TAB-TASTE bieten umfangreichere Bearbeitungsfunktionen in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="88137-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="88137-147">Ausführliche Informationen dazu, wie das Nutzen der Funktion Vervollständigung mit der TAB-TASTE beim Eingeben helfen kann, finden Sie unter [Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).</span><span class="sxs-lookup"><span data-stu-id="88137-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="88137-148">So suchen Sie nach Text im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="88137-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="88137-149">Drücken Sie <kbd>STRG</kbd>+<kbd>F</kbd>, oder klicken Sie im Menü **Bearbeiten** auf **Im Skript suchen**, um nach Text an einer beliebigen Stelle zu suchen.</span><span class="sxs-lookup"><span data-stu-id="88137-149">To find text anywhere, press <kbd>CTRL</kbd>+<kbd>F</kbd> or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="88137-150">Um nach Text ab dem Cursor zu suchen, drücken Sie <kbd>F3</kbd>, oder klicken Sie im Menü **Bearbeiten** auf **Im Skript weitersuchen**.</span><span class="sxs-lookup"><span data-stu-id="88137-150">To find text after the cursor, press <kbd>F3</kbd> or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="88137-151">Drücken Sie <kbd>UMSCHALT</kbd>+<kbd>F3</kbd>, oder klicken Sie im Menü **Bearbeiten** auf **Vorheriges im Skript suchen**, um nach Text vor dem Cursor zu suchen.</span><span class="sxs-lookup"><span data-stu-id="88137-151">To find text before the cursor, press <kbd>SHIFT</kbd>+<kbd>F3</kbd> or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="88137-152">So finden und ersetzen Sie Text im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="88137-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="88137-153">Drücken Sie <kbd>STRG</kbd>+<kbd>H</kbd>, oder klicken Sie im Menü **Bearbeiten** auf **Im Skript ersetzen**.</span><span class="sxs-lookup"><span data-stu-id="88137-153">Press <kbd>CTRL</kbd>+<kbd>H</kbd> or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="88137-154">Geben Sie den Suchtext und den Ersetzungstext ein, drücken Sie dann die <kbd>EINGABETASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="88137-154">Enter the text you want to find and the replacement text, then press <kbd>ENTER</kbd>.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="88137-155">So wechseln Sie zu einer bestimmten Zeile des Texts im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="88137-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="88137-156">Drücken Sie im Skriptbereich die Tastenkombination <kbd>STRG</kbd>+<kbd>G</kbd>, oder klicken Sie im Menü **Bearbeiten** auf **Gehe zu Zeile**.</span><span class="sxs-lookup"><span data-stu-id="88137-156">In the Script Pane, press <kbd>CTRL</kbd>+<kbd>G</kbd> or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="88137-157">Geben Sie eine Zeilennummer ein.</span><span class="sxs-lookup"><span data-stu-id="88137-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="88137-158">So kopieren Sie Text in den Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="88137-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="88137-159">Wählen Sie im Skriptbereich den Text aus, den Sie kopieren möchten.</span><span class="sxs-lookup"><span data-stu-id="88137-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="88137-160">Drücken Sie <kbd>STRG</kbd>+<kbd>C</kbd>, klicken Sie auf der Symbolleiste auf das Symbol **Kopieren**, oder klicken Sie im Menü **Bearbeiten** auf **Kopieren**.</span><span class="sxs-lookup"><span data-stu-id="88137-160">Press <kbd>CTRL</kbd>+<kbd>C</kbd> or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="88137-161">So schneiden Sie Text im Skriptbereich aus</span><span class="sxs-lookup"><span data-stu-id="88137-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="88137-162">Wählen Sie im Skriptbereich den Text aus, den Sie ausschneiden möchten.</span><span class="sxs-lookup"><span data-stu-id="88137-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="88137-163">Drücken Sie <kbd>STRG</kbd>+<kbd>X</kbd>, oder klicken Sie auf der Symbolleiste auf das Symbol **Ausschneiden**, oder klicken Sie im Menü **Bearbeiten** auf **Ausschneiden**.</span><span class="sxs-lookup"><span data-stu-id="88137-163">Press <kbd>CTRL</kbd>+<kbd>X</kbd> or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="88137-164">So fügen Sie Text in den Skriptbereich ein</span><span class="sxs-lookup"><span data-stu-id="88137-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="88137-165">Drücken Sie <kbd>STRG</kbd>+<kbd>V</kbd>, oder klicken Sie auf der Symbolleiste auf das Symbol **Einfügen**, oder klicken Sie im Menü **Bearbeiten** auf **Einfügen**.</span><span class="sxs-lookup"><span data-stu-id="88137-165">Press <kbd>CTRL</kbd>+<kbd>V</kbd> or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="88137-166">So machen Sie eine Aktion im Skriptbereich rückgängig</span><span class="sxs-lookup"><span data-stu-id="88137-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="88137-167">Drücken Sie <kbd>STRG</kbd>+<kbd>Z</kbd>, oder klicken Sie auf der Symbolleiste auf das Symbol **Rückgängig**, oder klicken Sie im Menü **Bearbeiten** auf **Rückgängig**.</span><span class="sxs-lookup"><span data-stu-id="88137-167">Press <kbd>CTRL</kbd>+<kbd>Z</kbd> or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="88137-168">So wiederholen Sie eine Aktion im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="88137-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="88137-169">Drücken Sie <kbd>STRG</kbd>+<kbd>Y</kbd>, oder klicken Sie auf der Symbolleiste auf das Symbol **Wiederholen**, oder klicken Sie im Menü **Bearbeiten** auf **Wiederholen**.</span><span class="sxs-lookup"><span data-stu-id="88137-169">Press <kbd>CTRL</kbd>+<kbd>Y</kbd> or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="88137-170">Speichern eines Skripts</span><span class="sxs-lookup"><span data-stu-id="88137-170">How to save a script</span></span>

<span data-ttu-id="88137-171">Ein Sternchen wird neben dem Skriptnamen angezeigt, um zu kennzeichnen, dass eine Datei nicht gespeichert wurde, seit sie geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="88137-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="88137-172">Das Sternchen verschwindet, wenn die Datei gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="88137-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="88137-173">So speichern Sie ein Skript</span><span class="sxs-lookup"><span data-stu-id="88137-173">To save a script</span></span>

<span data-ttu-id="88137-174">Drücken Sie <kbd>STRG</kbd>+<kbd>S</kbd>, oder klicken Sie auf der Symbolleiste auf das Symbol **Speichern**, oder klicken Sie im Menü **Datei** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="88137-174">Press <kbd>CTRL</kbd>+<kbd>S</kbd> or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="88137-175">So geben Sie einem Skript einen Namen und speichern es</span><span class="sxs-lookup"><span data-stu-id="88137-175">To save and name a script</span></span>

1. <span data-ttu-id="88137-176">Klicken Sie im Menü **Datei** auf **Speichern unter**.</span><span class="sxs-lookup"><span data-stu-id="88137-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="88137-177">Das Dialogfeld **Speichern unter** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="88137-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="88137-178">Geben Sie in das Feld **Dateiname** einen Namen für die Datei ein.</span><span class="sxs-lookup"><span data-stu-id="88137-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="88137-179">Wählen Sie im Feld **Dateityp** einen Dateityp aus.</span><span class="sxs-lookup"><span data-stu-id="88137-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="88137-180">Wählen Sie beispielsweise im Feld **Dateityp** den Typ „PowerShell-Skripts (`*.ps1`)“ aus.</span><span class="sxs-lookup"><span data-stu-id="88137-180">For example, in the **Save as type** box, select 'PowerShell Scripts (`*.ps1`)'.</span></span>
4. <span data-ttu-id="88137-181">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="88137-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="88137-182">So speichern Sie ein Skript in ASCII-Codierung</span><span class="sxs-lookup"><span data-stu-id="88137-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="88137-183">Windows PowerShell ISE speichert neue Skriptdateien (`.ps1`), Skriptdatendateien (`.psd1`) und Skriptmoduldateien (`.psm1`) standardmäßig im Unicode-Format (BigEndianUnicode).</span><span class="sxs-lookup"><span data-stu-id="88137-183">By default, Windows PowerShell ISE saves new script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="88137-184">Um ein Skript in einer anderen Codierung, z. B. ASCII (ANSI), zu speichern, verwenden Sie die **Save**- oder **SaveAs**-Methode des [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="88137-184">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="88137-185">Im folgenden Befehl wird ein neues Skript als „MyScript.ps1“ mit ASCII-Codierung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="88137-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="88137-186">Im folgenden Befehl wird die aktuelle Skriptdatei durch eine Datei ersetzt, die denselben Namen hat, aber in ASCII-Codierung vorliegt.</span><span class="sxs-lookup"><span data-stu-id="88137-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="88137-187">Im folgenden Befehl wird die Codierung der aktuellen Datei abgerufen.</span><span class="sxs-lookup"><span data-stu-id="88137-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="88137-188">Windows PowerShell ISE unterstützt die folgenden Codierungsoptionen: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 und Default.</span><span class="sxs-lookup"><span data-stu-id="88137-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="88137-189">Der Wert der Option „Default“ ist je nach System unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="88137-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="88137-190">Windows PowerShell ISE ändert die Codierung von Skriptdateien nicht, wenn Sie die Befehle „Speichern“ oder „Speichern unter“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="88137-190">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="88137-191">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="88137-191">See Also</span></span>

- [<span data-ttu-id="88137-192">Kennenlernen der Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="88137-192">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
