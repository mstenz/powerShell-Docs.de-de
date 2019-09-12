---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: Neuigkeiten bei PowerShell 5.0 ISE
ms.openlocfilehash: a719baef0da1600f0a5377e1b72c81b67e37eef2
ms.sourcegitcommit: a74ae7ed089301992fed201fbe55d827a622afa0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2019
ms.locfileid: "70746223"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="8b25f-103">Neuigkeiten bei Windows PowerShell 5.0 ISE</span><span class="sxs-lookup"><span data-stu-id="8b25f-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="8b25f-104">In diesem Thema werden die neuen und aktualisierten Features vorgestellt, die in Versionen von Windows PowerShell Integrated Scripting Environment (ISE) eingeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="8b25f-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="8b25f-105">Featurebeschreibung</span><span class="sxs-lookup"><span data-stu-id="8b25f-105">Feature description</span></span>

<span data-ttu-id="8b25f-106">Die Windows PowerShell ISE ist eine Hostanwendung, die es Ihnen ermöglicht, Skripts und Module in einer grafischen und intuitiven Umgebung zu schreiben, auszuführen und zu testen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="8b25f-107">Wichtige Features wie farbliche Syntaxkennzeichnung, Vervollständigung mit der TAB-Taste, visuelles Debuggen, Unicode-Kompatibilität und kontextbezogene Hilfe ermöglichen eine komfortable Skripterstellung.</span><span class="sxs-lookup"><span data-stu-id="8b25f-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="8b25f-108">Weitere Informationen finden Sie unter [Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="8b25f-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="8b25f-109">Die folgende Tabelle enthält die neuen und geänderten Funktionen für diese Version von Windows PowerShell ISE in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b25f-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="8b25f-110">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="8b25f-110">IntelliSense</span></span>

> <span data-ttu-id="8b25f-111">In ISE 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-111">Added in ISE 3.0</span></span>

<span data-ttu-id="8b25f-112">IntelliSense ist ein Feature für die automatische Vervollständigung, das zur Windows PowerShell ISE gehört.</span><span class="sxs-lookup"><span data-stu-id="8b25f-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="8b25f-113">IntelliSense zeigt während der Eingabe klickbare Menüs möglicherweise übereinstimmender Cmdlets, Parameter, Parameterwerte, Dateien oder Ordner an.</span><span class="sxs-lookup"><span data-stu-id="8b25f-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="8b25f-114">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-114">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-115">Durch Hinzufügen von IntelliSense ist es einfacher, Cmdlets und Syntax zu ermitteln, wenn Sie die Windows PowerShell ISE zum Erstellen von Skripts nutzen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="8b25f-116">Sie können mithilfe von Windows PowerShell ISE auch Windows PowerShell erlernen, während Sie neue Skripts erstellen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="8b25f-117">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-117">**What works differently?**</span></span>

<span data-ttu-id="8b25f-118">Bei Eingabe von Cmdlets in die Windows PowerShell ISE wird ein scrollfähiges und klickbares Menü angezeigt, das Ihnen das Durchsuchen und Auswählen der entsprechenden Befehle ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="8b25f-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="8b25f-119">Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="8b25f-119">Snippets</span></span>

> <span data-ttu-id="8b25f-120">In ISE 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-120">Added in ISE 3.0</span></span>

<span data-ttu-id="8b25f-121">*Codeausschnitte* sind kurze Abschnitte von Windows PowerShell-Code, die Sie in die in Windows PowerShell ISE erstellten Skripts einfügen können.</span><span class="sxs-lookup"><span data-stu-id="8b25f-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="8b25f-122">Windows PowerShell ISE bietet einen Standardsatz von Codeausschnitten.</span><span class="sxs-lookup"><span data-stu-id="8b25f-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="8b25f-123">Beim Arbeiten in der Windows PowerShell ISE können Sie Codeausschnitte mithilfe des Cmdlets `New-Snippet` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="8b25f-124">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-124">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-125">Mithilfe von Codeausschnitten können Sie Skripts zum Automatisieren Ihrer Umgebung schnell zusammenstellen und erstellen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="8b25f-126">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-126">**What works differently?**</span></span>

<span data-ttu-id="8b25f-127">Klicken Sie zum Verwenden von Codeausschnitten in Windows PowerShell 3.0 oder höher im Menü **Bearbeiten** auf **Codeausschnitte starten**, oder drücken Sie <kbd>STRG</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8b25f-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="8b25f-128">Add-On-Tools</span><span class="sxs-lookup"><span data-stu-id="8b25f-128">Add-on tools</span></span>

> <span data-ttu-id="8b25f-129">In PowerShell 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8b25f-130">Windows PowerShell ISE unterstützt jetzt Add-On-Tools, die das Objektmodell verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b25f-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="8b25f-131">Diese Add-Ons sind Windows Presentation Foundation-Steuerelemente (WPF), die in der Konsole als vertikaler oder horizontaler Bereich angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8b25f-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="8b25f-132">Mehrere Add-On-Tools in einem Bereich werden als Registerkarten-Steuerelement angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b25f-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="8b25f-133">Sie können auch Add-On-Tools von anderen Anbietern als Microsoft hinzufügen oder entfernen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="8b25f-134">Weitere Informationen finden Sie unter [Zweck des Windows PowerShell ISE-Skriptobjektmodells](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="8b25f-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="8b25f-135">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-135">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-136">Add-Ons ermöglichen Ihnen das Erweitern und Anpassen der Windows PowerShell ISE mit Tools, die die Funktionalität erweitern und Ihre Skripterstellungsumgebung verbessern.</span><span class="sxs-lookup"><span data-stu-id="8b25f-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="8b25f-137">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-137">**What works differently?**</span></span>

<span data-ttu-id="8b25f-138">Zum Funktionsumfang der Windows PowerShell ISE 3.0 und höher gehört das Add-On **Befehle**.</span><span class="sxs-lookup"><span data-stu-id="8b25f-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="8b25f-139">Das Add-On **Befehle** ermöglicht das Durchsuchen von Cmdlets und das Zugreifen auf die Hilfe zu den Cmdlets. Es wird neben den Bereichen **Skript** und **Konsole** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b25f-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="8b25f-140">Zusätzliche Add-Ons finden Sie über den Befehl **Website mit Add-On-Tools öffnen** im Menü**Add-Ons**.</span><span class="sxs-lookup"><span data-stu-id="8b25f-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="8b25f-141">Neustart-Manager und automatisches Speichern</span><span class="sxs-lookup"><span data-stu-id="8b25f-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="8b25f-142">In PowerShell 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8b25f-143">Windows PowerShell ISE speichert nun Ihre geöffneten Skripts automatisch alle zwei Minuten an einem gesonderten Speicherort.</span><span class="sxs-lookup"><span data-stu-id="8b25f-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="8b25f-144">Wenn Windows PowerShell ISE nach einem unerwarteten Absturz oder geplant neu startet, werden die in der letzten Sitzung geöffneten Skripts auch dann wiederhergestellt, wenn die Skripts nicht gespeichert wurden.</span><span class="sxs-lookup"><span data-stu-id="8b25f-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="8b25f-145">Führen Sie im Konsolenbereich den folgenden Befehl aus, um das Intervall für die automatische Speicherung zu ändern: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="8b25f-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="8b25f-146">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-146">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-147">Sie können jetzt mit Windows PowerShell ISE mit dem Wissen arbeiten, dass Ihre geöffneten Skripts automatisch gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="8b25f-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="8b25f-148">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-148">**What works differently?**</span></span>

<span data-ttu-id="8b25f-149">In Windows PowerShell ISE 2.0 werden die Skripts nicht automatisch gespeichert.</span><span class="sxs-lookup"><span data-stu-id="8b25f-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="8b25f-150">Liste „Zuletzt verwendet“</span><span class="sxs-lookup"><span data-stu-id="8b25f-150">Most-recently used list</span></span>

> <span data-ttu-id="8b25f-151">In PowerShell 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8b25f-152">Die Windows PowerShell ISE bietet jetzt eine Liste der zuletzt verwendeten Dateien.</span><span class="sxs-lookup"><span data-stu-id="8b25f-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="8b25f-153">Beim Öffnen einer Datei in der Windows PowerShell ISE wird die Datei der Liste „Zuletzt verwendet“ im Menü **Datei** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8b25f-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="8b25f-154">Führen Sie im Konsolenbereich den folgenden Befehl aus, um die Standardanzahl von Dateien in der Liste „Zuletzt verwendet“ zu ändern: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="8b25f-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="8b25f-155">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-155">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-156">Über die Liste „Zuletzt verwendet“ können Sie nun mühelos auf die zuletzt verwendeten Dateien zugreifen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="8b25f-157">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-157">**What works differently?**</span></span>

<span data-ttu-id="8b25f-158">Die Windows PowerShell ISE 2.0 bietet keine solche Liste.</span><span class="sxs-lookup"><span data-stu-id="8b25f-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="8b25f-159">Konsolenbereich</span><span class="sxs-lookup"><span data-stu-id="8b25f-159">Console Pane</span></span>

> <span data-ttu-id="8b25f-160">In PowerShell 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8b25f-161">Die separaten Befehls- und Ausgabebereiche, die in der ersten Version der Windows PowerShell ISE verfügbar waren, wurden in einem Konsolenbereich kombiniert.</span><span class="sxs-lookup"><span data-stu-id="8b25f-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="8b25f-162">Von der Funktion und Darstellung ähnelt der Konsolenbereich einer typischen Windows PowerShell-Konsole, er bietet aber die im Folgenden aufgeführten Erweiterungen:</span><span class="sxs-lookup"><span data-stu-id="8b25f-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="8b25f-163">Syntaxfarben für Eingabetext (nicht für Ausgabetext), einschließlich XML-Syntax</span><span class="sxs-lookup"><span data-stu-id="8b25f-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="8b25f-164">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="8b25f-164">IntelliSense</span></span>
- <span data-ttu-id="8b25f-165">Zugehörige Klammer</span><span class="sxs-lookup"><span data-stu-id="8b25f-165">Brace matching</span></span>
- <span data-ttu-id="8b25f-166">Fehleranzeige</span><span class="sxs-lookup"><span data-stu-id="8b25f-166">Error indication</span></span>
- <span data-ttu-id="8b25f-167">Vollständige Unicode-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="8b25f-167">Full Unicode support</span></span>
- <span data-ttu-id="8b25f-168">Kontextbezogene Hilfe über <kbd>F1</kbd></span><span class="sxs-lookup"><span data-stu-id="8b25f-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="8b25f-169">Kontextbezogene Befehlsanzeige (Show-Command) über <kbd>STRG</kbd>+<kbd>F1</kbd></span><span class="sxs-lookup"><span data-stu-id="8b25f-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="8b25f-170">Unterstützung für komplexe Skripts und Sprachen mit Leserichtung von rechts nach links</span><span class="sxs-lookup"><span data-stu-id="8b25f-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="8b25f-171">Schriftartenunterstützung</span><span class="sxs-lookup"><span data-stu-id="8b25f-171">Font support</span></span>
- <span data-ttu-id="8b25f-172">Zoom</span><span class="sxs-lookup"><span data-stu-id="8b25f-172">Zoom</span></span>
- <span data-ttu-id="8b25f-173">Modi für Linien- und Blockauswahl</span><span class="sxs-lookup"><span data-stu-id="8b25f-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="8b25f-174">Beibehaltung von über die Befehlszeile eingegebenem Inhalt, wenn Sie mithilfe der <kbd>NACH-OBEN-TASTE</kbd> den Verlauf in der Konsole anzeigen</span><span class="sxs-lookup"><span data-stu-id="8b25f-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="8b25f-175">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-175">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-176">Diese Änderungen im Konsolenbereich ermöglichen eine Skripterstellungsumgebung, die mit der Konsolenschnittstelle konsistenter ist.</span><span class="sxs-lookup"><span data-stu-id="8b25f-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="8b25f-177">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-177">**What works differently?**</span></span>

<span data-ttu-id="8b25f-178">Die Windows PowerShell ISE 2.0 verfügt über getrennte Befehls- und Ausgabebereiche.</span><span class="sxs-lookup"><span data-stu-id="8b25f-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="8b25f-179">Befehlszeilenschalter</span><span class="sxs-lookup"><span data-stu-id="8b25f-179">Command-line switches</span></span>

> <span data-ttu-id="8b25f-180">In PowerShell 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8b25f-181">Wenn Sie die Windows PowerShell ISE über die Befehlszeile starten (indem Sie **powershell_ise.exe** eingeben), können Sie die folgenden neuen Befehlszeilenschalter hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="8b25f-182">`-NoProfile`: Startet die Windows PowerShell ISE ohne Ausführung von `$profile`</span><span class="sxs-lookup"><span data-stu-id="8b25f-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="8b25f-183">`-Help`: Zeigt ein Hilfefenster an.</span><span class="sxs-lookup"><span data-stu-id="8b25f-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="8b25f-184">`-mta`: Startet die Windows PowerShell ISE im Multithread-Apartment-Modus</span><span class="sxs-lookup"><span data-stu-id="8b25f-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="8b25f-185">Der Standardbetriebsmodus der Windows PowerShell ISE ist der Singlethread-Apartment-Modus bzw. `-sta`.</span><span class="sxs-lookup"><span data-stu-id="8b25f-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="8b25f-186">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-186">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-187">Das Hinzufügen dieser Befehlszeilenschalter ermöglicht Ihnen das Steuern der Umgebung, in der die Windows PowerShell ISE ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8b25f-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="8b25f-188">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-188">**What works differently?**</span></span>

<span data-ttu-id="8b25f-189">Die Windows PowerShell ISE 2.0 erkennt diese Befehlszeilenschalter nicht.</span><span class="sxs-lookup"><span data-stu-id="8b25f-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="8b25f-190">Neue Features im Editor</span><span class="sxs-lookup"><span data-stu-id="8b25f-190">New editor features</span></span>

> <span data-ttu-id="8b25f-191">In PowerShell 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8b25f-192">Zu den weiteren Windows PowerShell ISE-Bearbeitungsfeatures zählen:</span><span class="sxs-lookup"><span data-stu-id="8b25f-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="8b25f-193">**XML-Syntaxfarben**: Windows PowerShell ISE versieht die XML-Syntax jetzt ebenso mit Farben wie die Windows PowerShell-Syntax.</span><span class="sxs-lookup"><span data-stu-id="8b25f-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="8b25f-194">**Zugehörige Klammer**: Die Windows PowerShell ISE bietet die Funktion „Zugehörige Klammer (Hervorhebung)“, die wie folgt verwendet werden kann: Wenn Sie z. B. den Befehl **Gehe zu Spiel** bzw. <kbd>STRG</kbd>+<kbd>]</kbd> verwenden, wird die schließende Klammer gefunden, wenn eine öffnende Klammer ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="8b25f-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="8b25f-195">**Gliederungsansicht** Der Skriptbereich unterstützt Gliederungen, sodass Codeabschnitte durch Klicken auf Plus- bzw. Minuszeichen am linken Rand auf- bzw. zugeklappt werden können.</span><span class="sxs-lookup"><span data-stu-id="8b25f-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="8b25f-196">Sie können Klammern bzw. die Tags `#region` und `#endregion` verwenden, um den Anfang bzw. das Ende eines zuklappbaren Abschnitts zu markieren.</span><span class="sxs-lookup"><span data-stu-id="8b25f-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="8b25f-197">Drücken Sie zum Auf- bzw. Zuklappen aller Bereiche <kbd>STRG</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8b25f-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="8b25f-198">**Textbearbeitung mit Drag & Drop**: Windows PowerShell ISE unterstützt nun die Textbearbeitung mit Drag & Drop.</span><span class="sxs-lookup"><span data-stu-id="8b25f-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="8b25f-199">Sie können einen beliebigen Textblock auswählen und an eine andere Stelle im Editor oder in der Konsole ziehen, um den Text zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="8b25f-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="8b25f-200">Wenn Sie die <kbd>STRG</kbd>-Taste gedrückt halten, während Sie den markierten Text ziehen, wird der Text, sobald Sie die Maustaste loslassen, an den neuen Ort kopiert.</span><span class="sxs-lookup"><span data-stu-id="8b25f-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="8b25f-201">In dieser Version von Windows PowerShell ISE wird beim Ziehen und Ablegen von Dateien auf Windows PowerShell ISE die Datei von Windows PowerShell ISE geöffnet.</span><span class="sxs-lookup"><span data-stu-id="8b25f-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="8b25f-202">**Anzeige von Analysefehlern**: Analysefehler werden rot unterstrichen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b25f-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="8b25f-203">Wenn Sie auf einen Fehler zeigen, wird das im Code gefundene Problem als QuickInfo angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8b25f-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="8b25f-204">**Zoom**: Der Zoomprozentsatz des Konsoleninhalts kann mit einem Zoomschieberegler (rechts unten im Fenster der Windows PowerShell ISE) oder durch Eingabe des Befehls `$psise.options.Zoom` im Konsolenbereich festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="8b25f-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="8b25f-205">**Umfassende Funktionen zum Kopieren und Einfügen von Text**: Beim Kopieren in die Zwischenablage in Windows PowerShell ISE bleiben Informationen zur Schriftart, Größe und Farbe der ursprünglichen Auswahl erhalten.</span><span class="sxs-lookup"><span data-stu-id="8b25f-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="8b25f-206">**Blockauswahl**: Sie können einen Textblock auswählen, indem Sie bei gedrückter <kbd>ALT</kbd>-TASTE den Text im Skriptbereich mit der Maus auswählen, oder indem Sie <kbd>ALT</kbd>+<kbd>UMSCHALT</kbd>+<kbd>NACH-OBEN/NACH-UNTEN</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="8b25f-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="8b25f-207">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-207">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-208">Die zusätzlichen Bearbeitungsfeatures bieten eine konsistentere und leistungsstärkere Bearbeitungsumgebung.</span><span class="sxs-lookup"><span data-stu-id="8b25f-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="8b25f-209">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-209">**What works differently?**</span></span>

<span data-ttu-id="8b25f-210">In Windows PowerShell ISE 2.0 waren diese Bearbeitungsoptimierungen nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="8b25f-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="8b25f-211">Neues Anzeigefenster für Hilfe</span><span class="sxs-lookup"><span data-stu-id="8b25f-211">New Help viewer window</span></span>

> <span data-ttu-id="8b25f-212">In PowerShell 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8b25f-213">Wenn Sie <kbd>F1</kbd> drücken, während sich der Cursor in einem Cmdlet befindet oder Sie einen Teil eines Cmdlets hervorgehoben haben, wird im neuen Anzeigefenster für Hilfe eine kontextbezogene Hilfe zum hervorgehobenen Cmdlet geöffnet.</span><span class="sxs-lookup"><span data-stu-id="8b25f-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="8b25f-214">Um die **konzeptionelle Hilfe** für Windows PowerShell ISE anzuzeigen, geben Sie im Konsolenbereich `operators` ein, und drücken Sie dann <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8b25f-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="8b25f-215">Laden Sie die aktuelle Version der Windows PowerShell-Hilfethemen von der Microsoft-Website herunter, bevor Sie dieses Feature verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b25f-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="8b25f-216">Die einfachste Methode zum Herunterladen der Hilfethemen ist die Ausführung des Cmdlets `Update-Help` im Konsolenbereich, wenn Sie die Windows PowerShell ISE als Administrator ausführen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="8b25f-217">Sie können ändern, wo über die Taste <kbd>F1</kbd> nach Hilfe gesucht wird.</span><span class="sxs-lookup"><span data-stu-id="8b25f-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="8b25f-218">Im Menü **Extras**/**Optionen** können Sie auf der Registerkarte **Allgemeine Einstellungen** unter **Andere Einstellungen** das Kontrollkästchen **Lokale Hilfe anstatt Onlineinhalt verwenden** aktivieren bzw. deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="8b25f-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="8b25f-219">Wenn aktiviert, sucht der Client die Cmdlet-Hilfe in der heruntergeladenen Hilfe im Ordner „modules“.</span><span class="sxs-lookup"><span data-stu-id="8b25f-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="8b25f-220">Wenn das Kontrollkästchen deaktiviert ist, sucht der Client online nach der Hilfe.</span><span class="sxs-lookup"><span data-stu-id="8b25f-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="8b25f-221">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-221">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-222">Durch eine kontextbezogene Hilfe ohne Verlassen des aktuellen Cmdlets oder Skripts machen Sie eine integrierte Lernerfahrung.</span><span class="sxs-lookup"><span data-stu-id="8b25f-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="8b25f-223">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-223">**What works differently?**</span></span>

<span data-ttu-id="8b25f-224">Durch Drücken von <kbd>F1</kbd> in früheren Versionen von Windows PowerShell ISE wurde die Hilfedatei auf dem lokalen Computer geöffnet.</span><span class="sxs-lookup"><span data-stu-id="8b25f-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="8b25f-225">In Windows PowerShell ISE 3.0 und höher wird ein Fenster geöffnet, das die Hilfe für das Cmdlet enthält, die durchsuchbar und konfigurierbar ist.</span><span class="sxs-lookup"><span data-stu-id="8b25f-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="8b25f-226">Diese Hilfe ist in Windows PowerShell ISE 3.0 neu. Die aktualisierbare Hilfe ist in Windows PowerShell 3.0 neu.</span><span class="sxs-lookup"><span data-stu-id="8b25f-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="8b25f-227">Cmdlet „Show-Command“</span><span class="sxs-lookup"><span data-stu-id="8b25f-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="8b25f-228">In PowerShell 3.0 hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="8b25f-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8b25f-229">Das Cmdlet `Show-Command` ermöglicht das Erstellen und Ausführen eines Cmdlets oder einer Funktion, indem ein grafisches Formular ausgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="8b25f-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="8b25f-230">Das Formular ermöglicht Benutzern das Arbeiten mit Windows PowerShell in einer grafischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="8b25f-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="8b25f-231">Mit `Show-Command` können erfahrene Skriptentwickler schnell eine Windows PowerShell-basierte grafische Benutzeroberfläche (GUI) erstellen.</span><span class="sxs-lookup"><span data-stu-id="8b25f-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="8b25f-232">**Welchen Nutzen bietet diese Änderung?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-232">**What value does this change add?**</span></span>

<span data-ttu-id="8b25f-233">Durch das Verwenden von `Show-Command` in Ihren Windows PowerShell-Skripts können Sie Ihren Benutzern die grafische Umgebung bereitstellen, mit der sie vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="8b25f-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="8b25f-234">`Show-Command` hilft darüber hinaus Einsteigern beim Erlernen von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b25f-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="8b25f-235">**Worin bestehen die Unterschiede?**</span><span class="sxs-lookup"><span data-stu-id="8b25f-235">**What works differently?**</span></span>

<span data-ttu-id="8b25f-236">`Show-Command` ist neu in Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="8b25f-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b25f-237">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8b25f-237">See also</span></span>

<span data-ttu-id="8b25f-238">Weitere Informationen über die Verwendung von Windows PowerShell ISE finden Sie unter [Kennenlernen der Windows PowerShell ISE](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="8b25f-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../getting-started/fundamental/exploring-the-windows-powershell-ise.md).</span></span>
