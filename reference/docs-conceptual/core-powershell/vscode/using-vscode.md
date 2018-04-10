# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="16c57-101">Verwenden von Visual Studio Code für die Entwicklung mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="16c57-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="16c57-102">Neben der [PowerShell ISE][ise] wird auch PowerShell in Visual Studio Code unterstützt.</span><span class="sxs-lookup"><span data-stu-id="16c57-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="16c57-103">Außerdem wird die PowerShell ISE zwar nicht mit PowerShell Core unterstützt, jedoch wird Visual Studio Code für PowerShell Core auf sämtlichen Plattformen (Windows, macOS und Linux) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="16c57-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="16c57-104">Sie können Visual Studio Code unter Windows mit PowerShell Version 5 verwenden, wenn Sie Windows 10 verwenden oder für ältere Windows-Versionen (z.B. Windows 8.1) [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installieren.</span><span class="sxs-lookup"><span data-stu-id="16c57-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="16c57-105">Prüfen Sie, ob PowerShell auf Ihrem System vorhanden ist, bevor Sie das Programm starten.</span><span class="sxs-lookup"><span data-stu-id="16c57-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="16c57-106">Aktuelle Workloads unter Windows, macOS und Linux finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="16c57-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="16c57-107">[Installing PowerShell Core on macOS and Linux (Installieren von PowerShell Core unter macOS und Linux)][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="16c57-107">[Installing PowerShell Core on macOS and Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="16c57-108">[Installing PowerShell Core on Windows (Installieren von PowerShell Core unter Windows)][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="16c57-108">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="16c57-109">Herkömmliche Windows PowerShell-Workloads finden Sie unter [Installieren von Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="16c57-109">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="16c57-110">Bearbeiten von Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="16c57-110">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="16c57-111">1. Installieren von Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="16c57-111">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="16c57-112">**Linux:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on Linux (Ausführen von VS Code unter Linux)](https://code.visualstudio.com/docs/setup/linux) aus.</span><span class="sxs-lookup"><span data-stu-id="16c57-112">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="16c57-113">**macOS:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on macOS (Ausführen von VS Code unter macOS)](https://code.visualstudio.com/docs/setup/mac) aus.</span><span class="sxs-lookup"><span data-stu-id="16c57-113">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="16c57-114">Unter macOS müssen Sie OpenSSL für die PowerShell-Erweiterung installieren, damit diese einwandfrei funktionieren kann.</span><span class="sxs-lookup"><span data-stu-id="16c57-114">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="16c57-115">Dies funktioniert am besten, wenn Sie [Homebrew](http://brew.sh/) installieren und anschließend `brew install openssl` ausführen.</span><span class="sxs-lookup"><span data-stu-id="16c57-115">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="16c57-116">Die PowerShell-Erweiterung sollte nun einwandfrei geladen werden können.</span><span class="sxs-lookup"><span data-stu-id="16c57-116">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="16c57-117">**Windows:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on Windows (Ausführen von VS Code unter Windows)](https://code.visualstudio.com/docs/setup/windows) aus.</span><span class="sxs-lookup"><span data-stu-id="16c57-117">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="16c57-118">2. Installieren der PowerShell-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="16c57-118">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="16c57-119">Starten Sie die Visual Studio Code-App, indem Sie:</span><span class="sxs-lookup"><span data-stu-id="16c57-119">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="16c57-120">**Windows:** `code` in Ihre PowerShell-Sitzung eingeben.</span><span class="sxs-lookup"><span data-stu-id="16c57-120">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="16c57-121">**Linux:** `code` in Ihr Terminal eingeben.</span><span class="sxs-lookup"><span data-stu-id="16c57-121">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="16c57-122">**macOS:** `code` in Ihr Terminal eingeben.</span><span class="sxs-lookup"><span data-stu-id="16c57-122">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="16c57-123">Starten Sie **Quick Open**, indem Sie **STRG+P** (**cmd+P** unter Mac) drücken.</span><span class="sxs-lookup"><span data-stu-id="16c57-123">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="16c57-124">Geben Sie in Quick Open `ext install powershell` ein, und drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="16c57-124">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="16c57-125">Dann öffnet sich die Ansicht **Erweiterungen** in der Seitenleiste.</span><span class="sxs-lookup"><span data-stu-id="16c57-125">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="16c57-126">Wählen Sie die PowerShell-Erweiterung für Microsoft aus.</span><span class="sxs-lookup"><span data-stu-id="16c57-126">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="16c57-127">Anschließend wird eine Ansicht angezeigt, die der Folgenden ähnlich ist:</span><span class="sxs-lookup"><span data-stu-id="16c57-127">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="16c57-129">Klicken Sie auf die Schaltfläche **Installieren** in der PowerShell-Erweiterung für Microsoft.</span><span class="sxs-lookup"><span data-stu-id="16c57-129">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="16c57-130">Nach der Installation ändert sich die Schaltfläche **Installieren** in **Erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="16c57-130">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="16c57-131">Klicken Sie auf **Erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="16c57-131">Click on **Reload**.</span></span>
- <span data-ttu-id="16c57-132">Nachdem Visual Studio Code neu geladen wurde, können Sie Bearbeitungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="16c57-132">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="16c57-133">Klicken Sie z.B. auf **Datei > Neu**, um eine neue Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="16c57-133">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="16c57-134">Klicken Sie zum Speichern auf **Datei > Speichern**, und geben Sie anschließend einen Dateinamen ein, z.B. `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="16c57-134">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="16c57-135">Klicken Sie auf das „x“ neben dem Dateinamen, um die Datei zu schließen.</span><span class="sxs-lookup"><span data-stu-id="16c57-135">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="16c57-136">Klicken Sie auf **Datei > Beenden**, um Visual Studio Code zu beenden.</span><span class="sxs-lookup"><span data-stu-id="16c57-136">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="16c57-137">Verwenden einer bestimmten installierten PowerShell-Version</span><span class="sxs-lookup"><span data-stu-id="16c57-137">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="16c57-138">Wenn Sie eine bestimmte PowerShell-Installation mit Visual Studio Code verwenden möchten, müssen Sie der Datei mit den Benutzereinstellungen eine neue Variable hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="16c57-138">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="16c57-139">Klicken Sie auf **Datei > Voreinstellungen > Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="16c57-139">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="16c57-140">Anschließend werden zwei Editorbereiche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="16c57-140">Two editor panes will appear.</span></span>
   <span data-ttu-id="16c57-141">Fügen Sie die nachfolgende Einstellung im Bereich rechts (`settings.json`) abhängig von Ihrem Betriebssystem zwischen den geschweiften Klammern (`{` und `}`) ein, und ersetzen Sie *<version>* durch die installierte PowerShell-Version:</span><span class="sxs-lookup"><span data-stu-id="16c57-141">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="16c57-142">Ersetzen Sie die Einstellung durch den Pfad zu der gewünschten ausführbaren PowerShell-Datei.</span><span class="sxs-lookup"><span data-stu-id="16c57-142">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="16c57-143">Speichern Sie die Datei mit den Einstellungen, und starten Sie Visual Studio Code neu.</span><span class="sxs-lookup"><span data-stu-id="16c57-143">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="16c57-144">Konfigurationseinstellungen für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="16c57-144">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="16c57-145">Mithilfe der im vorherigen Absatz aufgeführten Schritte können Sie die Konfigurationseinstellungen zu `settings.json` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="16c57-145">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="16c57-146">Die folgenden Konfigurationseinstellungen werden für Visual Studio Code empfohlen:</span><span class="sxs-lookup"><span data-stu-id="16c57-146">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="16c57-147">Debuggen mit Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="16c57-147">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="16c57-148">Debuggen außerhalb des Arbeitsbereichs</span><span class="sxs-lookup"><span data-stu-id="16c57-148">No-workspace debugging</span></span>

<span data-ttu-id="16c57-149">Ab Visual Studio Code Version 1.9 können Sie PowerShell-Skripts debuggen, ohne den Ordner öffnen zu müssen, in dem das jeweilige Skript enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="16c57-149">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="16c57-150">Öffnen Sie einfach die PowerShell-Skriptdatei über **Datei > Datei öffnen...**, legen Sie auf einer Zeile einen Breakpoint fest (indem Sie F9 drücken), und drücken Sie anschließend F5, um mit dem Debuggen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="16c57-150">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="16c57-151">Dann wird der Aktionsbereich „Debuggen“ angezeigt, über den Sie den Debugger anhalten und den Debugvorgang ausführen, fortsetzen oder abbrechen können.</span><span class="sxs-lookup"><span data-stu-id="16c57-151">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="16c57-152">Debuggen von Arbeitsbereichen</span><span class="sxs-lookup"><span data-stu-id="16c57-152">Workspace debugging</span></span>

<span data-ttu-id="16c57-153">Wenn davon die Rede ist, Arbeitsbereiche zu debuggen, ist damit das Debuggen eines Ordners gemeint, den Sie in Visual Studio Code über **Ordner öffnen...** im Menü **Datei** öffnen.</span><span class="sxs-lookup"><span data-stu-id="16c57-153">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="16c57-154">In der Regel wird dafür der PowerShell-Projektordner und bzw. oder der Stamm des Git-Repositorys geöffnet.</span><span class="sxs-lookup"><span data-stu-id="16c57-154">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="16c57-155">Sie können sogar in diesem Modus damit beginnen, das zu diesem Zeitpunkt ausgewählte PowerShell-Skript zu debuggen, indem Sie F5 drücken.</span><span class="sxs-lookup"><span data-stu-id="16c57-155">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="16c57-156">Wenn Sie allerdings Arbeitsbereiche debuggen, kann nicht nur für die zu diesem Zeitpunkt geöffnete Datei ein Debugvorgang ausgeführt werden, sondern es können auch mehrere Debugkonfigurationen definiert werden.</span><span class="sxs-lookup"><span data-stu-id="16c57-156">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="16c57-157">Beispielsweise können Sie Konfigurationen zu folgenden Vorgängen hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="16c57-157">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="16c57-158">Starten von Pester-Tests im Debugger</span><span class="sxs-lookup"><span data-stu-id="16c57-158">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="16c57-159">Starten einer bestimmten Datei mit Argumenten im Debugger</span><span class="sxs-lookup"><span data-stu-id="16c57-159">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="16c57-160">Starten einer interaktiven Sitzung im Debugger</span><span class="sxs-lookup"><span data-stu-id="16c57-160">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="16c57-161">Anfügen des Debuggers an einen PowerShell-Hostvorgang</span><span class="sxs-lookup"><span data-stu-id="16c57-161">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="16c57-162">Führen Sie die folgenden Schritte aus, um eine Konfigurationsdatei für den Debugvorgang zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="16c57-162">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="16c57-163">Öffnen Sie die Ansicht **Debuggen**, indem Sie **STRG+UMSCHALT+D** drücken (oder **cmd+UMSCHALT+D** unter Mac).</span><span class="sxs-lookup"><span data-stu-id="16c57-163">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="16c57-164">Klicken Sie in der Symbolleiste auf das Zahnradsymbol **Konfigurieren**.</span><span class="sxs-lookup"><span data-stu-id="16c57-164">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="16c57-165">Visual Studio Code zeigt folgende Eingabeaufforderung an: **Umgebung auswählen**.</span><span class="sxs-lookup"><span data-stu-id="16c57-165">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="16c57-166">Wählen Sie **PowerShell** aus.</span><span class="sxs-lookup"><span data-stu-id="16c57-166">Choose **PowerShell**.</span></span>

   <span data-ttu-id="16c57-167">Nachdem Sie diesen Vorgang ausgeführt haben, erstellt Visual Studio Code im Stamm Ihres Arbeitsbereichordners ein Verzeichnis und eine Datei: „.vscode\launch.json“.</span><span class="sxs-lookup"><span data-stu-id="16c57-167">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="16c57-168">An dieser Stelle wird Ihre Debugkonfiguration gespeichert.</span><span class="sxs-lookup"><span data-stu-id="16c57-168">This is where your debug configuration is stored.</span></span> <span data-ttu-id="16c57-169">Wenn sich Ihre Dateien in einem Git-Repository befinden, sollten Sie einen Commit für die launch.json-Datei ausführen.</span><span class="sxs-lookup"><span data-stu-id="16c57-169">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="16c57-170">In dieser Datei sind folgende Inhalte enthalten:</span><span class="sxs-lookup"><span data-stu-id="16c57-170">The contents of the launch.json file are:</span></span>

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

<span data-ttu-id="16c57-171">Dies ist ein Beispiel für häufig auftretende Debugszenarios.</span><span class="sxs-lookup"><span data-stu-id="16c57-171">This represents the common debug scenarios.</span></span>
<span data-ttu-id="16c57-172">Wenn Sie diese Datei im Editor öffnen, wird Ihnen jedoch die Schaltfläche **Konfiguration hinzufügen...** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="16c57-172">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="16c57-173">Sie können auf diese Schaltfläche klicken, um weitere Debugkonfigurationen für PowerShell hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="16c57-173">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="16c57-174">Sie können zum Beispiel die Konfiguration **PowerShell: Launch Script** (PowerShell: Skript starten) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="16c57-174">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="16c57-175">Mithilfe dieser Konfiguration können Sie optionale Argumente für eine bestimmte Datei angeben, die immer gestartet werden soll, wenn Sie F5 drücken. Dabei macht es keinen Unterschied, welche Datei zu diesem Zeitpunkt im Editor aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="16c57-175">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="16c57-176">Nachdem Sie die Debugkonfiguration eingerichtet haben, können Sie auswählen, welche Konfiguration Sie während der Debugsitzung verwenden möchten, indem Sie eine der Debugkonfigurationen aus der Dropdownliste in der Symbolleistenansicht **Debuggen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="16c57-176">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="16c57-177">Im Folgenden werden einige Blogbeiträge aufgeführt, die hilfreich für die ersten Schritte mit der PowerShell-Erweiterung für Visual Studio Code sein können:</span><span class="sxs-lookup"><span data-stu-id="16c57-177">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="16c57-178">Visual Studio Code: [PowerShell Extension (PowerShell-Erweiterung)][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="16c57-178">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="16c57-179">[Write and debug PowerShell scripts in Visual Studio Code (Schreiben und Debuggen von PowerShell-Skripts in Visual Studio Code)][debug]</span><span class="sxs-lookup"><span data-stu-id="16c57-179">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="16c57-180">[Debugging Visual Studio Code Guidance (Debuggen der Visual Studio Code-Anleitung)][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="16c57-180">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="16c57-181">[Debugging PowerShell in Visual Studio Code (Debuggen von PowerShell in Visual Studio Code)][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="16c57-181">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="16c57-182">[Get started with PowerShell development in Visual Studio Code (Erste Schritte für die PowerShell-Entwicklung in Visual Studio Code)][getting-started]</span><span class="sxs-lookup"><span data-stu-id="16c57-182">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="16c57-183">[Visual Studio Code editing features for PowerShell development – Part 1 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 1)][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="16c57-183">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="16c57-184">[Visual Studio Code editing features for PowerShell development – Part 2 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 2)][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="16c57-184">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="16c57-185">[Debugging PowerShell script in Visual Studio Code – Part 1 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 1)][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="16c57-185">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="16c57-186">[Debugging PowerShell script in Visual Studio Code – Part 2 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 2)][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="16c57-186">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="16c57-187">PowerShell-Erweiterung für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="16c57-187">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="16c57-188">Sie finden den Quellcode der PowerShell-Erweiterung auf [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="16c57-188">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>