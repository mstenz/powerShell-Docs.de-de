---
title: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
description: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058504"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="286cb-103">Replizieren der ISE-Benutzeroberfläche in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="286cb-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="286cb-104">Obwohl die PowerShell-Erweiterung für VSCode keine vollständige Funktionsparität mit der PowerShell ISE anstrebt, gibt es Funktionen, die die VSCode-Benutzeroberfläche für Benutzer der ISE natürlicher gestalten.</span><span class="sxs-lookup"><span data-stu-id="286cb-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="286cb-105">Dieses Dokument versucht, Einstellungen aufzulisten, die Sie in VSCode konfigurieren können, um die Benutzerfreundlichkeit im Vergleich zur ISE etwas vertrauter zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="286cb-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="286cb-106">Schlüsselbindungen</span><span class="sxs-lookup"><span data-stu-id="286cb-106">Key bindings</span></span>

| <span data-ttu-id="286cb-107">Funktion</span><span class="sxs-lookup"><span data-stu-id="286cb-107">Function</span></span>                              | <span data-ttu-id="286cb-108">ISE-Bindung</span><span class="sxs-lookup"><span data-stu-id="286cb-108">ISE Binding</span></span>                  | <span data-ttu-id="286cb-109">VSCode-Bindung</span><span class="sxs-lookup"><span data-stu-id="286cb-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="286cb-110">Unterbrechen und Pausieren des Debuggers</span><span class="sxs-lookup"><span data-stu-id="286cb-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="286cb-111"><kbd>STRG</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="286cb-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="286cb-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="286cb-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="286cb-113">Ausführen der aktuellen Zeile/des hervorgehobenen Texts</span><span class="sxs-lookup"><span data-stu-id="286cb-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="286cb-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="286cb-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="286cb-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="286cb-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="286cb-116">Auflisten verfügbarer Codeausschnitte</span><span class="sxs-lookup"><span data-stu-id="286cb-116">List available snippets</span></span>               | <span data-ttu-id="286cb-117"><kbd>STRG</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="286cb-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="286cb-118"><kbd>STRG</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="286cb-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="286cb-119">Benutzerdefinierte Schlüsselbindungen</span><span class="sxs-lookup"><span data-stu-id="286cb-119">Custom Key bindings</span></span>

<span data-ttu-id="286cb-120">Sie können in Visual Studio Code auch [Ihre eigenen Schlüsselbindungen konfigurieren](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings).</span><span class="sxs-lookup"><span data-stu-id="286cb-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="286cb-121">Vervollständigung mit der TAB-TASTE</span><span class="sxs-lookup"><span data-stu-id="286cb-121">Tab completion</span></span>

<span data-ttu-id="286cb-122">Fügen Sie die folgende Einstellung hinzu, um Vervollständigung mit der TAB-TASTE zu erzielen, die der ISE ähnlicher ist:</span><span class="sxs-lookup"><span data-stu-id="286cb-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="286cb-123">Diese Einstellung wurde VSCode direkt (anstatt in der Erweiterung) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="286cb-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="286cb-124">Das Verhalten wird direkt von VSCode bestimmt und kann durch die Erweiterung nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="286cb-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="286cb-125">Kein Fokus auf der Konsole bei der Ausführung</span><span class="sxs-lookup"><span data-stu-id="286cb-125">No focus on console when executing</span></span>

<span data-ttu-id="286cb-126">So bleibt der Fokus bei der Ausführung mit <kbd>F8</kbd> im Editor:</span><span class="sxs-lookup"><span data-stu-id="286cb-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="286cb-127">Der Standardwert ist aus Gründen der Barrierefreiheit `true`.</span><span class="sxs-lookup"><span data-stu-id="286cb-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="286cb-128">Integrierte Konsole beim Start nicht starten</span><span class="sxs-lookup"><span data-stu-id="286cb-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="286cb-129">Legen Sie Folgendes fest, um die integrierte Konsole beim Start zu beenden:</span><span class="sxs-lookup"><span data-stu-id="286cb-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="286cb-130">Der PowerShell-Hintergrundprozess wird trotzdem gestartet, da er IntelliSense, Skriptanalyse, Symbolnavigation usw. bereitstellt. Die Konsole wird aber nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="286cb-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="286cb-131">Standardmäßige Annahme, dass es sich um PowerShell-Dateien handelt</span><span class="sxs-lookup"><span data-stu-id="286cb-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="286cb-132">Um neue/unbenannte Dateien zu erstellen, registrieren Sie sie standardmäßig als PowerShell:</span><span class="sxs-lookup"><span data-stu-id="286cb-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="286cb-133">Farbschema</span><span class="sxs-lookup"><span data-stu-id="286cb-133">Color scheme</span></span>

<span data-ttu-id="286cb-134">Für VSCode stehen eine Reihe von ISE-Designs zur Verfügung, damit der Editor der ISE wesentlich ähnlicher sieht.</span><span class="sxs-lookup"><span data-stu-id="286cb-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="286cb-135">Geben Sie `theme` in der [Befehlspalette] ein, um `Preferences: Color Theme` abzurufen, und drücken Sie die <kbd>EINGABETASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="286cb-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="286cb-136">Wählen Sie in der Dropdownliste `PowerShell ISE` aus.</span><span class="sxs-lookup"><span data-stu-id="286cb-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="286cb-137">Sie können dieses Design in den Einstellungen wie folgt festlegen:</span><span class="sxs-lookup"><span data-stu-id="286cb-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="286cb-138">PowerShell-Befehls-Explorer</span><span class="sxs-lookup"><span data-stu-id="286cb-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="286cb-139">Dank der Arbeit von [@corbob](https://github.com/corbob) weist die PowerShell-Erweiterung Anfänge eines eigenen Befehls-Explorers auf.</span><span class="sxs-lookup"><span data-stu-id="286cb-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="286cb-140">Geben Sie `PowerShell Command Explorer` in der [Befehlspalette] ein, und drücken Sie die <kbd>EINGABETASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="286cb-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="286cb-141">Öffnen in der ISE</span><span class="sxs-lookup"><span data-stu-id="286cb-141">Open in the ISE</span></span>

<span data-ttu-id="286cb-142">Wenn Sie letztendlich trotzdem eine Datei in der ISE öffnen möchten, können Sie <kbd>UMSCHALT</kbd>+<kbd>ALT</kbd>+<kbd>P</kbd> verwenden.</span><span class="sxs-lookup"><span data-stu-id="286cb-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="286cb-143">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="286cb-143">Other resources</span></span>

- <span data-ttu-id="286cb-144">4sysops bietet [einen großartigen Artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) zur Konfiguration von VSCode, um der ISE ähnlicher zu sein.</span><span class="sxs-lookup"><span data-stu-id="286cb-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="286cb-145">Mike F. Robbins hat [einen hervorragenden Beitrag](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) zum Einrichten von VSCode verfasst.</span><span class="sxs-lookup"><span data-stu-id="286cb-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="286cb-146">Learn PowerShell bietet [eine ausgezeichnete Zusammenfassung](https://www.learnpwsh.com/setup-vs-code-for-powershell/) zur Einrichtung von VSCode für PowerShell.</span><span class="sxs-lookup"><span data-stu-id="286cb-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="286cb-147">Weitere Einstellungen</span><span class="sxs-lookup"><span data-stu-id="286cb-147">More settings</span></span>

<span data-ttu-id="286cb-148">Wenn Sie weitere Möglichkeiten kennen, wie Sie VSCode für ISE-Anwender vertrauter gestalten können, tragen Sie zu diesem Dokument bei. Wenn Sie nach einer Kompatibilitätskonfiguration suchen, aber keine Möglichkeit finden, diese zu aktivieren, [legen Sie ein Issue an](https://github.com/PowerShell/vscode-powershell/issues/new/choose), und fragen Sie nach einer Lösung!</span><span class="sxs-lookup"><span data-stu-id="286cb-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="286cb-149">Wir freuen uns immer über PRs und Beiträge!</span><span class="sxs-lookup"><span data-stu-id="286cb-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="286cb-150">VSCode-Tipps</span><span class="sxs-lookup"><span data-stu-id="286cb-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="286cb-151">Befehlspalette</span><span class="sxs-lookup"><span data-stu-id="286cb-151">Command Palette</span></span>

<span data-ttu-id="286cb-152"><kbd>F1</kbd> ODER <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> unter MacOS)</span><span class="sxs-lookup"><span data-stu-id="286cb-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="286cb-153">Eine praktische Möglichkeit zur Ausführung von Befehlen in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="286cb-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="286cb-154">Weitere Informationen finden Sie in der [VSCode-Dokumentation](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="286cb-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Befehlspalette]: #command-palette
[Command Palette]: #command-palette
