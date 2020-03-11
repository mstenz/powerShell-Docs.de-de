---
title: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
description: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 16ae228c0d169261b783366a730fd2d5d77d32d6
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279066"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="4f7d3-103">Verwenden von Visual Studio Code für die Entwicklung mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f7d3-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="4f7d3-104">Neben der [PowerShell ISE][ise] wird auch PowerShell in Visual Studio Code (VS Code) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="4f7d3-105">Die ISE wird nicht mit PowerShell Core unterstützt, jedoch wird VS Code für PowerShell Core auf sämtlichen Plattformen unterstützt. Windows, macOS und Linux.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="4f7d3-106">Sie können VS Code unter Windows mit PowerShell-Version 5 verwenden, indem Sie Windows 10 nutzen oder Windows Management Framework 5.1 für ältere Windows-Versionen wie Windows 8.1 installieren.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="4f7d3-107">Weitere Informationen finden Sie unter [Installieren und Konfigurieren von WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span><span class="sxs-lookup"><span data-stu-id="4f7d3-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="4f7d3-108">Prüfen Sie, ob PowerShell auf Ihrem System vorhanden ist, bevor Sie starten.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="4f7d3-109">Aktuelle Workloads unter Windows, macOS und Linux finden Sie unter den folgenden Links:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="4f7d3-110">[Installieren von PowerShell Core unter Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="4f7d3-111">[Installieren von PowerShell Core unter macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="4f7d3-112">[Installieren von PowerShell Core unter Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="4f7d3-113">Herkömmliche Windows PowerShell-Workloads finden Sie unter [Installieren von Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="4f7d3-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="4f7d3-114">Bearbeiten mit VS Code</span><span class="sxs-lookup"><span data-stu-id="4f7d3-114">Editing with VSCode</span></span>

1. <span data-ttu-id="4f7d3-115">Installieren Sie VS Code.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-115">Install VSCode.</span></span> <span data-ttu-id="4f7d3-116">Weitere Informationen finden Sie in der Übersicht [Einrichten von Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="4f7d3-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="4f7d3-117">Dort finden Sie Installationsanweisungen für jede Plattform:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="4f7d3-118">**Linux**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von VS Code unter Linux](https://code.visualstudio.com/docs/setup/linux) aus.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="4f7d3-119">**macOS**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von VS Code unter macOS](https://code.visualstudio.com/docs/setup/mac) aus.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="4f7d3-120">Unter macOS müssen Sie OpenSSL für die PowerShell-Erweiterung installieren, damit diese einwandfrei funktionieren kann.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="4f7d3-121">Dies funktioniert am besten, wenn Sie [Homebrew](https://brew.sh/) installieren und anschließend `brew install openssl` ausführen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="4f7d3-122">VS Code kann jetzt die PowerShell-Erweiterung erfolgreich laden.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="4f7d3-123">**Windows**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von VS Code unter Windows](https://code.visualstudio.com/docs/setup/windows) aus.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="4f7d3-124">Installieren Sie die PowerShell-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="4f7d3-125">Starten Sie VS Code, indem Sie:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="4f7d3-126">**Windows:** `code` in Ihre PowerShell-Sitzung eingeben.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="4f7d3-127">**Linux:** `code` in Ihr Terminal eingeben.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="4f7d3-128">**macOS:** `code` in Ihr Terminal eingeben.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="4f7d3-129">Starten Sie **Quick Open** unter Windows oder Linux, indem Sie <kbd>STRG</kbd>+<kbd>P</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="4f7d3-130">Drücken Sie unter macOS <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="4f7d3-131">Geben Sie in Quick Open `ext install powershell` ein, und drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="4f7d3-132">Dann öffnet sich die Ansicht **Erweiterungen** in der Seitenleiste.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="4f7d3-133">Wählen Sie die PowerShell-Erweiterung für Microsoft aus.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="4f7d3-134">Sie sollten einen VS Code-Bildschirm ähnlich dem folgenden Bild sehen:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](media/using-vscode/vscode.png)

   1. <span data-ttu-id="4f7d3-136">Klicken Sie auf die Schaltfläche **Installieren** in der PowerShell-Erweiterung für Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="4f7d3-137">Nach der Installation ändert sich die Schaltfläche **Installieren** in **Erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="4f7d3-138">Klicken Sie auf **Erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="4f7d3-139">Nachdem VS Code neu geladen wurde, können Sie Bearbeitungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="4f7d3-140">Klicken Sie z. B. auf **Datei > Neu**, um eine neue Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="4f7d3-141">Klicken Sie zum Speichern auf **Datei > Speichern**, und geben Sie anschließend einen Dateinamen ein, z. B. `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="4f7d3-142">Klicken Sie auf `X` neben dem Dateinamen, um die Datei zu schließen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="4f7d3-143">Wählen Sie zum Beenden von VS Code **Datei > Beenden** aus.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="4f7d3-144">Installieren der PowerShell-Erweiterung auf eingeschränkten Systemen</span><span class="sxs-lookup"><span data-stu-id="4f7d3-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="4f7d3-145">Einige Systeme sind so eingerichtet, dass alle Codesignaturen überprüft werden müssen und die Editor-Dienste von PowerShell manuell für die Ausführung auf dem System genehmigt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="4f7d3-146">Ein Gruppenrichtlinienupdate, das die Ausführungsrichtlinie ändert, ist eine wahrscheinliche Ursache, wenn Sie die PowerShell-Erweiterung installiert haben, aber einen Fehler wie diesen erhalten:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="4f7d3-147">Öffnen Sie zur manuellen Genehmigung der Editor-Dienste von PowerShell und der PowerShell-Erweiterung für VSCode eine PowerShell-Eingabeaufforderung, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="4f7d3-148">Sie werden gefragt: **Möchten Sie Software von diesem nicht vertrauenswürdigen Herausgeber ausführen?** .</span><span class="sxs-lookup"><span data-stu-id="4f7d3-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="4f7d3-149">Geben Sie `A` ein, um die Datei auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-149">Type `A` to run the file.</span></span> <span data-ttu-id="4f7d3-150">Öffnen Sie dann VS Code, und überprüfen Sie, ob die PowerShell-Erweiterung ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="4f7d3-151">Wenn Sie noch immer Probleme haben, lassen Sie uns dies auf [GitHub](https://github.com/PowerShell/vscode-powershell/issues) wissen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="4f7d3-152">Auswählen einer Version von PowerShell für die Verwendung mit der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="4f7d3-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="4f7d3-153">Mit einer parallelen Installation von PowerShell Core und Windows PowerShell ist es jetzt möglich, eine bestimmte Version von PowerShell mit der PowerShell-Erweiterung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="4f7d3-154">Verwenden Sie die folgenden Schritte, um die Version auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="4f7d3-155">Öffnen Sie die **Befehlspalette** unter Windows oder Linux mit <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="4f7d3-156">Verwenden Sie unter macOS <kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="4f7d3-157">Suchen Sie nach **Sitzung**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-157">Search for **Session**.</span></span>
1. <span data-ttu-id="4f7d3-158">Klicken Sie auf **PowerShell: Menü „Sitzung“ anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="4f7d3-159">Wählen Sie die Version von PowerShell aus der Liste aus, die Sie verwenden möchten, z. B. **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f7d3-160">Dieses Feature sucht in ein paar bekannten Pfaden unter verschiedenen Betriebssystemen, um die Installationsspeicherorte von PowerShell zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="4f7d3-161">Wenn Sie PowerShell an einem untypischen Speicherort installiert haben, wird es möglicherweise anfangs nicht im Menü „Sitzung“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="4f7d3-162">Sie können das Menü „Sitzung“ erweitern, indem Sie [Ihre eigenen benutzerdefinierten Pfade hinzufügen](#adding-your-own-powershell-paths-to-the-session-menu), wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="4f7d3-163">Es gibt eine weitere Möglichkeit, um zum Menü „Sitzung“ zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="4f7d3-164">Wenn Sie eine PowerShell-Datei im Editor geöffnet haben, wird unten rechts eine grüne Versionsnummer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="4f7d3-165">Wenn Sie auf diese Versionsnummer klicken, gelangen Sie zum Menü „Sitzung“.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="4f7d3-166">Hinzufügen Ihres eigenen PowerShell-Pfads zum Menü „Sitzung“</span><span class="sxs-lookup"><span data-stu-id="4f7d3-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="4f7d3-167">Sie können dem Menü „Sitzung“ mithilfe einer VS Code-Einstellung andere PowerShell-Pfade für ausführbare Dateien hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="4f7d3-168">Fügen Sie der Liste `powershell.powerShellAdditionalExePaths` eine Element hinzu, oder erstellen Sie die Liste, wenn sie in Ihrer `settings.json` nicht vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="4f7d3-169">Jedes Element benötigt:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-169">Each item must have:</span></span>

* <span data-ttu-id="4f7d3-170">`exePath`: Der Pfad zu `pwsh` oder zur ausführbaren `powershell`-Datei.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="4f7d3-171">`versionName`: Der Text, der im Menü „Sitzung“ angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="4f7d3-172">Sie können die PowerShell-Standardversion so festlegen, dass die Einstellung `powershell.powerShellDefaultVersion` verwendet wird, indem Sie diese auf den Text festlegen, der im Menü „Sitzung“ angezeigt wird (auch bekannt als `versionName` in der letzten Einstellung):</span><span class="sxs-lookup"><span data-stu-id="4f7d3-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="4f7d3-173">Nachdem Sie diese Einstellung konfiguriert haben, starten Sie VS Code neu, oder laden Sie das aktuelle VS Code-Fenster über die **Befehlspalette**, und geben Sie **Entwickler: Fenster neu laden** ein.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="4f7d3-174">Wenn Sie das Menü „Sitzung“ öffnen, werden jetzt Ihre zusätzlichen PowerShell-Versionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="4f7d3-175">Wenn Sie PowerShell aus der Quelle erstellen, ist dies eine hervorragende Möglichkeit zum Testen Ihres lokalen Builds von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="4f7d3-176">Konfigurationseinstellungen für VS Code</span><span class="sxs-lookup"><span data-stu-id="4f7d3-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="4f7d3-177">Mithilfe der im vorherigen Absatz aufgeführten Schritte können Sie die Konfigurationseinstellungen zu `settings.json` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="4f7d3-178">Die folgenden Konfigurationseinstellungen werden für VS Code empfohlen:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-178">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="4f7d3-179">Wenn Sie nicht möchten, dass diese Einstellungen für alle Dateitypen gelten, können Sie in VS Code auch sprachspezifische Konfigurationen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="4f7d3-180">Sie können sprachspezifische Einstellungen erstellen, indem Sie Einstellungen in ein `[<language-name>]` einfügen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="4f7d3-181">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="4f7d3-182">Weitere Informationen zur Dateicodierung in VS Code finden Sie unter [Informationen zur Dateicodierung](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="4f7d3-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="4f7d3-183">Debuggen mit VS Code</span><span class="sxs-lookup"><span data-stu-id="4f7d3-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="4f7d3-184">Debuggen außerhalb des Arbeitsbereichs</span><span class="sxs-lookup"><span data-stu-id="4f7d3-184">No-workspace debugging</span></span>

<span data-ttu-id="4f7d3-185">Ab VS Code Version 1.9 können Sie PowerShell-Skripts debuggen, ohne den Ordner öffnen zu müssen, in dem das PowerShell-Skript enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="4f7d3-186">Öffnen Sie die PowerShell-Skriptdatei über **Datei > Datei öffnen**, legen Sie einen Breakpoint für eine Zeile fest, drücken Sie <kbd>F9</kbd> und dann <kbd>F5</kbd>, um mit dem Debuggen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="4f7d3-187">Dann wird der Aktionsbereich „Debuggen“ angezeigt, über den Sie den Debugger anhalten und den Debugvorgang ausführen, fortsetzen oder abbrechen können.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="4f7d3-188">Debuggen von Arbeitsbereichen</span><span class="sxs-lookup"><span data-stu-id="4f7d3-188">Workspace debugging</span></span>

<span data-ttu-id="4f7d3-189">Wenn davon die Rede ist, Arbeitsbereiche zu debuggen, ist damit das Debuggen eines Ordners gemeint, den Sie in Visual Studio Code über **Ordner öffnen...** im Menü **Datei** öffnen. In der Regel wird dafür der PowerShell-Projektordner und bzw. oder der Stamm des Git-Repositorys geöffnet.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="4f7d3-190">Sie können sogar in diesem Modus damit beginnen, das aktuell ausgewählte PowerShell-Skript zu debuggen, indem Sie <kbd>F5</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="4f7d3-191">Wenn Sie allerdings Arbeitsbereiche debuggen, kann nicht nur für die zu diesem Zeitpunkt geöffnete Datei ein Debugvorgang ausgeführt werden, sondern es können auch mehrere Debugkonfigurationen definiert werden.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="4f7d3-192">Beispielsweise können Sie eine Konfiguration zu folgenden Vorgängen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="4f7d3-193">Starten von Pester-Tests im Debugger</span><span class="sxs-lookup"><span data-stu-id="4f7d3-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="4f7d3-194">Starten einer bestimmten Datei mit Argumenten im Debugger</span><span class="sxs-lookup"><span data-stu-id="4f7d3-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="4f7d3-195">Starten einer interaktiven Sitzung im Debugger</span><span class="sxs-lookup"><span data-stu-id="4f7d3-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="4f7d3-196">Anfügen des Debuggers an einen PowerShell-Hostvorgang</span><span class="sxs-lookup"><span data-stu-id="4f7d3-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="4f7d3-197">Führen Sie die folgenden Schritte aus, um eine Konfigurationsdatei für den Debugvorgang zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="4f7d3-198">Öffnen Sie die Ansicht **Debuggen** in Windows oder Linux, indem Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="4f7d3-199">Drücken Sie unter macOS <kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="4f7d3-200">Klicken Sie in der Symbolleiste auf das Zahnradsymbol **Konfigurieren**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="4f7d3-201">VS Code zeigt folgende Eingabeaufforderung an: **Umgebung auswählen**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="4f7d3-202">Wählen Sie **PowerShell** aus.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="4f7d3-203">VS Code erstellt als Ergebnis im Stamm Ihres Arbeitsbereichordners ein Verzeichnis und eine Datei `.vscode\launch.json`.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="4f7d3-204">Hier wird Ihre Debugkonfiguration gespeichert.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="4f7d3-205">Wenn sich Ihre Dateien in einem Git-Repository befinden, sollten Sie einen Commit für die `launch.json`-Datei ausführen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="4f7d3-206">Die `launch.json`-Datei beinhaltet:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="4f7d3-207">Diese Datei ist ein Beispiel für häufig auftretende Debugszenarios.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="4f7d3-208">Wenn Sie diese Datei im Editor öffnen, wird die Schaltfläche **Konfiguration hinzufügen...** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="4f7d3-209">Sie können auf diese Schaltfläche klicken, um weitere Debugkonfigurationen für PowerShell hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="4f7d3-210">Sie können zum Beispiel die Konfiguration **PowerShell: Launch Script** (PowerShell: Skript starten) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="4f7d3-211">Mithilfe dieser Konfiguration können Sie optionale Argumente für eine Datei angeben, die immer gestartet werden soll, wenn Sie <kbd>F5</kbd> drücken. Dabei macht es keinen Unterschied, welche Datei zu diesem Zeitpunkt im Editor aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="4f7d3-212">Nachdem die Debugkonfiguration eingerichtet wurde, können Sie auswählen, welche Konfiguration Sie während einer Debugsitzung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="4f7d3-213">Wählen Sie eine Konfiguration aus der Dropdownliste „Debugkonfiguration“ in der Symbolleiste der Ansicht **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="4f7d3-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="4f7d3-214">Im Folgenden werden einige Blogbeiträge aufgeführt, die bei den ersten Schritten mit der PowerShell-Erweiterung für Visual Studio Code hilfreich sein können:</span><span class="sxs-lookup"><span data-stu-id="4f7d3-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="4f7d3-215">[PowerShell-Erweiterung][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="4f7d3-216">[Write and debug PowerShell scripts in Visual Studio Code (Schreiben und Debuggen von PowerShell-Skripts in Visual Studio Code)][debug]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="4f7d3-217">[Debugging Visual Studio Code Guidance (Anleitung zum Debuggen in Visual Studio Code)][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="4f7d3-218">[Debugging PowerShell in Visual Studio Code (Debuggen von PowerShell in Visual Studio Code)][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="4f7d3-219">[Get started with PowerShell development in Visual Studio Code (Erste Schritte für die PowerShell-Entwicklung in Visual Studio Code)][getting-started]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="4f7d3-220">[Visual Studio Code editing features for PowerShell development – Part 1 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 1)][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="4f7d3-221">[Visual Studio Code editing features for PowerShell development – Part 2 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 2)][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="4f7d3-222">[Debugging PowerShell script in Visual Studio Code – Part 1 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 1)][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="4f7d3-223">[Debugging PowerShell script in Visual Studio Code – Part 2 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 2)][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="4f7d3-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="4f7d3-224">PowerShell-Erweiterung für VS Code</span><span class="sxs-lookup"><span data-stu-id="4f7d3-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="4f7d3-225">Sie finden den Quellcode der PowerShell-Erweiterung auf [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="4f7d3-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
