---
title: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
description: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 5251094388f6abc7da7f2cc706537eade78df7c9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978694"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="b3e87-103">Verwenden von Visual Studio Code für die Entwicklung mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3e87-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="b3e87-104">[Visual Studio Code][vscode] ist ein plattformübergreifender Skript-Editor von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b3e87-104">[Visual Studio Code][vscode] is a cross-platform script editor by Microsoft.</span></span> <span data-ttu-id="b3e87-105">In Verbindung mit der [PowerShell-Erweiterung][psext] bietet er eine umfassende und interaktive Oberfläche zur Skriptbearbeitung, die das Schreiben zuverlässiger PowerShell-Skripts vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="b3e87-105">Together with the [PowerShell extension][psext], it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span> <span data-ttu-id="b3e87-106">Visual Studio Code mit PowerShell-Erweiterung ist der empfohlene Editor zum Schreiben von PowerShell-Skripts.</span><span class="sxs-lookup"><span data-stu-id="b3e87-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>

<span data-ttu-id="b3e87-107">Die folgenden PowerShell-Versionen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="b3e87-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="b3e87-108">PowerShell 7 und höher (Windows, macOS und Linux)</span><span class="sxs-lookup"><span data-stu-id="b3e87-108">PowerShell 7 and up (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="b3e87-109">PowerShell Core 6 (Windows, macOS und Linux)</span><span class="sxs-lookup"><span data-stu-id="b3e87-109">PowerShell Core 6 (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="b3e87-110">Windows PowerShell 5.1 (nur Windows)</span><span class="sxs-lookup"><span data-stu-id="b3e87-110">Windows PowerShell 5.1 (Windows-only)</span></span>

> [!NOTE]
> <span data-ttu-id="b3e87-111">Visual Studio Code ist nicht identisch mit [Visual Studio][].</span><span class="sxs-lookup"><span data-stu-id="b3e87-111">Visual Studio Code is not the same as [Visual Studio][].</span></span>

## <a name="getting-started"></a><span data-ttu-id="b3e87-112">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="b3e87-112">Getting started</span></span>

<span data-ttu-id="b3e87-113">Prüfen Sie, ob PowerShell auf Ihrem System vorhanden ist, bevor Sie starten.</span><span class="sxs-lookup"><span data-stu-id="b3e87-113">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="b3e87-114">Aktuelle Workloads unter Windows, macOS und Linux finden Sie unter den folgenden Links:</span><span class="sxs-lookup"><span data-stu-id="b3e87-114">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="b3e87-115">[Installieren von PowerShell unter Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="b3e87-115">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="b3e87-116">[Installieren von PowerShell unter macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="b3e87-116">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="b3e87-117">[Installieren von PowerShell unter Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="b3e87-117">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="b3e87-118">Herkömmliche Windows PowerShell-Workloads finden Sie unter [Installieren von Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="b3e87-118">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3e87-119">Die [Windows PowerShell ISE][ise] ist für Windows weiterhin verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b3e87-119">The [Windows PowerShell ISE][ise] is still available for Windows.</span></span> <span data-ttu-id="b3e87-120">Sie befindet sich jedoch nicht mehr in der aktiven Featureentwicklung.</span><span class="sxs-lookup"><span data-stu-id="b3e87-120">However, it is no longer in active feature development.</span></span> <span data-ttu-id="b3e87-121">Die ISE funktioniert nicht mit PowerShell 6 und höher.</span><span class="sxs-lookup"><span data-stu-id="b3e87-121">The ISE does not work with PowerShell 6 and higher.</span></span> <span data-ttu-id="b3e87-122">Als Windows-Komponente wird sie weiterhin offiziell mit Sicherheits- und Wartungsfixes hoher Priorität unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b3e87-122">As a component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="b3e87-123">Es ist nicht geplant, die ISE aus Windows zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-123">We have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="b3e87-124">Bearbeiten von Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b3e87-124">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="b3e87-125">Installieren Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b3e87-125">Install Visual Studio Code.</span></span> <span data-ttu-id="b3e87-126">Weitere Informationen finden Sie in der Übersicht [Einrichten von Visual Studio Code][vsc-setup].</span><span class="sxs-lookup"><span data-stu-id="b3e87-126">For more information, see the overview [Setting up Visual Studio Code][vsc-setup].</span></span>

   <span data-ttu-id="b3e87-127">Dort finden Sie Installationsanweisungen für jede Plattform:</span><span class="sxs-lookup"><span data-stu-id="b3e87-127">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="b3e87-128">**Windows**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter Windows][vsc-setup-win] aus.</span><span class="sxs-lookup"><span data-stu-id="b3e87-128">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows][vsc-setup-win] page.</span></span>
   - <span data-ttu-id="b3e87-129">**macOS**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter macOS][vsc-setup-macOS] aus.</span><span class="sxs-lookup"><span data-stu-id="b3e87-129">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS][vsc-setup-macOS] page.</span></span>
   - <span data-ttu-id="b3e87-130">**Linux**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter Linux][vsc-setup-linux] aus.</span><span class="sxs-lookup"><span data-stu-id="b3e87-130">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux][vsc-setup-linux] page.</span></span>

1. <span data-ttu-id="b3e87-131">Installieren Sie die PowerShell-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="b3e87-131">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="b3e87-132">Starten Sie die Visual Studio Code-App, indem Sie `code` in einer Konsole eingeben bzw. `code-insiders`, falls Sie Visual Studio Code für Insider installiert haben.</span><span class="sxs-lookup"><span data-stu-id="b3e87-132">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="b3e87-133">Starten Sie **Quick Open** unter Windows oder Linux, indem Sie <kbd>STRG</kbd>+<kbd>P</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="b3e87-133">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="b3e87-134">Drücken Sie unter macOS <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b3e87-134">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="b3e87-135">Geben Sie in Quick Open `ext install powershell` ein, und drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="b3e87-135">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="b3e87-136">Dann öffnet sich die Ansicht **Erweiterungen** in der Seitenleiste.</span><span class="sxs-lookup"><span data-stu-id="b3e87-136">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="b3e87-137">Wählen Sie die PowerShell-Erweiterung für Microsoft aus.</span><span class="sxs-lookup"><span data-stu-id="b3e87-137">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="b3e87-138">Ihnen wird in etwa folgender Visual Studio Code-Bildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b3e87-138">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="b3e87-140">Klicken Sie auf die Schaltfläche **Installieren** in der PowerShell-Erweiterung für Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b3e87-140">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="b3e87-141">Nach der Installation ändert sich die Schaltfläche **Installieren** in **Erneut laden**. Klicken Sie auf **Erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="b3e87-141">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="b3e87-142">Nachdem Visual Studio Code neu geladen wurde, können Sie Bearbeitungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-142">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="b3e87-143">Klicken Sie z. B. auf **Datei > Neu**, um eine neue Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-143">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="b3e87-144">Klicken Sie zum Speichern auf **Datei > Speichern**, und geben Sie anschließend einen Dateinamen ein, z. B. `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b3e87-144">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="b3e87-145">Klicken Sie auf `X` neben dem Dateinamen, um die Datei zu schließen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-145">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="b3e87-146">Klicken Sie auf **Datei > Beenden**, um Visual Studio Code zu beenden.</span><span class="sxs-lookup"><span data-stu-id="b3e87-146">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="b3e87-147">Installieren der PowerShell-Erweiterung auf eingeschränkten Systemen</span><span class="sxs-lookup"><span data-stu-id="b3e87-147">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="b3e87-148">Einige Systeme sind so eingerichtet, dass alle Codesignaturen überprüft werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-148">Some systems are set up to require validation of all code signatures.</span></span> <span data-ttu-id="b3e87-149">Unter Umständen wird der folgende Fehler angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b3e87-149">You may receive the following error:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="b3e87-150">Dieses Problem kann auftreten, wenn die PowerShell-Ausführungsrichtlinie von Windows-Gruppenrichtlinie festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b3e87-150">This problem can occur when PowerShell's execution policy is set by Windows Group Policy.</span></span> <span data-ttu-id="b3e87-151">Öffnen Sie eine PowerShell-Eingabeaufforderung, um die Editor-Dienste von PowerShell und die PowerShell-Erweiterung für Visual Studio Code manuell zu genehmigen, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="b3e87-151">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="b3e87-152">Sie werden gefragt: **Möchten Sie Software von diesem nicht vertrauenswürdigen Herausgeber ausführen?** .</span><span class="sxs-lookup"><span data-stu-id="b3e87-152">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="b3e87-153">Geben Sie `A` ein, um die Datei auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-153">Type `A` to run the file.</span></span> <span data-ttu-id="b3e87-154">Öffnen Sie dann Visual Studio Code, und überprüfen Sie, ob die PowerShell-Erweiterung ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b3e87-154">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="b3e87-155">Wenn weiterhin Probleme auftreten, lassen Sie uns dies auf [GitHub-Probleme][] wissen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-155">If you still have problems getting started, let us know on [GitHub issues][].</span></span>

> [!NOTE]
> <span data-ttu-id="b3e87-156">Die PowerShell-Erweiterung für Visual Studio Code unterstützt nicht die Ausführung im eingeschränkten Sprachmodus.</span><span class="sxs-lookup"><span data-stu-id="b3e87-156">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="b3e87-157">Weitere Informationen finden Sie unter dem [GitHub-Problem #606][i606].</span><span class="sxs-lookup"><span data-stu-id="b3e87-157">For more information, see [GitHub issue #606][i606].</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="b3e87-158">Auswählen einer Version von PowerShell für die Verwendung mit der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b3e87-158">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="b3e87-159">Mit einer parallelen Installation von PowerShell Core und Windows PowerShell ist es jetzt möglich, eine bestimmte Version von PowerShell mit der PowerShell-Erweiterung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3e87-159">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a specific version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="b3e87-160">Dieses Feature sucht in ein paar bekannten Pfaden unter verschiedenen Betriebssystemen, um PowerShell-Installationen zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="b3e87-160">This feature looks at a few well-known paths on different operating systems to discover installations of PowerShell.</span></span>

<span data-ttu-id="b3e87-161">Verwenden Sie die folgenden Schritte, um die Version auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="b3e87-161">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="b3e87-162">Öffnen Sie die **Befehlspalette** unter Windows oder Linux mit <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b3e87-162">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="b3e87-163">Verwenden Sie unter macOS <kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b3e87-163">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="b3e87-164">Suchen Sie nach **Sitzung**.</span><span class="sxs-lookup"><span data-stu-id="b3e87-164">Search for **Session**.</span></span>
1. <span data-ttu-id="b3e87-165">Klicken Sie auf **PowerShell: Menü „Sitzung“ anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="b3e87-165">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="b3e87-166">Wählen Sie die Version von PowerShell aus der Liste aus, die Sie verwenden möchten, z. B. **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="b3e87-166">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

<span data-ttu-id="b3e87-167">Wenn Sie PowerShell an einem untypischen Speicherort installiert haben, wird es möglicherweise anfangs nicht im Menü „Sitzung“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b3e87-167">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="b3e87-168">Sie können das Menü „Sitzung“ erweitern, indem Sie [Ihre eigenen benutzerdefinierten Pfade hinzufügen](#adding-your-own-powershell-paths-to-the-session-menu), wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b3e87-168">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

> [!NOTE]
> <span data-ttu-id="b3e87-169">Der Zugriff auf das PowerShell-Sitzungsmenü ist auch über die grüne Versionsnummer unten rechts auf der Statusleiste möglich.</span><span class="sxs-lookup"><span data-stu-id="b3e87-169">The PowerShell session menu can also be accessed from the green version number in the bottom right corner of status bar.</span></span> <span data-ttu-id="b3e87-170">Wenn Sie auf diese Versionsnummer klicken, wird das Menü „Sitzung“ geöffnet.</span><span class="sxs-lookup"><span data-stu-id="b3e87-170">Clicking this version number opens the session menu.</span></span>

## <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="b3e87-171">Konfigurationseinstellungen für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b3e87-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="b3e87-172">Wenn Sie mit dem Ändern von Einstellungen in Visual Studio Code nicht vertraut sind, sollten Sie die [Dokumentation zu den Visual Studio Code-Einstellungen][vsc-settings] lesen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-172">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend reading [Visual Studio Code's settings][vsc-settings] documentation.</span></span>

<span data-ttu-id="b3e87-173">Anschließend können Sie Konfigurationseinstellungen in `settings.json` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-173">After reading the documentation, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="b3e87-174">Wenn Sie nicht möchten, dass diese Einstellungen für alle Dateitypen gelten, können Sie in Visual Studio Code auch sprachspezifische Konfigurationen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-174">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="b3e87-175">Sie können sprachspezifische Einstellungen erstellen, indem Sie Einstellungen in ein `[<language-name>]` einfügen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-175">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="b3e87-176">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b3e87-176">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="b3e87-177">Weitere Informationen zur Dateicodierung in Visual Studio Code finden Sie unter [Informationen zur Dateicodierung][file-encoding].</span><span class="sxs-lookup"><span data-stu-id="b3e87-177">For more information about file encoding in Visual Studio Code, see [Understanding file encoding][file-encoding].</span></span>
>
> <span data-ttu-id="b3e87-178">Weitere Tipps zum Konfigurieren von Visual Studio Code für die PowerShell-Bearbeitung finden Sie unter [Replizieren der ISE-Benutzeroberfläche in Visual Studio Code][vsc-ise].</span><span class="sxs-lookup"><span data-stu-id="b3e87-178">Also, check out [How to replicate the ISE experience in Visual Studio Code][vsc-ise] for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="b3e87-179">Hinzufügen Ihres eigenen PowerShell-Pfads zum Menü „Sitzung“</span><span class="sxs-lookup"><span data-stu-id="b3e87-179">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="b3e87-180">Sie können dem Sitzungsmenü über die folgende [Visual Studio Code-Einstellung](https://code.visualstudio.com/docs/getstarted/settings) andere PowerShell-Pfade für ausführbare Dateien hinzufügen: `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="b3e87-180">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="b3e87-181">Fügen Sie der Liste `powershell.powerShellAdditionalExePaths` eine Element hinzu, oder erstellen Sie die Liste, wenn sie in Ihrer `settings.json` nicht vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="b3e87-181">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="b3e87-182">Jedes Element benötigt:</span><span class="sxs-lookup"><span data-stu-id="b3e87-182">Each item must have:</span></span>

- <span data-ttu-id="b3e87-183">`exePath`: Der Pfad zu `pwsh` oder zur ausführbaren `powershell`-Datei.</span><span class="sxs-lookup"><span data-stu-id="b3e87-183">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="b3e87-184">`versionName`: Der Text, der im Menü „Sitzung“ angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b3e87-184">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="b3e87-185">Zum Festlegen der PowerShell-Standardversion legen Sie den Wert `powershell.powerShellDefaultVersion` auf den im Sitzungsmenü angezeigten Text fest (auch als `versionName` bezeichnet):</span><span class="sxs-lookup"><span data-stu-id="b3e87-185">To set the default PowerShell version, set the value `powershell.powerShellDefaultVersion` to the text displayed in the session menu (also known as the `versionName`):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="b3e87-186">Nachdem Sie diese Einstellung konfiguriert haben, starten Sie Visual Studio Code neu, oder laden Sie das aktuelle Visual Studio Code-Fenster über die **Befehlspalette**, und geben Sie **Entwickler: Fenster neu laden** ein.</span><span class="sxs-lookup"><span data-stu-id="b3e87-186">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="b3e87-187">Wenn Sie das Menü „Sitzung“ öffnen, werden jetzt Ihre zusätzlichen PowerShell-Versionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b3e87-187">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="b3e87-188">Wenn Sie PowerShell aus der Quelle erstellen, ist dies eine hervorragende Möglichkeit zum Testen Ihres lokalen Builds von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3e87-188">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="b3e87-189">Verwenden einer älteren Version der PowerShell-Erweiterung für Windows PowerShell v3 und v4</span><span class="sxs-lookup"><span data-stu-id="b3e87-189">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="b3e87-190">Die aktuelle PowerShell-Erweiterung bietet keine Unterstützung für [PowerShell v3 und v4][i1310].</span><span class="sxs-lookup"><span data-stu-id="b3e87-190">The current PowerShell extension doesn't support [PowerShell v3 and v4][i1310].</span></span> <span data-ttu-id="b3e87-191">Sie können jedoch die letzte Version der Erweiterung verwenden, die PowerShell v3 und v4 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b3e87-191">However, you can use the last version of the extension that supports PowerShell v3 and v4.</span></span>

> [!CAUTION]
> <span data-ttu-id="b3e87-192">Für diese ältere Version der Erweiterung werden keine weiteren Fixes bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="b3e87-192">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="b3e87-193">Sie wird in der vorgelegten Form („AS IS“) bereitgestellt, ist aber für Sie verfügbar, wenn Sie noch Windows PowerShell v3 und Windows PowerShell v4 verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3e87-193">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="b3e87-194">Öffnen Sie zunächst den Erweiterungsbereich, und suchen Sie nach `PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="b3e87-194">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="b3e87-195">Klicken Sie dann auf das Zahnrad, und wählen Sie **Andere Version installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="b3e87-195">Then click the gear and select **Install another version...**.</span></span>

![Andere Version installieren...](media/using-vscode/install-another-version.png)

<span data-ttu-id="b3e87-197">Wählen Sie anschließend die Version **2020.1.0** aus.</span><span class="sxs-lookup"><span data-stu-id="b3e87-197">Then select the **2020.1.0** version.</span></span> <span data-ttu-id="b3e87-198">Diese Version der Erweiterung ist die letzte Version, die v3 und v4 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b3e87-198">This version of the extension was the last version to support v3 and v4.</span></span> <span data-ttu-id="b3e87-199">Fügen Sie außerdem die folgende Einstellung hinzu, damit Ihre Erweiterungsversion nicht automatisch aktualisiert wird:</span><span class="sxs-lookup"><span data-stu-id="b3e87-199">Be sure to add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="b3e87-200">Die Version **2020.1.0** wird auf absehbare Zeit funktionieren.</span><span class="sxs-lookup"><span data-stu-id="b3e87-200">Version **2020.1.0** will work for the foreseeable future.</span></span> <span data-ttu-id="b3e87-201">Dennoch könnte Visual Studio Code eine Änderung implementieren, die bei dieser Version der Erweiterung einen Fehler verursacht.</span><span class="sxs-lookup"><span data-stu-id="b3e87-201">However, Visual Studio Code could implement a change that breaks this version of the extension.</span></span> <span data-ttu-id="b3e87-202">Aus diesem Grund und aufgrund der fehlenden Unterstützung wird eine der beiden folgenden Aktionen empfohlen:</span><span class="sxs-lookup"><span data-stu-id="b3e87-202">Because of this, and lack of support, we recommend:</span></span>

- <span data-ttu-id="b3e87-203">Upgrade auf Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="b3e87-203">Upgrading to Windows PowerShell 5.1</span></span>
- <span data-ttu-id="b3e87-204">Installieren von PowerShell 7 (dies ist eine parallele Installation zu Windows PowerShell, die mit der PowerShell-Erweiterung am besten funktioniert)</span><span class="sxs-lookup"><span data-stu-id="b3e87-204">Install PowerShell 7, which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="b3e87-205">Debuggen mit Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b3e87-205">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="b3e87-206">Debuggen außerhalb des Arbeitsbereichs</span><span class="sxs-lookup"><span data-stu-id="b3e87-206">No-workspace debugging</span></span>

<span data-ttu-id="b3e87-207">In Visual Studio Code Version 1.9 (oder höher) können Sie PowerShell-Skripts debuggen, ohne den Ordner öffnen zu müssen, in dem das PowerShell-Skript enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="b3e87-207">In Visual Studio Code version 1.9 (or higher), you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span>

1. <span data-ttu-id="b3e87-208">Öffnen Sie die PowerShell-Skriptdatei über **Datei > Datei öffnen...**</span><span class="sxs-lookup"><span data-stu-id="b3e87-208">Open the PowerShell script file with **File > Open File...**</span></span>
1. <span data-ttu-id="b3e87-209">Legen Sie einen Breakpoint fest (wählen Sie eine Zeile aus, und drücken Sie dann <kbd>F9</kbd>)</span><span class="sxs-lookup"><span data-stu-id="b3e87-209">Set a breakpoint - select a line then press <kbd>F9</kbd></span></span>
1. <span data-ttu-id="b3e87-210">Drücken Sie <kbd>F5</kbd>, um das Debuggen zu starten</span><span class="sxs-lookup"><span data-stu-id="b3e87-210">Press <kbd>F5</kbd> to start debugging</span></span>

<span data-ttu-id="b3e87-211">Dann wird der Aktionsbereich „Debuggen“ angezeigt, über den Sie den Debugger anhalten und den Debugvorgang ausführen, fortsetzen oder abbrechen können.</span><span class="sxs-lookup"><span data-stu-id="b3e87-211">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="b3e87-212">Debuggen von Arbeitsbereichen</span><span class="sxs-lookup"><span data-stu-id="b3e87-212">Workspace debugging</span></span>

<span data-ttu-id="b3e87-213">Wenn davon die Rede ist, Arbeitsbereiche zu debuggen, ist damit das Debuggen eines Ordners gemeint, den Sie über **Ordner öffnen...** im Menü **Datei** geöffnet haben. In der Regel ist dies der PowerShell-Projektordner oder der Stamm des Git-Repositorys.</span><span class="sxs-lookup"><span data-stu-id="b3e87-213">Workspace debugging refers to debugging in the context of a folder that you've opened from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder or the root of your Git repository.</span></span> <span data-ttu-id="b3e87-214">Beim Debuggen von Arbeitsbereichen kann nicht nur für die aktuell geöffnete Datei ein Debugvorgang ausgeführt werden, sondern es können auch mehrere Debugkonfigurationen definiert werden.</span><span class="sxs-lookup"><span data-stu-id="b3e87-214">Workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>

<span data-ttu-id="b3e87-215">Führen Sie die folgenden Schritte aus, um eine Konfigurationsdatei für den Debugvorgang zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="b3e87-215">Follow these steps to create a debug configuration file:</span></span>

1. <span data-ttu-id="b3e87-216">Öffnen Sie die Ansicht **Debuggen** in Windows oder Linux, indem Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="b3e87-216">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="b3e87-217">Drücken Sie unter macOS <kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b3e87-217">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
1. <span data-ttu-id="b3e87-218">Klicken Sie auf den **Link zum Erstellen einer Datei „launch.json“** .</span><span class="sxs-lookup"><span data-stu-id="b3e87-218">Click the **create a launch.json file** link.</span></span>
1. <span data-ttu-id="b3e87-219">Wählen Sie in der Eingabeaufforderung **Umgebung auswählen** die Option **PowerShell** aus.</span><span class="sxs-lookup"><span data-stu-id="b3e87-219">From the **Select Environment** prompt, choose **PowerShell**.</span></span>
1. <span data-ttu-id="b3e87-220">Wählen Sie den gewünschten Debugtyp aus:</span><span class="sxs-lookup"><span data-stu-id="b3e87-220">Choose the type of debugging you'd like to use:</span></span>

   - <span data-ttu-id="b3e87-221">**Aktuelle Datei starten**: Starten und Debuggen der Datei im aktuell aktiven Editor-Fenster</span><span class="sxs-lookup"><span data-stu-id="b3e87-221">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
   - <span data-ttu-id="b3e87-222">**Skript starten**: Starten und Debuggen der angegebenen Datei oder des angegebenen Befehls</span><span class="sxs-lookup"><span data-stu-id="b3e87-222">**Launch Script** - Launch and debug the specified file or command</span></span>
   - <span data-ttu-id="b3e87-223">**Interaktive Sitzung**: Debuggen von Befehlen, die über die integrierte Konsole ausgeführt werden</span><span class="sxs-lookup"><span data-stu-id="b3e87-223">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
   - <span data-ttu-id="b3e87-224">**Anfügen**: Anfügen des Debuggers an einen ausgeführten PowerShell-Hostvorgang</span><span class="sxs-lookup"><span data-stu-id="b3e87-224">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="b3e87-225">Visual Studio Code erstellt im Stamm Ihres Arbeitsbereichsordners ein Verzeichnis und eine Datei `.vscode\launch.json` zum Speichern der Debugkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="b3e87-225">Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder to store the debug configuration.</span></span> <span data-ttu-id="b3e87-226">Wenn sich Ihre Dateien in einem Git-Repository befinden, sollten Sie einen Commit für die `launch.json`-Datei ausführen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-226">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="b3e87-227">Die `launch.json`-Datei beinhaltet:</span><span class="sxs-lookup"><span data-stu-id="b3e87-227">The contents of the `launch.json` file are:</span></span>

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

<span data-ttu-id="b3e87-228">Diese Datei ist ein Beispiel für häufig auftretende Debugszenarios.</span><span class="sxs-lookup"><span data-stu-id="b3e87-228">This file represents the common debug scenarios.</span></span> <span data-ttu-id="b3e87-229">Wenn Sie diese Datei im Editor öffnen, wird die Schaltfläche **Konfiguration hinzufügen...** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b3e87-229">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="b3e87-230">Sie können auf diese Schaltfläche klicken, um weitere Debugkonfigurationen für PowerShell hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-230">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="b3e87-231">Sie können zum Beispiel die Konfiguration **PowerShell: Launch Script** (PowerShell: Skript starten) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-231">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="b3e87-232">Mithilfe dieser Konfiguration können Sie eine Datei mit optionalen Argumenten angeben, die immer dann verwendet werden sollen, wenn Sie <kbd>F5</kbd> drücken. Dabei macht es keinen Unterschied, welche Datei aktuell im Editor aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="b3e87-232">With this configuration, you can specify a file containing optional arguments that are used whenever you press <kbd>F5</kbd> no matter which file is active in the editor.</span></span>

<span data-ttu-id="b3e87-233">Nachdem die Debugkonfiguration eingerichtet wurde, können Sie auswählen, welche Konfiguration Sie während einer Debugsitzung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="b3e87-233">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="b3e87-234">Wählen Sie eine Konfiguration aus der Dropdownliste „Debugkonfiguration“ in der Symbolleiste der Ansicht **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="b3e87-234">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="b3e87-235">Problembehandlung der PowerShell-Erweiterung für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b3e87-235">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="b3e87-236">Wenn bei der Verwendung von Visual Studio Code für die PowerShell-Skriptentwicklung Probleme auftreten, sehen Sie sich den [Leitfaden zur Problembehandlung][troubleshooting] auf GitHub an.</span><span class="sxs-lookup"><span data-stu-id="b3e87-236">If you experience any issues using Visual Studio Code for PowerShell script development, see the [troubleshooting guide][troubleshooting] on GitHub.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="b3e87-237">Nützliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="b3e87-237">Useful resources</span></span>

<span data-ttu-id="b3e87-238">Im Folgenden sind einige Videos und Blogbeiträge aufgeführt, die bei den ersten Schritten mit der PowerShell-Erweiterung für Visual Studio Code hilfreich sein können:</span><span class="sxs-lookup"><span data-stu-id="b3e87-238">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="b3e87-239">Videos</span><span class="sxs-lookup"><span data-stu-id="b3e87-239">Videos</span></span>

- <span data-ttu-id="b3e87-240">[Using Visual Studio Code as Your Default PowerShell Editor](https://youtu.be/bGn45vIeAMM) (Verwenden von Visual Studio Code als PowerShell-Standard-Editor)</span><span class="sxs-lookup"><span data-stu-id="b3e87-240">[Using Visual Studio Code as Your Default PowerShell Editor](https://youtu.be/bGn45vIeAMM)</span></span>
- <span data-ttu-id="b3e87-241">[Visual Studio Code: deep dive into debugging your PowerShell scripts](https://youtu.be/cSbIXmlkr8o) (Visual Studio Code: Ausführliche Einführung in das Debuggen von PowerShell-Skripts)</span><span class="sxs-lookup"><span data-stu-id="b3e87-241">[Visual Studio Code: deep dive into debugging your PowerShell scripts](https://youtu.be/cSbIXmlkr8o)</span></span>

### <a name="blog-posts"></a><span data-ttu-id="b3e87-242">Blogbeiträge</span><span class="sxs-lookup"><span data-stu-id="b3e87-242">Blog posts</span></span>

- <span data-ttu-id="b3e87-243">[PowerShell-Erweiterung][pscdn]</span><span class="sxs-lookup"><span data-stu-id="b3e87-243">[PowerShell Extension][pscdn]</span></span>
- <span data-ttu-id="b3e87-244">[Write and debug PowerShell scripts in Visual Studio Code (Schreiben und Debuggen von PowerShell-Skripts in Visual Studio Code)][debug]</span><span class="sxs-lookup"><span data-stu-id="b3e87-244">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="b3e87-245">[Debugging Visual Studio Code Guidance (Anleitung zum Debuggen in Visual Studio Code)][psdbgblog]</span><span class="sxs-lookup"><span data-stu-id="b3e87-245">[Debugging Visual Studio Code Guidance][psdbgblog]</span></span>
- <span data-ttu-id="b3e87-246">[Debugging PowerShell in Visual Studio Code (Debuggen von PowerShell in Visual Studio Code)][psdbg-gh]</span><span class="sxs-lookup"><span data-stu-id="b3e87-246">[Debugging PowerShell in Visual Studio Code][psdbg-gh]</span></span>
- <span data-ttu-id="b3e87-247">[Get started with PowerShell development in Visual Studio Code (Erste Schritte für die PowerShell-Entwicklung in Visual Studio Code)][getting-started]</span><span class="sxs-lookup"><span data-stu-id="b3e87-247">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="b3e87-248">[Visual Studio Code editing features for PowerShell development – Part 1 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 1)][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="b3e87-248">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="b3e87-249">[Visual Studio Code editing features for PowerShell development – Part 2 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 2)][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="b3e87-249">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="b3e87-250">[Debugging PowerShell script in Visual Studio Code – Part 1 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 1)][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="b3e87-250">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="b3e87-251">[Debugging PowerShell script in Visual Studio Code – Part 2 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 2)][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="b3e87-251">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-project-source-code"></a><span data-ttu-id="b3e87-252">Quellcode des PowerShell-Erweiterungsprojekts</span><span class="sxs-lookup"><span data-stu-id="b3e87-252">PowerShell extension project source code</span></span>

<span data-ttu-id="b3e87-253">Sie finden den Quellcode der PowerShell-Erweiterung auf [GitHub][psext-src].</span><span class="sxs-lookup"><span data-stu-id="b3e87-253">The PowerShell extension's source code can be found on [GitHub][psext-src].</span></span>

<span data-ttu-id="b3e87-254">Wenn Sie an diesen Inhalten mitwirken möchten, sind Pull Requests sehr willkommen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-254">If you're interested in contributing, Pull Requests are greatly appreciated.</span></span> <span data-ttu-id="b3e87-255">Befolgen Sie die Schritte in der [Entwicklerdokumentation auf GitHub][dev-docs], um loszulegen.</span><span class="sxs-lookup"><span data-stu-id="b3e87-255">Follow along with the [developer documentation][dev-docs] on GitHub to get started.</span></span>

<!-- related articles -->
[ise]:                    ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[GitHub-Probleme]:          https://github.com/PowerShell/vscode-powershell/issues
[GitHub issues]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
