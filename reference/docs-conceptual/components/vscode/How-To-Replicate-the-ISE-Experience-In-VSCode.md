---
title: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
description: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012482"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="6cd37-103">Replizieren der ISE-Benutzeroberfläche in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6cd37-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="6cd37-104">Während die PowerShell-Erweiterung für VSCode vollständige Funktionsparität mit der PowerShell ISE seek nicht, gibt es Features direkt auf die VSCode-Erfahrung für Benutzer von ISE natürlicher zu machen.</span><span class="sxs-lookup"><span data-stu-id="6cd37-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="6cd37-105">Dieses Dokument versucht, listeneinstellungen, die Sie in Visual Studio Code, um die benutzerfreundlichkeit ein wenig mehr vertraut, die im Vergleich zu der ISE machen konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="6cd37-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="6cd37-106">Tastenzuordnungen</span><span class="sxs-lookup"><span data-stu-id="6cd37-106">Key bindings</span></span>

| <span data-ttu-id="6cd37-107">Funktion</span><span class="sxs-lookup"><span data-stu-id="6cd37-107">Function</span></span>                              | <span data-ttu-id="6cd37-108">ISE-Bindung</span><span class="sxs-lookup"><span data-stu-id="6cd37-108">ISE Binding</span></span>                  | <span data-ttu-id="6cd37-109">VSCode-Bindung</span><span class="sxs-lookup"><span data-stu-id="6cd37-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="6cd37-110">Unterbrechen und das Unterbrechen des Debuggers</span><span class="sxs-lookup"><span data-stu-id="6cd37-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="6cd37-111"><kbd>STRG</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="6cd37-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="6cd37-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="6cd37-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="6cd37-113">Führen Sie die aktuelle Zeile/hervorgehobener text</span><span class="sxs-lookup"><span data-stu-id="6cd37-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="6cd37-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="6cd37-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="6cd37-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="6cd37-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="6cd37-116">Liste verfügbaren Ausschnitte</span><span class="sxs-lookup"><span data-stu-id="6cd37-116">List available snippets</span></span>               | <span data-ttu-id="6cd37-117"><kbd>STRG</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="6cd37-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="6cd37-118"><kbd>STRG</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="6cd37-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="6cd37-119">Benutzerdefinierte Schlüssel-Bindungen</span><span class="sxs-lookup"><span data-stu-id="6cd37-119">Custom Key bindings</span></span>

<span data-ttu-id="6cd37-120">Sie können [konfigurieren Sie Ihre eigenen tastenzuordnungen](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in Visual Studio Code auch.</span><span class="sxs-lookup"><span data-stu-id="6cd37-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="6cd37-121">Registerkartenvervollständigung</span><span class="sxs-lookup"><span data-stu-id="6cd37-121">Tab completion</span></span>

<span data-ttu-id="6cd37-122">Um mehr ISE-ähnliche befehlszeilenergänzung zu aktivieren, fügen Sie diese Einstellung aus:</span><span class="sxs-lookup"><span data-stu-id="6cd37-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="6cd37-123">Diese Einstellung wurde direkt in VSCode (statt in der Erweiterung) hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="6cd37-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="6cd37-124">Das Verhalten wird direkt von VSCode bestimmt und kann nicht geändert werden, von der Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="6cd37-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="6cd37-125">Ohne Fokus auf die Konsole beim Ausführen</span><span class="sxs-lookup"><span data-stu-id="6cd37-125">No focus on console when executing</span></span>

<span data-ttu-id="6cd37-126">Zu den Fokus im Editor, beim Ausführen von mit <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="6cd37-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="6cd37-127">Der Standardwert ist `true` aus Gründen der Barrierefreiheit.</span><span class="sxs-lookup"><span data-stu-id="6cd37-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="6cd37-128">Integrierte Konsole kann beim Start nicht gestartet</span><span class="sxs-lookup"><span data-stu-id="6cd37-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="6cd37-129">Um die integrierte Konsole beim Start zu beenden, legen Sie Folgendes fest:</span><span class="sxs-lookup"><span data-stu-id="6cd37-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="6cd37-130">Hintergrund PowerShell-Prozess startet immer noch da, IntelliSense, Skript-Analyse, symbolnavigation usw. bereitstellt. Aber die Konsole wird nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="6cd37-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="6cd37-131">Wird davon ausgegangen Sie, dass Dateien mit PowerShell in der Standardeinstellung sind</span><span class="sxs-lookup"><span data-stu-id="6cd37-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="6cd37-132">Um neue/unbenannte Dateien zu machen, registrieren Sie standardmäßig als PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6cd37-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="6cd37-133">Farbschema</span><span class="sxs-lookup"><span data-stu-id="6cd37-133">Color scheme</span></span>

<span data-ttu-id="6cd37-134">Eine Anzahl von ISE Designs stehen zur Verfügung, für VSCode, um den Editor, suchen Sie die ISE eher zu machen.</span><span class="sxs-lookup"><span data-stu-id="6cd37-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="6cd37-135">In der [Befehlspalette] Typ `theme` abzurufenden `Preferences: Color Theme` , und drücken Sie <kbd>EINGABETASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="6cd37-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="6cd37-136">Wählen Sie in der Dropdown-Liste `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="6cd37-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="6cd37-137">Sie können dieses Design in den Einstellungen mit festlegen:</span><span class="sxs-lookup"><span data-stu-id="6cd37-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="6cd37-138">PowerShell-Befehl-Explorer</span><span class="sxs-lookup"><span data-stu-id="6cd37-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="6cd37-139">Dank der Arbeit der [ @corbob ](https://github.com/corbob), die PowerShell-Erweiterung verfügt über die Anfänge von eigenen Befehl-Explorer.</span><span class="sxs-lookup"><span data-stu-id="6cd37-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="6cd37-140">In der [Befehlspalette], geben Sie `PowerShell Command Explorer` , und drücken Sie <kbd>EINGABETASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="6cd37-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="6cd37-141">In der ISE öffnen</span><span class="sxs-lookup"><span data-stu-id="6cd37-141">Open in the ISE</span></span>

<span data-ttu-id="6cd37-142">Wenn Sie am Ende eine Datei trotzdem in der ISE öffnen möchten, können Sie <kbd>UMSCHALT</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="6cd37-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="6cd37-143">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="6cd37-143">Other resources</span></span>

- <span data-ttu-id="6cd37-144">4sysops hat [ein großartiger Artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) zum Konfigurieren von VSCode genauer wie der ISE.</span><span class="sxs-lookup"><span data-stu-id="6cd37-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="6cd37-145">Mike F Robbins hat [einen hervorragenden Beitrag](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) zum Einrichten von VSCode.</span><span class="sxs-lookup"><span data-stu-id="6cd37-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="6cd37-146">Erfahren Sie mehr PowerShell verfügt über [eine ausgezeichnete schreiben Sie](https://www.learnpwsh.com/setup-vs-code-for-powershell/) richten Sie zum Abrufen von VSCode für PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6cd37-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="6cd37-147">Weitere Einstellungen</span><span class="sxs-lookup"><span data-stu-id="6cd37-147">More settings</span></span>

<span data-ttu-id="6cd37-148">Wenn Sie weitere Informationen zum Stellen von VSCode für ISE Benutzer mehr vertraut sein kennen, tragen Sie zu diesem Dokument. Wenn eine Anwendungskompatibilitäts-Konfiguration, die Sie suchen vorliegt, aber keinesfalls zu seiner Aktivierung nicht auffindbar [eröffnen Sie ein Problem](https://github.com/PowerShell/vscode-powershell/issues/new/choose) und stellen Sie Ihre Fragen!</span><span class="sxs-lookup"><span data-stu-id="6cd37-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="6cd37-149">Wir freuen uns immer zum Akzeptieren von PRs und Beiträge auch!</span><span class="sxs-lookup"><span data-stu-id="6cd37-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="6cd37-150">VSCode-Tipps</span><span class="sxs-lookup"><span data-stu-id="6cd37-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="6cd37-151">Befehlspalette</span><span class="sxs-lookup"><span data-stu-id="6cd37-151">Command Palette</span></span>

<span data-ttu-id="6cd37-152"><kbd>F1</kbd> oder <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Shift</kbd>+<kbd>P</kbd> unter MacOS)</span><span class="sxs-lookup"><span data-stu-id="6cd37-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="6cd37-153">Eine praktische Möglichkeit der Ausführung von Befehlen in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="6cd37-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="6cd37-154">Weitere Informationen finden Sie unter [VSCode Dokumentation](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="6cd37-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Befehlspalette]: #command-palette
[Command Palette]: #command-palette
