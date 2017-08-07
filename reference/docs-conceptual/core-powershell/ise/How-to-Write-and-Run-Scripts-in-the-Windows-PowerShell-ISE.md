---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Schreiben und Ausführen von Skripts in der Windows PowerShell ISE"
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 871a4b6f4575af4f823a6957dc971335497320a4
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="b163d-103">Schreiben und Ausführen von Skripts in der Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b163d-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>
<span data-ttu-id="b163d-104">In diesem Thema ist beschrieben, wie Skripts im Skriptbereich erstellt, bearbeitet, ausgeführt und gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b163d-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

-   [<span data-ttu-id="b163d-105">Erstellen und Ausführen von Skripts</span><span class="sxs-lookup"><span data-stu-id="b163d-105">How to create and run scripts</span></span>](#bkmk_1)

-   [<span data-ttu-id="b163d-106">Schreiben und Bearbeiten von Text im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="b163d-106">How to write and edit text in the Script Pane</span></span>](#bkmk_2)

-   [<span data-ttu-id="b163d-107">Speichern eines Skripts</span><span class="sxs-lookup"><span data-stu-id="b163d-107">How to save a script</span></span>](#bkmk_3)

## <span data-ttu-id="b163d-108"><a name="bkmk_1"></a>Erstellen und Ausführen von Skripts</span><span class="sxs-lookup"><span data-stu-id="b163d-108"><a name="bkmk_1"></a>How to create and run scripts</span></span>
<span data-ttu-id="b163d-109">Sie können Windows PowerShell®-Dateien im Skriptbereich öffnen und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="b163d-109">You can open and edit Windows PowerShell® files in the Script Pane.</span></span> <span data-ttu-id="b163d-110">Die speziellen Dateitypen für Windows PowerShell® sind Skriptdateien (.ps1), Skriptdatendateien (.psd1) und Skriptmoduldateien (.psm1).</span><span class="sxs-lookup"><span data-stu-id="b163d-110">Specific file types of interest in Windows PowerShell® are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="b163d-111">Diese Dateitypen werden mit Syntaxfärbung im Skriptbereichs-Editor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b163d-111">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="b163d-112">Andere gängige Dateitypen, die Sie möglicherweise im Skriptbereich öffnen möchten, sind Konfigurationsdateien (PS1XML), XML-Dateien und Textdateien.</span><span class="sxs-lookup"><span data-stu-id="b163d-112">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="b163d-113">Die Windows PowerShell-Ausführungsrichtlinie bestimmt, ob Sie Skripts ausführen sowie Windows PowerShell-Profile und -Konfigurationsdateien laden können.</span><span class="sxs-lookup"><span data-stu-id="b163d-113">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="b163d-114">Die Standardausführungsrichtlinie, „Restricted“, verhindert sowohl das Ausführen jeglicher Skripts als auch das Laden von Profilen.</span><span class="sxs-lookup"><span data-stu-id="b163d-114">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="b163d-115">Wenn Sie die Ausführungsrichtlinie ändern möchten, sodass sie das Laden und Verwenden von Profilen zulässt, lesen Sie [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) und [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="b163d-115">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/en-us/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="b163d-116">So erstellen Sie eine neue Skriptdatei</span><span class="sxs-lookup"><span data-stu-id="b163d-116">To create a new script file</span></span>
<span data-ttu-id="b163d-117">Klicken Sie auf der Symbolleiste auf **Neu**, oder klicken Sie im Menü **Datei** auf **Neu**.</span><span class="sxs-lookup"><span data-stu-id="b163d-117">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="b163d-118">Die erstellte Datei wird in einer neuen Dateiregisterkarte unter der aktuellen PowerShell-Registerkarte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b163d-118">The created file appears in a new file tab under the current PowerShell tab.</span></span> <span data-ttu-id="b163d-119">Denken Sie daran, dass die PowerShell-Registerkarten nur angezeigt werden, wenn mehrere vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b163d-119">Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="b163d-120">Standardmäßig wird eine Datei des Typs Skript (PS1) erstellt, diese kann aber mit einem neuen Namen und einer neuen Erweiterung gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b163d-120">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="b163d-121">Es können mehrere Skriptdateien auf derselben PowerShell-Registerkarte erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="b163d-121">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="b163d-122">So öffnen Sie ein vorhandenes Skript</span><span class="sxs-lookup"><span data-stu-id="b163d-122">To open an existing script</span></span>
<span data-ttu-id="b163d-123">Klicken Sie auf der Symbolleiste auf **Öffnen…**, oder klicken Sie im Menü **Datei** auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="b163d-123">On the toolbar, click **Open…**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="b163d-124">Wählen Sie im Dialogfeld **Öffnen** die Datei aus, die Sie öffnen möchten.</span><span class="sxs-lookup"><span data-stu-id="b163d-124">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="b163d-125">Die geöffnete Datei wird auf einer neuen Registerkarte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b163d-125">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="b163d-126">So schließen Sie eine Skriptregisterkarte</span><span class="sxs-lookup"><span data-stu-id="b163d-126">To close a script tab</span></span>
<span data-ttu-id="b163d-127">Klicken Sie auf die Skriptregisterkarte des Skripts, das Sie schließen möchten, und führen Sie dann einen der folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="b163d-127">Click the script tab of the script you want to close, then do one of the following:</span></span>

1.  <span data-ttu-id="b163d-128">Klicken Sie auf das Symbol **Schließen** (X) auf der Skriptregisterkarte.</span><span class="sxs-lookup"><span data-stu-id="b163d-128">Click the **Close** icon (X) on the script tab.</span></span>

2.  <span data-ttu-id="b163d-129">Klicken Sie im Menü **Datei** auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="b163d-129">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="b163d-130">Wurde die Datei seit ihrer letzten Speicherung geändert, werden Sie aufgefordert, die Datei zu speichern oder zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="b163d-130">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="b163d-131">So zeigen Sie den Dateipfad an</span><span class="sxs-lookup"><span data-stu-id="b163d-131">To display the file path</span></span>
<span data-ttu-id="b163d-132">Zeigen Sie auf der Registerkarte der Datei auf den Dateinamen an.</span><span class="sxs-lookup"><span data-stu-id="b163d-132">On the file tab, point to the file name.</span></span> <span data-ttu-id="b163d-133">Der vollqualifizierte Pfad der Skriptdatei wird als QuickInfo angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b163d-133">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="b163d-134">So führen Sie ein Skript aus</span><span class="sxs-lookup"><span data-stu-id="b163d-134">To run a script</span></span>
<span data-ttu-id="b163d-135">Klicken Sie auf der Symbolleiste auf **Skript ausführen**, oder klicken Sie im Menü **Datei** auf **Ausführen**.</span><span class="sxs-lookup"><span data-stu-id="b163d-135">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="b163d-136">So führen Sie einen Abschnitt eines Skripts aus</span><span class="sxs-lookup"><span data-stu-id="b163d-136">To run a portion of a script</span></span>

1.  <span data-ttu-id="b163d-137">Wählen Sie Skriptbereich einen Abschnitt eines Skripts aus.</span><span class="sxs-lookup"><span data-stu-id="b163d-137">In the Script Pane, select a portion of a script.</span></span>

2.  <span data-ttu-id="b163d-138">Klicken Sie im Menü **Datei** auf **Auswahl ausführen**, oder klicken Sie auf der Symbolleiste auf **Auswahl ausführen**.</span><span class="sxs-lookup"><span data-stu-id="b163d-138">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="b163d-139">So beenden Sie ein Skript, das ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="b163d-139">To stop a running script</span></span>
<span data-ttu-id="b163d-140">Klicken Sie auf der Symbolleiste auf **Vorgang beenden**, drücken Sie STRG+UNTBR, oder klicken Sie im Menü **Datei** auf **Vorgang beenden**.</span><span class="sxs-lookup"><span data-stu-id="b163d-140">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="b163d-141">Drücken von **STRG+C** funktioniert ebenfalls, sofern aktuell kein Text ausgewählt ist. Ist dies der Fall, wird **STRG+C** der Kopierfunktion für den ausgewählten Text zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="b163d-141">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <span data-ttu-id="b163d-142"><a name="bkmk_2"></a>Schreiben und Bearbeiten von Text im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="b163d-142"><a name="bkmk_2"></a>How to write and edit text in the Script Pane</span></span>
<span data-ttu-id="b163d-143">Führen Sie die folgenden Schritte aus, um Text im Skriptbereich zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="b163d-143">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="b163d-144">Sie können Text kopieren, ausschneiden, einfügen, suchen und ersetzen.</span><span class="sxs-lookup"><span data-stu-id="b163d-144">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="b163d-145">Sie können außerdem die letzte von Ihnen ausgeführte Aktion rückgängig machen und wiederholen.</span><span class="sxs-lookup"><span data-stu-id="b163d-145">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="b163d-146">Die Tastenkombinationen zum Ausführen dieser Aktionen sind mit denen identisch, die für alle Windows-Anwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b163d-146">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="b163d-147">So geben Sie Text im Skriptbereich ein</span><span class="sxs-lookup"><span data-stu-id="b163d-147">To enter text in the Script Pane</span></span>

1.  <span data-ttu-id="b163d-148">Bewegen Sie den Cursor in den Skriptbereich, indem Sie auf eine beliebige Stelle im Skriptbereich oder im Menü **Ansicht** auf **Zum Skriptbereich gehen** klicken.</span><span class="sxs-lookup"><span data-stu-id="b163d-148">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2.  <span data-ttu-id="b163d-149">Erstellen Sie ein Skript.</span><span class="sxs-lookup"><span data-stu-id="b163d-149">Create a script.</span></span> <span data-ttu-id="b163d-150">Farbliche Syntaxkennzeichnung und Vervollständigung mit der TAB-TASTE vereinfachen dies erheblich in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b163d-150">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3.  <span data-ttu-id="b163d-151">Ausführliche Informationen dazu, wie das Nutzen der Funktion Vervollständigung mit der TAB-TASTE beim Eingeben helfen kann, finden Sie unter [Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).</span><span class="sxs-lookup"><span data-stu-id="b163d-151">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="b163d-152">So suchen Sie nach Text im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="b163d-152">To find text in the Script Pane</span></span>

1.  <span data-ttu-id="b163d-153">Drücken Sie **STRG+F**, oder klicken Sie im Menü **Bearbeiten** auf **Im Skript suchen**, um nach Text an einer beliebigen Stelle zu suchen.</span><span class="sxs-lookup"><span data-stu-id="b163d-153">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2.  <span data-ttu-id="b163d-154">Um nach Text ab dem Cursor zu suchen, drücken Sie **F3**, oder klicken Sie im Menü **Bearbeiten** auf **Im Skript weitersuchen**.</span><span class="sxs-lookup"><span data-stu-id="b163d-154">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3.  <span data-ttu-id="b163d-155">Drücken Sie **UMSCHALT+F3**, oder klicken Sie im Menü **Bearbeiten** auf **Vorheriges im Skript suchen**, um nach Text vor dem Cursor zu suchen.</span><span class="sxs-lookup"><span data-stu-id="b163d-155">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="b163d-156">So finden und ersetzen Sie Text im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="b163d-156">To find and replace text in the Script Pane</span></span>
<span data-ttu-id="b163d-157">Drücken Sie **STRG+H**, oder klicken Sie im Menü **Bearbeiten** auf **Im Skript ersetzen**.</span><span class="sxs-lookup"><span data-stu-id="b163d-157">Press **CRTL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="b163d-158">Geben Sie sowohl den zu suchenden Text und auch den Text ein, durch den der zu suchende Text ersetzt werden soll, und drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="b163d-158">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="b163d-159">So wechseln Sie zu einer bestimmten Zeile des Texts im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="b163d-159">To go to a particular line of text in the Script Pane</span></span>

1.  <span data-ttu-id="b163d-160">Drücken Sie im Skriptbereich die Tastenkombination **STRG+G**, oder klicken Sie im Menü **Bearbeiten** auf **Gehe zu Zeile**.</span><span class="sxs-lookup"><span data-stu-id="b163d-160">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2.  <span data-ttu-id="b163d-161">Geben Sie eine Zeilennummer ein.</span><span class="sxs-lookup"><span data-stu-id="b163d-161">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="b163d-162">So kopieren Sie Text in den Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="b163d-162">To copy text in the Script Pane</span></span>

1.  <span data-ttu-id="b163d-163">Wählen Sie im Skriptbereich den Text aus, den Sie kopieren möchten.</span><span class="sxs-lookup"><span data-stu-id="b163d-163">In the Script Pane, select the text that you want to copy.</span></span>

2.  <span data-ttu-id="b163d-164">Drücken Sie **STRG+C**, klicken Sie auf der Symbolleiste auf das Symbol **Kopieren**, oder klicken Sie im Menü **Bearbeiten** auf **Kopieren**.</span><span class="sxs-lookup"><span data-stu-id="b163d-164">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="b163d-165">So schneiden Sie Text im Skriptbereich aus</span><span class="sxs-lookup"><span data-stu-id="b163d-165">To cut text in the Script Pane</span></span>

1.  <span data-ttu-id="b163d-166">Wählen Sie im Skriptbereich den Text aus, den Sie ausschneiden möchten.</span><span class="sxs-lookup"><span data-stu-id="b163d-166">In the Script Pane, select the text that you want to cut.</span></span>

2.  <span data-ttu-id="b163d-167">Drücken Sie **STRG+X**, oder klicken Sie auf der Symbolleiste auf das Symbol **Ausschneiden**, oder klicken Sie im Menü **Bearbeiten** auf **Ausschneiden**.</span><span class="sxs-lookup"><span data-stu-id="b163d-167">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="b163d-168">So fügen Sie Text in den Skriptbereich ein</span><span class="sxs-lookup"><span data-stu-id="b163d-168">To paste text into the Script Pane</span></span>
<span data-ttu-id="b163d-169">Drücken Sie **STRG+V**, oder klicken Sie auf der Symbolleiste auf das Symbol **Einfügen**, oder klicken Sie im Menü **Bearbeiten** auf **Einfügen**.</span><span class="sxs-lookup"><span data-stu-id="b163d-169">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="b163d-170">So machen Sie eine Aktion im Skriptbereich rückgängig</span><span class="sxs-lookup"><span data-stu-id="b163d-170">To undo an action in the Script Pane</span></span>
<span data-ttu-id="b163d-171">Drücken Sie **STRG+Z**, oder klicken Sie auf der Symbolleiste auf das Symbol **Rückgängig**, oder klicken Sie im Menü **Bearbeiten** auf **Rückgängig**.</span><span class="sxs-lookup"><span data-stu-id="b163d-171">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="b163d-172">So wiederholen Sie eine Aktion im Skriptbereich</span><span class="sxs-lookup"><span data-stu-id="b163d-172">To redo an action in the Script Pane</span></span>
<span data-ttu-id="b163d-173">Drücken Sie **STRG+Y**, oder klicken Sie auf der Symbolleiste auf das Symbol **Wiederholen**, oder klicken Sie im Menü **Bearbeiten** auf **Wiederholen**.</span><span class="sxs-lookup"><span data-stu-id="b163d-173">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <span data-ttu-id="b163d-174"><a name="bkmk_3"></a>Speichern eines Skripts</span><span class="sxs-lookup"><span data-stu-id="b163d-174"><a name="bkmk_3"></a>How to save a script</span></span>
<span data-ttu-id="b163d-175">Gehen Sie folgendermaßen vor, um einem Skript einen Namen zu geben und es zu speichern.</span><span class="sxs-lookup"><span data-stu-id="b163d-175">Use the following steps to save and name a script.</span></span> <span data-ttu-id="b163d-176">Ein Sternchen wird neben dem Skriptnamen angezeigt, um zu kennzeichnen, dass die Datei nicht gespeichert wurde, seit sie geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="b163d-176">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="b163d-177">Das Sternchen verschwindet, wenn die Datei gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="b163d-177">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="b163d-178">So speichern Sie ein Skript</span><span class="sxs-lookup"><span data-stu-id="b163d-178">To save a script</span></span>
<span data-ttu-id="b163d-179">Drücken Sie **STRG+S**, oder klicken Sie auf der Symbolleiste auf das Symbol **Speichern**, oder klicken Sie im Menü **Datei** auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="b163d-179">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="b163d-180">So geben Sie einem Skript einen Namen und speichern es</span><span class="sxs-lookup"><span data-stu-id="b163d-180">To save and name a script</span></span>

1.  <span data-ttu-id="b163d-181">Klicken Sie im Menü **Datei** auf **Speichern unter**.</span><span class="sxs-lookup"><span data-stu-id="b163d-181">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="b163d-182">Das Dialogfeld **Speichern unter** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b163d-182">The **Save As** dialog box will appear.</span></span>

2.  <span data-ttu-id="b163d-183">Geben Sie in das Feld **Dateiname** einen Namen für die Datei ein.</span><span class="sxs-lookup"><span data-stu-id="b163d-183">In the **File name** box, enter a name for the file.</span></span>

3.  <span data-ttu-id="b163d-184">Wählen Sie im Feld **Dateityp** einen Dateityp aus.</span><span class="sxs-lookup"><span data-stu-id="b163d-184">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="b163d-185">Wählen Sie beispielsweise im Feld **Dateityp** den Typ „PowerShell-Skripte (\* .ps1)“ aus.</span><span class="sxs-lookup"><span data-stu-id="b163d-185">For example, in the **Save as type** box, select “PowerShell Scripts (\* .ps1)”.</span></span>

4.  <span data-ttu-id="b163d-186">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="b163d-186">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="b163d-187">So speichern Sie ein Skript in ASCII-Codierung</span><span class="sxs-lookup"><span data-stu-id="b163d-187">To save a script in ASCII encoding</span></span>
<span data-ttu-id="b163d-188">Windows PowerShell ISE speichert neue Skriptdateien (.ps1), Skriptdatendateien (.psd1) und Skriptmoduldateien (.psm1) standardmäßig im Unicode-Format (BigEndianUnicode).</span><span class="sxs-lookup"><span data-stu-id="b163d-188">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="b163d-189">Um ein Skript in einer anderen Codierung, z. B. ASCII (ANSI), zu speichern, verwenden Sie die **Save**- oder **SaveAs**-Methode des [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="b163d-189">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="b163d-190">Im folgenden Befehl wird ein neues Skript als „MyScript.ps1“ mit ASCII-Codierung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="b163d-190">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```
$psise.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="b163d-191">Im folgenden Befehl wird die aktuelle Skriptdatei durch eine Datei ersetzt, die denselben Namen hat, aber in ASCII-Codierung vorliegt.</span><span class="sxs-lookup"><span data-stu-id="b163d-191">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```
$psise.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="b163d-192">Im folgenden Befehl wird die Codierung der aktuellen Datei abgerufen.</span><span class="sxs-lookup"><span data-stu-id="b163d-192">The following command gets the encoding of the current file.</span></span>

```
$psise.CurrentFile.encoding
```

<span data-ttu-id="b163d-193">Windows PowerShell ISE unterstützt die folgenden Codierungsoptionen: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 und Default.</span><span class="sxs-lookup"><span data-stu-id="b163d-193">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="b163d-194">Der Wert der Option „Default“ ist je nach System unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="b163d-194">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="b163d-195">Windows PowerShell ISE ändert nicht die Codierung von Skripts, die in anderen Editoren erstellt wurden. Dies gilt selbst dann, wenn Sie den Befehl „Speichern“ oder „Speichern unter“ in Windows PowerShell ISE verwenden.</span><span class="sxs-lookup"><span data-stu-id="b163d-195">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="b163d-196">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b163d-196">See Also</span></span>
- [<span data-ttu-id="b163d-197">Verwenden der Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b163d-197">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

