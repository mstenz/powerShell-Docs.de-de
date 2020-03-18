---
title: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
description: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279248"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="1b7b5-103">Replizieren der ISE-Benutzeroberfläche in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b7b5-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="1b7b5-104">Obwohl die PowerShell-Erweiterung für VSCode keine vollständige Funktionsparität mit der PowerShell ISE anstrebt, gibt es Funktionen, die die VSCode-Benutzeroberfläche für Benutzer der ISE natürlicher gestalten.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="1b7b5-105">Dieses Dokument versucht, Einstellungen aufzulisten, die Sie in VSCode konfigurieren können, um die Benutzerfreundlichkeit im Vergleich zur ISE etwas vertrauter zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="1b7b5-106">ISE-Modus</span><span class="sxs-lookup"><span data-stu-id="1b7b5-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="1b7b5-107">Dieses Feature ist in der PowerShell Preview-Erweiterung seit Version 2019.12.0 und in der PowerShell-Erweiterung seit Version 2020.3.0 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="1b7b5-108">Die einfachste Möglichkeit zum Replizieren der ISE-Benutzeroberfläche in Visual Studio Code ist das Aktivieren des ISE-Modus.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="1b7b5-109">Öffnen Sie hierzu die Befehlspalette (<kbd>F1</kbd> oder <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> oder <kbd>BEFEHLSTASTE</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> unter macOS), und geben Sie „ISE-Modus“ ein.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-109">To do this, open the command pallet (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span>
<span data-ttu-id="1b7b5-110">Wählen Sie in der Liste „PowerShell: ISE-Modus aktivieren“ aus.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="1b7b5-111">Dieser Befehl wendet einen Großteil der in diesem Dokument beschriebenen Einstellungen automatisch an.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-111">This command will apply a lot of the settings found in this document automatically.</span></span>
<span data-ttu-id="1b7b5-112">Das Ergebnis sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-112">The result looks like this:</span></span>

![ISE-Modus](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

<span data-ttu-id="1b7b5-114">Der Rest dieses Artikels enthält detailliertere Informationen zu den Einstellungen im ISE-Modus und einigen zusätzlichen Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-114">The rest of this article includes more detailed information on settings in ISE Mode and some additional settings.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="1b7b5-115">Schlüsselbindungen</span><span class="sxs-lookup"><span data-stu-id="1b7b5-115">Key bindings</span></span>

| <span data-ttu-id="1b7b5-116">Funktion</span><span class="sxs-lookup"><span data-stu-id="1b7b5-116">Function</span></span>                              | <span data-ttu-id="1b7b5-117">ISE-Bindung</span><span class="sxs-lookup"><span data-stu-id="1b7b5-117">ISE Binding</span></span>                  | <span data-ttu-id="1b7b5-118">VSCode-Bindung</span><span class="sxs-lookup"><span data-stu-id="1b7b5-118">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="1b7b5-119">Unterbrechen und Pausieren des Debuggers</span><span class="sxs-lookup"><span data-stu-id="1b7b5-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="1b7b5-120"><kbd>STRG</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="1b7b5-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="1b7b5-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="1b7b5-121"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="1b7b5-122">Ausführen der aktuellen Zeile/des hervorgehobenen Texts</span><span class="sxs-lookup"><span data-stu-id="1b7b5-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="1b7b5-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="1b7b5-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="1b7b5-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="1b7b5-124"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="1b7b5-125">Auflisten verfügbarer Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="1b7b5-125">List available snippets</span></span>               | <span data-ttu-id="1b7b5-126"><kbd>STRG</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="1b7b5-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="1b7b5-127"><kbd>STRG</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="1b7b5-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="1b7b5-128">Benutzerdefinierte Schlüsselbindungen</span><span class="sxs-lookup"><span data-stu-id="1b7b5-128">Custom Key bindings</span></span>

<span data-ttu-id="1b7b5-129">Sie können in Visual Studio Code auch [Ihre eigenen Schlüsselbindungen konfigurieren](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings).</span><span class="sxs-lookup"><span data-stu-id="1b7b5-129">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="1b7b5-130">Vereinfachte, ISE-ähnliche Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="1b7b5-130">Simplified ISE-like UI</span></span>

<span data-ttu-id="1b7b5-131">Wenn Sie nach einer Möglichkeit zur Vereinfachung der Visual Studio Code-Benutzeroberfläche suchen, damit diese der ISE-Benutzeroberfläche ähnelt, wenden Sie diese zwei Einstellungen an:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-131">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> <span data-ttu-id="1b7b5-132">Diese Einstellungen sind im [ISE-Modus](#ise-mode) enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-132">These settings are included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="1b7b5-133">Dies führt zum Ausblenden der Aktivitätsleiste und der Seitenleiste zum Debuggen innerhalb des roten Kastens:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-133">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![Hervorgehobener Abschnitt mit Aktivitätsleiste und der Seitenleiste zum Debuggen](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="1b7b5-135">Das Endergebnis sieht so aus:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-135">The end result looks like this:</span></span>

![Vereinfachte Ansicht von VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="1b7b5-137">Registerkartenvervollständigung</span><span class="sxs-lookup"><span data-stu-id="1b7b5-137">Tab completion</span></span>

<span data-ttu-id="1b7b5-138">Fügen Sie die folgende Einstellung hinzu, um Vervollständigung mit der TAB-TASTE zu erzielen, die der ISE ähnlicher ist:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-138">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="1b7b5-139">Diese Einstellung wurde VSCode direkt (anstatt in der Erweiterung) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-139">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="1b7b5-140">Das Verhalten wird direkt von VSCode bestimmt und kann durch die Erweiterung nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-140">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

> [!NOTE]
> <span data-ttu-id="1b7b5-141">Diese Einstellung ist im [ISE-Modus](#ise-mode) enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-141">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="1b7b5-142">Kein Fokus auf der Konsole beim Ausführen</span><span class="sxs-lookup"><span data-stu-id="1b7b5-142">No focus on console when executing</span></span>

<span data-ttu-id="1b7b5-143">So bleibt der Fokus bei der Ausführung mit <kbd>F8</kbd> im Editor:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-143">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> <span data-ttu-id="1b7b5-144">Diese Einstellung ist im [ISE-Modus](#ise-mode) enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-144">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="1b7b5-145">Der Standardwert lautet aus Gründen der Barrierefreiheit `true`.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-145">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="1b7b5-146">Integrierte Konsole beim Start nicht starten</span><span class="sxs-lookup"><span data-stu-id="1b7b5-146">Don't start integrated console on startup</span></span>

<span data-ttu-id="1b7b5-147">Legen Sie Folgendes fest, um die integrierte Konsole beim Start zu beenden:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-147">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="1b7b5-148">Der PowerShell-Hintergrundprozess wird trotzdem gestartet, da er IntelliSense, Skriptanalyse, Symbolnavigation usw. bereitstellt. Die Konsole wird aber nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-148">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="1b7b5-149">Standardmäßige Annahme, dass es sich um PowerShell-Dateien handelt</span><span class="sxs-lookup"><span data-stu-id="1b7b5-149">Assume files are PowerShell by default</span></span>

<span data-ttu-id="1b7b5-150">Um neue/unbenannte Dateien zu erstellen, registrieren Sie sie standardmäßig als PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-150">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> <span data-ttu-id="1b7b5-151">Diese Einstellung ist im [ISE-Modus](#ise-mode) enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-151">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="color-scheme"></a><span data-ttu-id="1b7b5-152">Farbschema</span><span class="sxs-lookup"><span data-stu-id="1b7b5-152">Color scheme</span></span>

<span data-ttu-id="1b7b5-153">Für VSCode stehen eine Reihe von ISE-Designs zur Verfügung, damit der Editor der ISE wesentlich ähnlicher sieht.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-153">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="1b7b5-154">Geben Sie `theme` in der [Befehlspalette] ein, um `Preferences: Color Theme` abzurufen, und drücken Sie die <kbd>EINGABETASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-154">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="1b7b5-155">Wählen Sie in der Dropdownliste `PowerShell ISE` aus.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-155">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="1b7b5-156">Sie können dieses Design in den Einstellungen wie folgt festlegen:</span><span class="sxs-lookup"><span data-stu-id="1b7b5-156">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> <span data-ttu-id="1b7b5-157">Diese Einstellung ist im [ISE-Modus](#ise-mode) enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-157">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="powershell-command-explorer"></a><span data-ttu-id="1b7b5-158">PowerShell-Befehls-Explorer</span><span class="sxs-lookup"><span data-stu-id="1b7b5-158">PowerShell Command Explorer</span></span>

<span data-ttu-id="1b7b5-159">Dank der Arbeit von [@corbob](https://github.com/corbob) weist die PowerShell-Erweiterung Anfänge eines eigenen Befehls-Explorers auf.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-159">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="1b7b5-160">Geben Sie `PowerShell Command Explorer` in der [Befehlspalette] ein, und drücken Sie die <kbd>EINGABETASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-160">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

> [!NOTE]
> <span data-ttu-id="1b7b5-161">Dies wird im [ISE-Modus](#ise-mode) automatisch angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-161">This is shown automatically in ["ISE Mode"](#ise-mode).</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="1b7b5-162">Öffnen in der ISE</span><span class="sxs-lookup"><span data-stu-id="1b7b5-162">Open in the ISE</span></span>

<span data-ttu-id="1b7b5-163">Wenn Sie letztendlich trotzdem eine Datei in der ISE öffnen möchten, können Sie <kbd>UMSCHALT</kbd>+<kbd>ALT</kbd>+<kbd>P</kbd> verwenden.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-163">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="1b7b5-164">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="1b7b5-164">Other resources</span></span>

- <span data-ttu-id="1b7b5-165">4sysops bietet [einen großartigen Artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) zur Konfiguration von VSCode, um der ISE ähnlicher zu sein.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-165">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="1b7b5-166">Mike F. Robbins hat [einen hervorragenden Beitrag](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) zum Einrichten von VSCode verfasst.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-166">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="1b7b5-167">Learn PowerShell bietet [eine ausgezeichnete Zusammenfassung](https://www.learnpwsh.com/setup-vs-code-for-powershell/) zur Einrichtung von VSCode für PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-167">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="1b7b5-168">Weitere Einstellungen</span><span class="sxs-lookup"><span data-stu-id="1b7b5-168">More settings</span></span>

<span data-ttu-id="1b7b5-169">Wenn Sie weitere Möglichkeiten kennen, wie Sie VSCode für ISE-Anwender vertrauter gestalten können, tragen Sie zu diesem Dokument bei. Wenn Sie nach einer Kompatibilitätskonfiguration suchen, aber keine Möglichkeit finden, diese zu aktivieren, [legen Sie ein Issue an](https://github.com/PowerShell/vscode-powershell/issues/new/choose), und fragen Sie nach einer Lösung!</span><span class="sxs-lookup"><span data-stu-id="1b7b5-169">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="1b7b5-170">Wir freuen uns immer über PRs und Beiträge!</span><span class="sxs-lookup"><span data-stu-id="1b7b5-170">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="1b7b5-171">VSCode-Tipps</span><span class="sxs-lookup"><span data-stu-id="1b7b5-171">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="1b7b5-172">Befehlspalette</span><span class="sxs-lookup"><span data-stu-id="1b7b5-172">Command Palette</span></span>

<span data-ttu-id="1b7b5-173"><kbd>F1</kbd> ODER <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> unter MacOS)</span><span class="sxs-lookup"><span data-stu-id="1b7b5-173"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="1b7b5-174">Eine praktische Möglichkeit zur Ausführung von Befehlen in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1b7b5-174">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="1b7b5-175">Weitere Informationen finden Sie in der [VSCode-Dokumentation](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="1b7b5-175">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Befehlspalette]: #command-palette
[Command Palette]: #command-palette
