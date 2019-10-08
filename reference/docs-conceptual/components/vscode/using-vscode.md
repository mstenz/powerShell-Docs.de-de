---
title: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
description: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325228"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="4ab7e-103">Verwenden von Visual Studio Code für die Entwicklung mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ab7e-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="4ab7e-104">Neben der [PowerShell ISE][ise] wird auch PowerShell in Visual Studio Code (VS Code) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="4ab7e-105">Außerdem wird die PowerShell ISE zwar nicht mit PowerShell Core unterstützt, jedoch wird VS Code für PowerShell Core auf sämtlichen Plattformen (Windows, macOS und Linux) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-105">Furthermore, the ISE is not supported with PowerShell Core, while VSCode is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="4ab7e-106">Sie können VS Code unter Windows mit PowerShell Version 5 verwenden, wenn Sie Windows 10 verwenden oder für ältere Windows-Versionen (z.B. Windows 8.1) [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) installieren.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="4ab7e-107">Prüfen Sie, ob PowerShell auf Ihrem System vorhanden ist, bevor Sie das Programm starten.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-107">Before starting it, please make sure PowerShell exists on your system.</span></span> <span data-ttu-id="4ab7e-108">Aktuelle Workloads unter Windows, macOS und Linux finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="4ab7e-109">[Installieren von PowerShell Core unter Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="4ab7e-110">[Installieren von PowerShell Core unter macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="4ab7e-111">[Installing PowerShell Core on Windows (Installieren von PowerShell Core unter Windows)][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="4ab7e-112">Herkömmliche Windows PowerShell-Workloads finden Sie unter [Installieren von Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="4ab7e-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="4ab7e-113">Bearbeiten mit VS Code</span><span class="sxs-lookup"><span data-stu-id="4ab7e-113">Editing with VSCode</span></span>

1. [<span data-ttu-id="4ab7e-114">Installieren von VS Code</span><span class="sxs-lookup"><span data-stu-id="4ab7e-114">Installing VSCode</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

   - <span data-ttu-id="4ab7e-115">**Linux:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on Linux (Ausführen von VS Code unter Linux)](https://code.visualstudio.com/docs/setup/linux) aus.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-115">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>
   - <span data-ttu-id="4ab7e-116">**macOS:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on macOS (Ausführen von VS Code unter macOS)](https://code.visualstudio.com/docs/setup/mac) aus.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-116">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="4ab7e-117">Unter macOS müssen Sie OpenSSL für die PowerShell-Erweiterung installieren, damit diese einwandfrei funktionieren kann.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="4ab7e-118">Dies funktioniert am besten, wenn Sie [Homebrew](https://brew.sh/) installieren und anschließend `brew install openssl` ausführen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="4ab7e-119">VS Code kann jetzt die PowerShell-Erweiterung erfolgreich laden.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-119">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="4ab7e-120">**Windows:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on Windows (Ausführen von VS Code unter Windows)](https://code.visualstudio.com/docs/setup/windows) aus.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-120">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

2. <span data-ttu-id="4ab7e-121">Installieren der PowerShell-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="4ab7e-121">Installing PowerShell Extension</span></span>

   - <span data-ttu-id="4ab7e-122">Starten Sie VS Code, indem Sie:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-122">Launch the VSCode app by:</span></span>
     - <span data-ttu-id="4ab7e-123">**Windows:** `code` in Ihre PowerShell-Sitzung eingeben.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-123">**Windows**: typing `code` in your PowerShell session</span></span>
     - <span data-ttu-id="4ab7e-124">**Linux:** `code` in Ihr Terminal eingeben.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-124">**Linux**: typing `code` in your terminal</span></span>
     - <span data-ttu-id="4ab7e-125">**macOS:** `code` in Ihr Terminal eingeben.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-125">**macOS**: typing `code` in your terminal</span></span>
   - <span data-ttu-id="4ab7e-126">Starten Sie **Quick Open**, indem Sie <kbd>STRG</kbd>+<kbd>P</kbd> (<kbd>cmd</kbd>+<kbd>P</kbd> unter Mac) drücken.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-126">Launch **Quick Open** by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>P</kbd> on Mac).</span></span>
   - <span data-ttu-id="4ab7e-127">Geben Sie in Quick Open `ext install powershell` ein, und drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
   - <span data-ttu-id="4ab7e-128">Dann öffnet sich die Ansicht **Erweiterungen** in der Seitenleiste.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="4ab7e-129">Wählen Sie die PowerShell-Erweiterung für Microsoft aus.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-129">Select the PowerShell extension from Microsoft.</span></span>
     <span data-ttu-id="4ab7e-130">Es sollte etwa Folgendes angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-130">You should see something like below:</span></span>

     ![VSCode](../../images/using-vscode/vscode.png)

   - <span data-ttu-id="4ab7e-132">Klicken Sie auf die Schaltfläche **Installieren** in der PowerShell-Erweiterung für Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   - <span data-ttu-id="4ab7e-133">Nach der Installation ändert sich die Schaltfläche **Installieren** in **Erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-133">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="4ab7e-134">Klicken Sie auf **Erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-134">Click on **Reload**.</span></span>
   - <span data-ttu-id="4ab7e-135">Nachdem VS Code neu geladen wurde, können Sie Bearbeitungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-135">After VSCode has reload, you are ready for editing.</span></span>

<span data-ttu-id="4ab7e-136">Klicken Sie z.B. auf **Datei > Neu**, um eine neue Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-136">For example, to create a new file, click **File->New**.</span></span> <span data-ttu-id="4ab7e-137">Klicken Sie zum Speichern auf **Datei > Speichern**, und geben Sie anschließend einen Dateinamen ein, z.B. `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span> <span data-ttu-id="4ab7e-138">Klicken Sie auf das „x“ neben dem Dateinamen, um die Datei zu schließen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-138">To close the file, click on "x" next to the file name.</span></span> <span data-ttu-id="4ab7e-139">Wählen Sie zum Beenden von VS Code **Datei > Beenden** aus.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-139">To exit VSCode, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="4ab7e-140">Installieren der PowerShell-Erweiterung auf eingeschränkten Systemen</span><span class="sxs-lookup"><span data-stu-id="4ab7e-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="4ab7e-141">Einige Systeme sind so eingerichtet, dass alle Codesignaturen überprüft werden müssen und die Editor-Dienste von PowerShell daher manuell für die Ausführung auf dem System genehmigt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="4ab7e-142">Ein Gruppenrichtlinienupdate, das die Ausführungsrichtlinie ändert, ist eine wahrscheinliche Ursache, wenn Sie die PowerShell-Erweiterung installiert haben, aber einen Fehler wie diesen erhalten:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="4ab7e-143">Öffnen Sie zur manuellen Genehmigung der Editor-Dienste von PowerShell und somit der PowerShell-Erweiterung für VSCode eine PowerShell-Eingabeaufforderung, und führen Sie Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="4ab7e-144">Sie werden gefragt: „Do you want to run software from this untrusted publisher?“ (Möchten Sie Software von diesem nicht vertrauenswürdigen Herausgeber ausführen?).</span><span class="sxs-lookup"><span data-stu-id="4ab7e-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span> <span data-ttu-id="4ab7e-145">Geben Sie `R` ein, um die Datei auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-145">Type `R` to run the file.</span></span> <span data-ttu-id="4ab7e-146">Öffnen Sie dann VS Code, und überprüfen Sie, ob die PowerShell-Erweiterung ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-146">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="4ab7e-147">Wenn Sie noch immer Probleme haben, lassen Sie uns dies auf [GitHub](https://github.com/PowerShell/vscode-powershell/issues) wissen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="4ab7e-148">Auswählen einer Version von PowerShell für die Verwendung mit der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="4ab7e-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="4ab7e-149">Mit einer parallelen Installation von PowerShell Core und Windows PowerShell ist es jetzt möglich, eine bestimmte Version von PowerShell mit der PowerShell-Erweiterung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="4ab7e-150">Verwenden Sie die folgenden Schritte, um die Version auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="4ab7e-151">Öffnen Sie die Befehlspalette (<kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> auf Windows und Linux, <kbd>BEFEHL</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> unter MacOS).</span><span class="sxs-lookup"><span data-stu-id="4ab7e-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="4ab7e-152">Suchen Sie nach „Sitzung“.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-152">Search for "Session".</span></span>
1. <span data-ttu-id="4ab7e-153">Klicken Sie auf „PowerShell“: Zeigen Sie das Menü „Sitzung“ an.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="4ab7e-154">Wählen Sie die Version von PowerShell aus der Liste aus, die Sie verwenden möchten, z. B. „PowerShell Core“.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4ab7e-155">Dieses Feature sucht in ein paar bekannten Pfaden unter verschiedenen Betriebssystemen, um die Installationsspeicherorte von PowerShell zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="4ab7e-156">Wenn Sie PowerShell an einem untypischen Speicherort installiert haben, wird es möglicherweise anfangs nicht im Menü „Sitzung“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="4ab7e-157">Sie können das Menü „Sitzung“ erweitern, indem Sie [Ihre eigenen benutzerdefinierten Pfade hinzufügen](#adding-your-own-powershell-paths-to-the-session-menu), wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="4ab7e-158">Es gibt eine weitere Möglichkeit, um zum Menü „Sitzung“ zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="4ab7e-159">Wenn Sie eine PowerShell-Datei im Editor geöffnet haben, wird unten rechts eine grüne Versionsnummer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="4ab7e-160">Wenn Sie auf diese Versionsnummer klicken, gelangen Sie zum Menü „Sitzung“.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="4ab7e-161">Hinzufügen Ihres eigenen PowerShell-Pfads zum Menü „Sitzung“</span><span class="sxs-lookup"><span data-stu-id="4ab7e-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="4ab7e-162">Sie können dem Menü „Sitzung“ mithilfe einer VS Code-Einstellung andere PowerShell-Pfade für ausführbare Dateien hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-162">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="4ab7e-163">Fügen Sie der Liste `powershell.powerShellAdditionalExePaths` eine Element hinzu, oder erstellen Sie die Liste, wenn sie in Ihrer `settings.json` nicht vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-163">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="4ab7e-164">Jedes Element benötigt:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-164">Each item must have:</span></span>

* <span data-ttu-id="4ab7e-165">`exePath`: Der Pfad zu `pwsh` oder zur ausführbaren `powershell`-Datei.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="4ab7e-166">`versionName`: Der Text, der im Menü „Sitzung“ angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="4ab7e-167">Sie können die PowerShell-Standardversion so festlegen, dass die Einstellung `powershell.powerShellDefaultVersion` verwendet wird, indem Sie diese auf den Text festlegen, der im Menü „Sitzung“ angezeigt wird (auch bekannt als `versionName` in der letzten Einstellung):</span><span class="sxs-lookup"><span data-stu-id="4ab7e-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="4ab7e-168">Wenn Sie diese Einstellung festgelegt haben, starten Sie VS Code neu, oder verwenden Sie die Befehlspalettenaktion „Developer: Fenster erneut laden“, um das aktuelle Fenster neu zu laden.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-168">Once you've set this setting, restart VSCode or use the the "Developer: Reload Window" command pallet action to reload the current VSCode window.</span></span>

<span data-ttu-id="4ab7e-169">Wenn Sie das Menü „Sitzung“ öffnen, werden jetzt Ihre zusätzlichen PowerShell-Versionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-169">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="4ab7e-170">Wenn Sie PowerShell aus der Quelle erstellen, ist dies eine hervorragende Möglichkeit zum Testen Ihres lokalen Builds von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="4ab7e-171">Konfigurationseinstellungen für VS Code</span><span class="sxs-lookup"><span data-stu-id="4ab7e-171">Configuration settings for VSCode</span></span>

<span data-ttu-id="4ab7e-172">Mithilfe der im vorherigen Absatz aufgeführten Schritte können Sie die Konfigurationseinstellungen zu `settings.json` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="4ab7e-173">Die folgenden Konfigurationseinstellungen werden für VS Code empfohlen:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-173">We recommend the following configuration settings for VSCode:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="4ab7e-174">Wenn Sie nicht möchten, dass diese Einstellungen für alle Dateitypen gelten, können Sie in VS Code auch sprachspezifische Konfigurationen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="4ab7e-175">Sie können sprachspezifische Einstellungen erstellen, indem Sie Einstellungen in ein `[<language-name>]`-Feld einfügen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="4ab7e-176">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="4ab7e-177">Weitere Informationen zur Dateicodierung in VS Code finden Sie unter [Informationen zur Dateicodierung](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="4ab7e-177">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="4ab7e-178">Debuggen mit VS Code</span><span class="sxs-lookup"><span data-stu-id="4ab7e-178">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="4ab7e-179">Debuggen außerhalb des Arbeitsbereichs</span><span class="sxs-lookup"><span data-stu-id="4ab7e-179">No-workspace debugging</span></span>

<span data-ttu-id="4ab7e-180">Ab VS Code Version 1.9 können Sie PowerShell-Skripts debuggen, ohne den Ordner öffnen zu müssen, in dem das jeweilige PowerShell-Skript enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-180">As of VSCode version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="4ab7e-181">Öffnen Sie die PowerShell-Skriptdatei über **Datei > Datei öffnen**, legen Sie einen Breakpoint für eine Zeile fest (indem Sie <kbd>F9</kbd> drücken), und drücken Sie dann <kbd>F5</kbd>, um mit dem Debuggen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press <kbd>F9</kbd>) and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="4ab7e-182">Dann wird der Aktionsbereich „Debuggen“ angezeigt, über den Sie den Debugger anhalten und den Debugvorgang ausführen, fortsetzen oder abbrechen können.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="4ab7e-183">Debuggen von Arbeitsbereichen</span><span class="sxs-lookup"><span data-stu-id="4ab7e-183">Workspace debugging</span></span>

<span data-ttu-id="4ab7e-184">Wenn davon die Rede ist, Arbeitsbereiche zu debuggen, ist damit das Debuggen eines Ordners gemeint, den Sie in Visual Studio Code über **Ordner öffnen...** im Menü **Datei** öffnen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span> <span data-ttu-id="4ab7e-185">In der Regel wird dafür der PowerShell-Projektordner und bzw. oder der Stamm des Git-Repositorys geöffnet.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="4ab7e-186">Sie können sogar in diesem Modus damit beginnen, das aktuell ausgewählte PowerShell-Skript zu debuggen, indem Sie <kbd>F5</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="4ab7e-187">Wenn Sie allerdings Arbeitsbereiche debuggen, kann nicht nur für die zu diesem Zeitpunkt geöffnete Datei ein Debugvorgang ausgeführt werden, sondern es können auch mehrere Debugkonfigurationen definiert werden.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="4ab7e-188">Beispielsweise können Sie Konfigurationen zu folgenden Vorgängen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="4ab7e-189">Starten von Pester-Tests im Debugger</span><span class="sxs-lookup"><span data-stu-id="4ab7e-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="4ab7e-190">Starten einer bestimmten Datei mit Argumenten im Debugger</span><span class="sxs-lookup"><span data-stu-id="4ab7e-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="4ab7e-191">Starten einer interaktiven Sitzung im Debugger</span><span class="sxs-lookup"><span data-stu-id="4ab7e-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="4ab7e-192">Anfügen des Debuggers an einen PowerShell-Hostvorgang</span><span class="sxs-lookup"><span data-stu-id="4ab7e-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="4ab7e-193">Führen Sie die folgenden Schritte aus, um eine Konfigurationsdatei für den Debugvorgang zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="4ab7e-194">Öffnen Sie die Ansicht **Debuggen**, indem Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd> drücken (oder <kbd>cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd> unter Mac).</span><span class="sxs-lookup"><span data-stu-id="4ab7e-194">Open the **Debug** view by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> on Mac).</span></span>
  2. <span data-ttu-id="4ab7e-195">Klicken Sie in der Symbolleiste auf das Zahnradsymbol **Konfigurieren**.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-195">Click the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="4ab7e-196">VS Code zeigt folgende Eingabeaufforderung an: **Umgebung auswählen**.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-196">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="4ab7e-197">Wählen Sie **PowerShell** aus.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="4ab7e-198">Nachdem Sie diesen Vorgang ausgeführt haben, erstellt VS Code im Stamm Ihres Arbeitsbereichordners ein Verzeichnis und eine Datei: „.vscode\launch.json“.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-198">When you do this, VSCode creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span> <span data-ttu-id="4ab7e-199">An dieser Stelle wird Ihre Debugkonfiguration gespeichert.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="4ab7e-200">Wenn sich Ihre Dateien in einem Git-Repository befinden, sollten Sie einen Commit für die launch.json-Datei ausführen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span> <span data-ttu-id="4ab7e-201">In dieser Datei sind folgende Inhalte enthalten:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="4ab7e-202">Dies ist ein Beispiel für häufig auftretende Debugszenarios.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-202">This represents the common debug scenarios.</span></span> <span data-ttu-id="4ab7e-203">Wenn Sie diese Datei im Editor öffnen, wird Ihnen jedoch die Schaltfläche **Konfiguration hinzufügen...** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="4ab7e-204">Sie können auf diese Schaltfläche klicken, um weitere Debugkonfigurationen für PowerShell hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-204">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="4ab7e-205">Sie können zum Beispiel die Konfiguration **PowerShell: Launch Script** (PowerShell: Skript starten) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="4ab7e-206">Mithilfe dieser Konfiguration können Sie optionale Argumente für eine bestimmte Datei angeben, die immer gestartet werden soll, wenn Sie <kbd>F5</kbd> drücken. Dabei macht es keinen Unterschied, welche Datei zu diesem Zeitpunkt im Editor aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="4ab7e-207">Nachdem Sie die Debugkonfiguration eingerichtet haben, können Sie auswählen, welche Konfiguration Sie während der Debugsitzung verwenden möchten, indem Sie eine der Debugkonfigurationen aus der Dropdownliste in der Symbolleistenansicht **Debuggen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="4ab7e-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="4ab7e-208">Im Folgenden werden einige Blogbeiträge aufgeführt, die bei den ersten Schritten mit der PowerShell-Erweiterung für Visual Studio Code hilfreich sein können:</span><span class="sxs-lookup"><span data-stu-id="4ab7e-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="4ab7e-209">[PowerShell-Erweiterung][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="4ab7e-210">[Write and debug PowerShell scripts in Visual Studio Code (Schreiben und Debuggen von PowerShell-Skripts in Visual Studio Code)][debug]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="4ab7e-211">[Debugging Visual Studio Code Guidance (Anleitung zum Debuggen in Visual Studio Code)][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="4ab7e-212">[Debugging PowerShell in Visual Studio Code (Debuggen von PowerShell in Visual Studio Code)][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="4ab7e-213">[Get started with PowerShell development in Visual Studio Code (Erste Schritte für die PowerShell-Entwicklung in Visual Studio Code)][getting-started]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="4ab7e-214">[Visual Studio Code editing features for PowerShell development – Part 1 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 1)][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="4ab7e-215">[Visual Studio Code editing features for PowerShell development – Part 2 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 2)][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="4ab7e-216">[Debugging PowerShell script in Visual Studio Code – Part 1 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 1)][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="4ab7e-217">[Debugging PowerShell script in Visual Studio Code – Part 2 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 2)][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="4ab7e-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="4ab7e-218">PowerShell-Erweiterung für VS Code</span><span class="sxs-lookup"><span data-stu-id="4ab7e-218">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="4ab7e-219">Sie finden den Quellcode der PowerShell-Erweiterung auf [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="4ab7e-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
