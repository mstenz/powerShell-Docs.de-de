---
title: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
description: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 86739970b58460bef9686a75bf0604d0605d4888
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082437"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="e549d-103">Verwenden von Visual Studio Code für die Entwicklung mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="e549d-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="e549d-104">[Visual Studio Code](https://code.visualstudio.com/) ist ein plattformübergreifender Skript-Editor (Windows, macOS und Linux) von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e549d-104">[Visual Studio Code](https://code.visualstudio.com/) is a cross-platform (Windows, macOS, and Linux) script editor by Microsoft.</span></span> <span data-ttu-id="e549d-105">In Verbindung mit der [PowerShell-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell) bietet er eine umfassende und interaktive Oberfläche zur Skriptbearbeitung, die das Schreiben zuverlässiger PowerShell-Skripts vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="e549d-105">Together with the [the PowerShell extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span>

<span data-ttu-id="e549d-106">Visual Studio Code mit PowerShell-Erweiterung ist der empfohlene Editor zum Schreiben von PowerShell-Skripts.</span><span class="sxs-lookup"><span data-stu-id="e549d-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>
<span data-ttu-id="e549d-107">Die folgenden PowerShell-Versionen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="e549d-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="e549d-108">PowerShell 7 und höher</span><span class="sxs-lookup"><span data-stu-id="e549d-108">PowerShell 7 and up</span></span>
- <span data-ttu-id="e549d-109">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="e549d-109">PowerShell Core 6</span></span>
- <span data-ttu-id="e549d-110">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e549d-110">Windows PowerShell 5.1</span></span>

<span data-ttu-id="e549d-111">Prüfen Sie, ob PowerShell auf Ihrem System vorhanden ist, bevor Sie starten.</span><span class="sxs-lookup"><span data-stu-id="e549d-111">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="e549d-112">Aktuelle Workloads unter Windows, macOS und Linux finden Sie unter den folgenden Links:</span><span class="sxs-lookup"><span data-stu-id="e549d-112">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="e549d-113">[Installieren von PowerShell Core unter Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="e549d-113">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="e549d-114">[Installieren von PowerShell Core unter macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="e549d-114">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="e549d-115">[Installieren von PowerShell Core unter Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="e549d-115">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="e549d-116">Herkömmliche Windows PowerShell-Workloads finden Sie unter [Installieren von Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="e549d-116">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!NOTE]
> <span data-ttu-id="e549d-117">Visual Studio Code ist nicht identisch mit [Visual Studio](https://visualstudio.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="e549d-117">Visual Studio Code is not the same as [Visual Studio](https://visualstudio.microsoft.com/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e549d-118">Die [Windows PowerShell ISE][ise] ist auch weiterhin für Windows verfügbar. Sie befindet sich jedoch nicht mehr in der aktiven Featureentwicklung und funktioniert nicht mit PowerShell 7 und höher oder mit PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="e549d-118">The [Windows PowerShell ISE][ise] is also still available for Windows, however, it is no longer in active feature development and does not work with PowerShell 7 and up or PowerShell Core 6.</span></span>
> <span data-ttu-id="e549d-119">Als in Windows enthaltene Komponente wird sie weiterhin offiziell mit Sicherheits- und Wartungsfixes hoher Priorität unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e549d-119">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span> <span data-ttu-id="e549d-120">Zurzeit ist es nicht geplant, die ISE aus Windows zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="e549d-120">We currently have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="e549d-121">Bearbeiten von Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e549d-121">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="e549d-122">Installieren Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e549d-122">Install Visual Studio Code.</span></span> <span data-ttu-id="e549d-123">Weitere Informationen finden Sie in der Übersicht [Einrichten von Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="e549d-123">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

    <span data-ttu-id="e549d-124">Dort finden Sie Installationsanweisungen für jede Plattform:</span><span class="sxs-lookup"><span data-stu-id="e549d-124">There are installation instructions for each platform:</span></span>

    - <span data-ttu-id="e549d-125">**Windows**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter Windows](https://code.visualstudio.com/docs/setup/windows) aus.</span><span class="sxs-lookup"><span data-stu-id="e549d-125">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>
    - <span data-ttu-id="e549d-126">**macOS**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter macOS](https://code.visualstudio.com/docs/setup/mac) aus.</span><span class="sxs-lookup"><span data-stu-id="e549d-126">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>
    - <span data-ttu-id="e549d-127">**Linux**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter Linux](https://code.visualstudio.com/docs/setup/linux) aus.</span><span class="sxs-lookup"><span data-stu-id="e549d-127">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>

1. <span data-ttu-id="e549d-128">Installieren Sie die PowerShell-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="e549d-128">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="e549d-129">Starten Sie die Visual Studio Code-App, indem Sie `code` in einer Konsole eingeben bzw. `code-insiders`, falls Sie Visual Studio Code für Insider installiert haben.</span><span class="sxs-lookup"><span data-stu-id="e549d-129">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="e549d-130">Starten Sie **Quick Open** unter Windows oder Linux, indem Sie <kbd>STRG</kbd>+<kbd>P</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="e549d-130">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="e549d-131">Drücken Sie unter macOS <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e549d-131">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="e549d-132">Geben Sie in Quick Open `ext install powershell` ein, und drücken Sie die **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="e549d-132">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="e549d-133">Dann öffnet sich die Ansicht **Erweiterungen** in der Seitenleiste.</span><span class="sxs-lookup"><span data-stu-id="e549d-133">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="e549d-134">Wählen Sie die PowerShell-Erweiterung für Microsoft aus.</span><span class="sxs-lookup"><span data-stu-id="e549d-134">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="e549d-135">Ihnen wird in etwa folgender Visual Studio Code-Bildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="e549d-135">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="e549d-137">Klicken Sie auf die Schaltfläche **Installieren** in der PowerShell-Erweiterung für Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e549d-137">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="e549d-138">Nach der Installation ändert sich die Schaltfläche **Installieren** in **Erneut laden**. Klicken Sie auf **Erneut laden**.</span><span class="sxs-lookup"><span data-stu-id="e549d-138">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="e549d-139">Nachdem Visual Studio Code neu geladen wurde, können Sie Bearbeitungen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="e549d-139">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="e549d-140">Klicken Sie z. B. auf **Datei > Neu**, um eine neue Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e549d-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="e549d-141">Klicken Sie zum Speichern auf **Datei > Speichern**, und geben Sie anschließend einen Dateinamen ein, z. B. `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="e549d-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="e549d-142">Klicken Sie auf `X` neben dem Dateinamen, um die Datei zu schließen.</span><span class="sxs-lookup"><span data-stu-id="e549d-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="e549d-143">Klicken Sie auf **Datei > Beenden**, um Visual Studio Code zu beenden.</span><span class="sxs-lookup"><span data-stu-id="e549d-143">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="e549d-144">Installieren der PowerShell-Erweiterung auf eingeschränkten Systemen</span><span class="sxs-lookup"><span data-stu-id="e549d-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="e549d-145">Einige Systeme sind so eingerichtet, dass alle Codesignaturen überprüft werden müssen und die Editor-Dienste von PowerShell manuell für die Ausführung auf dem System genehmigt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="e549d-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="e549d-146">Ein Gruppenrichtlinienupdate, das die Ausführungsrichtlinie ändert, ist eine wahrscheinliche Ursache, wenn Sie die PowerShell-Erweiterung installiert haben, aber einen Fehler wie diesen erhalten:</span><span class="sxs-lookup"><span data-stu-id="e549d-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="e549d-147">Öffnen Sie eine PowerShell-Eingabeaufforderung, um die Editor-Dienste von PowerShell und die PowerShell-Erweiterung für Visual Studio Code manuell zu genehmigen, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="e549d-147">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="e549d-148">Sie werden gefragt: **Möchten Sie Software von diesem nicht vertrauenswürdigen Herausgeber ausführen?** .</span><span class="sxs-lookup"><span data-stu-id="e549d-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span>
<span data-ttu-id="e549d-149">Geben Sie `A` ein, um die Datei auszuführen.</span><span class="sxs-lookup"><span data-stu-id="e549d-149">Type `A` to run the file.</span></span> <span data-ttu-id="e549d-150">Öffnen Sie dann Visual Studio Code, und überprüfen Sie, ob die PowerShell-Erweiterung ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e549d-150">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="e549d-151">Wenn Sie noch immer Probleme haben, lassen Sie uns dies auf [GitHub](https://github.com/PowerShell/vscode-powershell/issues) wissen.</span><span class="sxs-lookup"><span data-stu-id="e549d-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="e549d-152">Die PowerShell-Erweiterung für Visual Studio Code unterstützt nicht die Ausführung im eingeschränkten Sprachmodus.</span><span class="sxs-lookup"><span data-stu-id="e549d-152">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="e549d-153">Weitere Informationen finden Sie in der [GitHub-Problemverfolgung zur Unterstützung](https://github.com/PowerShell/vscode-powershell/issues/606).</span><span class="sxs-lookup"><span data-stu-id="e549d-153">Please see the [GitHub issue tracking that support](https://github.com/PowerShell/vscode-powershell/issues/606) for more information.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="e549d-154">Verwenden einer älteren Version der PowerShell-Erweiterung für Windows PowerShell v3 und v4</span><span class="sxs-lookup"><span data-stu-id="e549d-154">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="e549d-155">Auch wenn die aktuelle PowerShell-Erweiterung [v3 und v4 nicht mehr unterstützt](https://github.com/PowerShell/vscode-powershell/issues/1310), können Sie weiterhin die letzte Version der Erweiterung verwenden, die diese Unterstützung bot.</span><span class="sxs-lookup"><span data-stu-id="e549d-155">Although the current PowerShell extension [stopped supporting v3 and v4](https://github.com/PowerShell/vscode-powershell/issues/1310), you can still use the last version of the extension that did.</span></span>

> [!NOTE]
> <span data-ttu-id="e549d-156">Für diese ältere Version der Erweiterung werden keine weiteren Fixes bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="e549d-156">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="e549d-157">Sie wird in der vorgelegten Form („AS IS“) bereitgestellt, ist aber für Sie verfügbar, wenn Sie noch Windows PowerShell v3 und Windows PowerShell v4 verwenden.</span><span class="sxs-lookup"><span data-stu-id="e549d-157">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="e549d-158">Öffnen Sie zunächst den Erweiterungsbereich, und suchen Sie nach `PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="e549d-158">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="e549d-159">Klicken Sie dann auf das Zahnrad, und wählen Sie **Andere Version installieren** aus.</span><span class="sxs-lookup"><span data-stu-id="e549d-159">Then click the gear and select **Install another version...**.</span></span>

![Andere Version installieren...](media/using-vscode/install-another-version.png)

<span data-ttu-id="e549d-161">Wählen Sie dann Version **`2020.1.0`** aus.</span><span class="sxs-lookup"><span data-stu-id="e549d-161">Then select the **`2020.1.0`** version.</span></span> <span data-ttu-id="e549d-162">Diese Version der Erweiterung ist die letzte Version, die v3 und v4 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e549d-162">This version of the extension was the last version to support v3 and v4.</span></span>

<span data-ttu-id="e549d-163">Fügen Sie außerdem die folgende Einstellung hinzu, damit Ihre Erweiterungsversion nicht automatisch aktualisiert wird:</span><span class="sxs-lookup"><span data-stu-id="e549d-163">Also, add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="e549d-164">Obwohl diese Lösung auf absehbare Zeit funktioniert, kann Visual Studio Code eine Änderung implementieren, die bei dieser Version der Erweiterung einen Fehler verursacht.</span><span class="sxs-lookup"><span data-stu-id="e549d-164">Although this will work in the forseeable future, Visual Studio Code could implement a change that breaks this version of the extension.</span></span>
<span data-ttu-id="e549d-165">Aus diesem Grund und aufgrund der fehlenden Unterstützung wird eine der beiden folgenden Aktionen dringend empfohlen:</span><span class="sxs-lookup"><span data-stu-id="e549d-165">Because of this, and lack of support, we highly recommend either:</span></span>

- <span data-ttu-id="e549d-166">Herunterladen von PowerShell 7: Dies ist eine parallele Installation zu Windows PowerShell, die mit der PowerShell-Erweiterung am besten funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e549d-166">Downloading PowerShell 7 - which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>
- <span data-ttu-id="e549d-167">Upgrade auf Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e549d-167">Upgrading to Windows PowerShell 5.1</span></span>

<span data-ttu-id="e549d-168">Im Abschnitt [Bearbeiten mit Visual Studio Code](#editing-with-visual-studio-code) in diesem Artikel finden Sie Informationen zu den entsprechenden Installationsorten.</span><span class="sxs-lookup"><span data-stu-id="e549d-168">The [Editing with Visual Studio Code](#editing-with-visual-studio-code) section in this article links to where to install these.</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="e549d-169">Auswählen einer Version von PowerShell für die Verwendung mit der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="e549d-169">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="e549d-170">Mit einer parallelen Installation von PowerShell Core und Windows PowerShell ist es jetzt möglich, eine bestimmte Version von PowerShell mit der PowerShell-Erweiterung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e549d-170">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="e549d-171">Verwenden Sie die folgenden Schritte, um die Version auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="e549d-171">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="e549d-172">Öffnen Sie die **Befehlspalette** unter Windows oder Linux mit <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e549d-172">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="e549d-173">Verwenden Sie unter macOS <kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e549d-173">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="e549d-174">Suchen Sie nach **Sitzung**.</span><span class="sxs-lookup"><span data-stu-id="e549d-174">Search for **Session**.</span></span>
1. <span data-ttu-id="e549d-175">Klicken Sie auf **PowerShell: Menü „Sitzung“ anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="e549d-175">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="e549d-176">Wählen Sie die Version von PowerShell aus der Liste aus, die Sie verwenden möchten, z. B. **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="e549d-176">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e549d-177">Dieses Feature sucht in ein paar bekannten Pfaden unter verschiedenen Betriebssystemen, um die Installationsspeicherorte von PowerShell zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="e549d-177">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="e549d-178">Wenn Sie PowerShell an einem untypischen Speicherort installiert haben, wird es möglicherweise anfangs nicht im Menü „Sitzung“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e549d-178">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="e549d-179">Sie können das Menü „Sitzung“ erweitern, indem Sie [Ihre eigenen benutzerdefinierten Pfade hinzufügen](#adding-your-own-powershell-paths-to-the-session-menu), wie unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e549d-179">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="e549d-180">Es gibt eine weitere Möglichkeit, um zum Menü „Sitzung“ zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="e549d-180">There's another way to get to the session menu.</span></span> <span data-ttu-id="e549d-181">Wenn Sie eine PowerShell-Datei im Editor geöffnet haben, wird unten rechts eine grüne Versionsnummer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e549d-181">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="e549d-182">Wenn Sie auf diese Versionsnummer klicken, gelangen Sie zum Menü „Sitzung“.</span><span class="sxs-lookup"><span data-stu-id="e549d-182">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="e549d-183">Hinzufügen Ihres eigenen PowerShell-Pfads zum Menü „Sitzung“</span><span class="sxs-lookup"><span data-stu-id="e549d-183">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="e549d-184">Sie können dem Sitzungsmenü über die folgende [Visual Studio Code-Einstellung](https://code.visualstudio.com/docs/getstarted/settings) andere PowerShell-Pfade für ausführbare Dateien hinzufügen: `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="e549d-184">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="e549d-185">Fügen Sie der Liste `powershell.powerShellAdditionalExePaths` eine Element hinzu, oder erstellen Sie die Liste, wenn sie in Ihrer `settings.json` nicht vorhanden ist:</span><span class="sxs-lookup"><span data-stu-id="e549d-185">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="e549d-186">Jedes Element benötigt:</span><span class="sxs-lookup"><span data-stu-id="e549d-186">Each item must have:</span></span>

- <span data-ttu-id="e549d-187">`exePath`: Der Pfad zu `pwsh` oder zur ausführbaren `powershell`-Datei.</span><span class="sxs-lookup"><span data-stu-id="e549d-187">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="e549d-188">`versionName`: Der Text, der im Menü „Sitzung“ angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e549d-188">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="e549d-189">Sie können die PowerShell-Standardversion so festlegen, dass die Einstellung `powershell.powerShellDefaultVersion` verwendet wird, indem Sie diese auf den Text festlegen, der im Menü „Sitzung“ angezeigt wird (auch bekannt als `versionName` in der letzten Einstellung):</span><span class="sxs-lookup"><span data-stu-id="e549d-189">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="e549d-190">Nachdem Sie diese Einstellung konfiguriert haben, starten Sie Visual Studio Code neu, oder laden Sie das aktuelle Visual Studio Code-Fenster über die **Befehlspalette**, und geben Sie **Entwickler: Fenster neu laden** ein.</span><span class="sxs-lookup"><span data-stu-id="e549d-190">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="e549d-191">Wenn Sie das Menü „Sitzung“ öffnen, werden jetzt Ihre zusätzlichen PowerShell-Versionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e549d-191">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="e549d-192">Wenn Sie PowerShell aus der Quelle erstellen, ist dies eine hervorragende Möglichkeit zum Testen Ihres lokalen Builds von PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e549d-192">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="e549d-193">Konfigurationseinstellungen für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e549d-193">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="e549d-194">Wenn Sie mit dem Ändern von Einstellungen in Visual Studio Code nicht vertraut sind, empfiehlt es sich, die [Dokumentation zu den Visual Studio Code-Einstellungen](https://code.visualstudio.com/docs/getstarted/settings) zu lesen.</span><span class="sxs-lookup"><span data-stu-id="e549d-194">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend looking at [Visual Studio Code's settings documentation](https://code.visualstudio.com/docs/getstarted/settings).</span></span>

<span data-ttu-id="e549d-195">Mithilfe der im vorherigen Absatz aufgeführten Schritte können Sie die Konfigurationseinstellungen zu `settings.json` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e549d-195">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="e549d-196">Wenn Sie nicht möchten, dass diese Einstellungen für alle Dateitypen gelten, können Sie in Visual Studio Code auch sprachspezifische Konfigurationen vornehmen.</span><span class="sxs-lookup"><span data-stu-id="e549d-196">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="e549d-197">Sie können sprachspezifische Einstellungen erstellen, indem Sie Einstellungen in ein `[<language-name>]` einfügen.</span><span class="sxs-lookup"><span data-stu-id="e549d-197">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="e549d-198">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e549d-198">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="e549d-199">Weitere Informationen zur Dateicodierung in Visual Studio Code finden Sie unter [Informationen zur Dateicodierung](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="e549d-199">For more information about file encoding in Visual Studio Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>
>
> <span data-ttu-id="e549d-200">Weitere Tipps zum Konfigurieren von Visual Studio Code für die PowerShell-Bearbeitung finden Sie auch unter [Replizieren der ISE-Benutzeroberfläche in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md).</span><span class="sxs-lookup"><span data-stu-id="e549d-200">Also check out the [How to replicate the ISE experience in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="e549d-201">Debuggen mit Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e549d-201">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="e549d-202">Debuggen außerhalb des Arbeitsbereichs</span><span class="sxs-lookup"><span data-stu-id="e549d-202">No-workspace debugging</span></span>

<span data-ttu-id="e549d-203">Ab Visual Studio Code Version 1.9 können Sie PowerShell-Skripts debuggen, ohne den Ordner öffnen zu müssen, in dem das PowerShell-Skript enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="e549d-203">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="e549d-204">Öffnen Sie die PowerShell-Skriptdatei über **Datei > Datei öffnen**, legen Sie einen Breakpoint für eine Zeile fest, drücken Sie <kbd>F9</kbd> und dann <kbd>F5</kbd>, um mit dem Debuggen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="e549d-204">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="e549d-205">Dann wird der Aktionsbereich „Debuggen“ angezeigt, über den Sie den Debugger anhalten und den Debugvorgang ausführen, fortsetzen oder abbrechen können.</span><span class="sxs-lookup"><span data-stu-id="e549d-205">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="e549d-206">Debuggen von Arbeitsbereichen</span><span class="sxs-lookup"><span data-stu-id="e549d-206">Workspace debugging</span></span>

<span data-ttu-id="e549d-207">Wenn davon die Rede ist, Arbeitsbereiche zu debuggen, ist damit das Debuggen eines Ordners gemeint, den Sie in Visual Studio Code über **Ordner öffnen...** im Menü **Datei** öffnen. In der Regel wird dafür der PowerShell-Projektordner und bzw. oder der Stamm des Git-Repositorys geöffnet.</span><span class="sxs-lookup"><span data-stu-id="e549d-207">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="e549d-208">Sie können sogar in diesem Modus damit beginnen, das aktuell ausgewählte PowerShell-Skript zu debuggen, indem Sie <kbd>F5</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="e549d-208">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="e549d-209">Wenn Sie allerdings Arbeitsbereiche debuggen, kann nicht nur für die zu diesem Zeitpunkt geöffnete Datei ein Debugvorgang ausgeführt werden, sondern es können auch mehrere Debugkonfigurationen definiert werden.</span><span class="sxs-lookup"><span data-stu-id="e549d-209">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="e549d-210">Dazu kommen wir in Kürze.</span><span class="sxs-lookup"><span data-stu-id="e549d-210">We'll get to those in a moment.</span></span>

<span data-ttu-id="e549d-211">Führen Sie die folgenden Schritte aus, um eine Konfigurationsdatei für den Debugvorgang zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="e549d-211">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="e549d-212">Öffnen Sie die Ansicht **Debuggen** in Windows oder Linux, indem Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd> drücken.</span><span class="sxs-lookup"><span data-stu-id="e549d-212">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="e549d-213">Drücken Sie unter macOS <kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e549d-213">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="e549d-214">Klicken Sie auf den Link zu Erstellen einer Datei „launch.json“.</span><span class="sxs-lookup"><span data-stu-id="e549d-214">Click the "create a launch.json file" link.</span></span>
  1. <span data-ttu-id="e549d-215">Visual Studio Code zeigt folgende Eingabeaufforderung an: **Umgebung auswählen**.</span><span class="sxs-lookup"><span data-stu-id="e549d-215">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="e549d-216">Wählen Sie **PowerShell** aus.</span><span class="sxs-lookup"><span data-stu-id="e549d-216">Choose **PowerShell**.</span></span>
  1. <span data-ttu-id="e549d-217">Wählen Sie abschließend den Debugtyp aus, den Sie verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="e549d-217">Lastly, choose the type of debugging you'd like to use:</span></span>

- <span data-ttu-id="e549d-218">**Aktuelle Datei starten**: Starten und Debuggen der Datei im aktuell aktiven Editor-Fenster</span><span class="sxs-lookup"><span data-stu-id="e549d-218">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
- <span data-ttu-id="e549d-219">**Skript starten**: Starten und Debuggen der angegebenen Datei oder des angegebenen Befehls</span><span class="sxs-lookup"><span data-stu-id="e549d-219">**Launch Script** - Launch and debug the specified file or command</span></span>
- <span data-ttu-id="e549d-220">**Interaktive Sitzung**: Debuggen von Befehlen, die über die integrierte Konsole ausgeführt werden</span><span class="sxs-lookup"><span data-stu-id="e549d-220">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
- <span data-ttu-id="e549d-221">**Anfügen**: Anfügen des Debuggers an einen ausgeführten PowerShell-Hostvorgang</span><span class="sxs-lookup"><span data-stu-id="e549d-221">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="e549d-222">Als Ergebnis erstellt Visual Studio Code im Stamm Ihres Arbeitsbereichsordners ein Verzeichnis und eine Datei `.vscode\launch.json`.</span><span class="sxs-lookup"><span data-stu-id="e549d-222">The result is that Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="e549d-223">Hier wird Ihre Debugkonfiguration gespeichert.</span><span class="sxs-lookup"><span data-stu-id="e549d-223">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="e549d-224">Wenn sich Ihre Dateien in einem Git-Repository befinden, sollten Sie einen Commit für die `launch.json`-Datei ausführen.</span><span class="sxs-lookup"><span data-stu-id="e549d-224">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="e549d-225">Die `launch.json`-Datei beinhaltet:</span><span class="sxs-lookup"><span data-stu-id="e549d-225">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="e549d-226">Diese Datei ist ein Beispiel für häufig auftretende Debugszenarios.</span><span class="sxs-lookup"><span data-stu-id="e549d-226">This file represents the common debug scenarios.</span></span> <span data-ttu-id="e549d-227">Wenn Sie diese Datei im Editor öffnen, wird die Schaltfläche **Konfiguration hinzufügen...** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e549d-227">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="e549d-228">Sie können auf diese Schaltfläche klicken, um weitere Debugkonfigurationen für PowerShell hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e549d-228">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="e549d-229">Sie können zum Beispiel die Konfiguration **PowerShell: Launch Script** (PowerShell: Skript starten) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e549d-229">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="e549d-230">Mithilfe dieser Konfiguration können Sie optionale Argumente für eine Datei angeben, die immer gestartet werden soll, wenn Sie <kbd>F5</kbd> drücken. Dabei macht es keinen Unterschied, welche Datei zu diesem Zeitpunkt im Editor aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="e549d-230">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="e549d-231">Nachdem die Debugkonfiguration eingerichtet wurde, können Sie auswählen, welche Konfiguration Sie während einer Debugsitzung verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="e549d-231">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="e549d-232">Wählen Sie eine Konfiguration aus der Dropdownliste „Debugkonfiguration“ in der Symbolleiste der Ansicht **Debuggen**.</span><span class="sxs-lookup"><span data-stu-id="e549d-232">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="e549d-233">Im Folgenden werden einige Blogbeiträge aufgeführt, die bei den ersten Schritten mit der PowerShell-Erweiterung für Visual Studio Code hilfreich sein können:</span><span class="sxs-lookup"><span data-stu-id="e549d-233">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="e549d-234">[PowerShell-Erweiterung][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="e549d-234">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="e549d-235">[Write and debug PowerShell scripts in Visual Studio Code (Schreiben und Debuggen von PowerShell-Skripts in Visual Studio Code)][debug]</span><span class="sxs-lookup"><span data-stu-id="e549d-235">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="e549d-236">[Debugging Visual Studio Code Guidance (Anleitung zum Debuggen in Visual Studio Code)][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="e549d-236">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="e549d-237">[Debugging PowerShell in Visual Studio Code (Debuggen von PowerShell in Visual Studio Code)][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="e549d-237">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="e549d-238">[Get started with PowerShell development in Visual Studio Code (Erste Schritte für die PowerShell-Entwicklung in Visual Studio Code)][getting-started]</span><span class="sxs-lookup"><span data-stu-id="e549d-238">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="e549d-239">[Visual Studio Code editing features for PowerShell development – Part 1 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 1)][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="e549d-239">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="e549d-240">[Visual Studio Code editing features for PowerShell development – Part 2 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 2)][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="e549d-240">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="e549d-241">[Debugging PowerShell script in Visual Studio Code – Part 1 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 1)][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="e549d-241">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="e549d-242">[Debugging PowerShell script in Visual Studio Code – Part 2 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 2)][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="e549d-242">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="e549d-243">PowerShell-Erweiterung für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e549d-243">PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="e549d-244">Sie finden den Quellcode der PowerShell-Erweiterung auf [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="e549d-244">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>

<span data-ttu-id="e549d-245">Wenn Sie einen Beitrag leisten möchten, sind Pull Requests sehr willkommen.</span><span class="sxs-lookup"><span data-stu-id="e549d-245">If you're interested in contributing, Pull Request are greatly appreciated.</span></span> <span data-ttu-id="e549d-246">Befolgen Sie die [Entwicklerdokumentation auf GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md), um loszulegen.</span><span class="sxs-lookup"><span data-stu-id="e549d-246">Follow along with the [developer documentation on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) to get started.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="e549d-247">Problembehandlung der PowerShell-Erweiterung für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e549d-247">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="e549d-248">Wenn bei der Verwendung von Visual Studio Code für die Entwicklung von PowerShell-Skripts Probleme auftreten, sehen Sie sich den [Leitfaden zur Problembehandlung auf GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md) an.</span><span class="sxs-lookup"><span data-stu-id="e549d-248">If you experience any issues using Visual Studio Code for PowerShell script development, please take a look at the [troubleshooting guide on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span></span>
