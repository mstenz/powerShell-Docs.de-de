---
title: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
description: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809276"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="79de1-103">Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen</span><span class="sxs-lookup"><span data-stu-id="79de1-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="79de1-104">Wenn Sie mit der ISE vertraut sind, wissen Sie sicher, dass Sie `psedit file.ps1` über die integrierte Konsole ausführen konnten, um Dateien – lokal oder remote – direkt in der ISE zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="79de1-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="79de1-105">Dieses Feature ist auch in der PowerShell-Erweiterung für VSCode verfügbar.</span><span class="sxs-lookup"><span data-stu-id="79de1-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="79de1-106">In diesem Leitfaden erfahren Sie, wie Sie dabei vorgehen.</span><span class="sxs-lookup"><span data-stu-id="79de1-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79de1-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="79de1-107">Prerequisites</span></span>

<span data-ttu-id="79de1-108">Dieses Handbuch setzt Folgendes voraus:</span><span class="sxs-lookup"><span data-stu-id="79de1-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="79de1-109">Eine Remoteressource (z.B. eine VM oder einen Container), auf die Sie Zugriff haben</span><span class="sxs-lookup"><span data-stu-id="79de1-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="79de1-110">Ausführung von PowerShell auf dieser Ressource und dem Hostcomputer</span><span class="sxs-lookup"><span data-stu-id="79de1-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="79de1-111">VSCode und PowerShell-Erweiterung für VSCode</span><span class="sxs-lookup"><span data-stu-id="79de1-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="79de1-112">Dieses Feature funktioniert unter Windows PowerShell und PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="79de1-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="79de1-113">Dieses Feature funktioniert auch beim Herstellen der Verbindung mit einem Remotecomputer über WinRM, PowerShell Direct oder SSH.</span><span class="sxs-lookup"><span data-stu-id="79de1-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="79de1-114">Wenn Sie SSH verwenden möchten, aber Windows verwenden, informieren Sie sich über die [Win32-Version von SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="79de1-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79de1-115">Die Befehle `Open-EditorFile` und `psedit` funktionieren nur in der **integrierten PowerShell-Konsole**, die von der PowerShell-Erweiterung für VSCode erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="79de1-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="79de1-116">Anwendungsbeispiele</span><span class="sxs-lookup"><span data-stu-id="79de1-116">Usage examples</span></span>

<span data-ttu-id="79de1-117">Diese Beispiele veranschaulichen das Remotebearbeiten und -debuggen von einem MacBook Pro aus auf einer in Azure ausgeführten Ubuntu-VM.</span><span class="sxs-lookup"><span data-stu-id="79de1-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="79de1-118">Der Prozess läuft unter Windows identisch ab.</span><span class="sxs-lookup"><span data-stu-id="79de1-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="79de1-119">Lokale Dateibearbeitung mit Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="79de1-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="79de1-120">Nach Starten der PowerShell-Erweiterung für VSCode und Öffnen der integrierten PowerShell-Konsole können wir `Open-EditorFile foo.ps1` oder `psedit foo.ps1` eingeben, um die lokale Datei „foo.ps1“ direkt im Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="79de1-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Bearbeitung von „foo.ps1“ in Open-EditorFile funktioniert lokal](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="79de1-122">Die Datei `foo.ps1` muss bereits vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="79de1-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="79de1-123">Von dort aus können wir:</span><span class="sxs-lookup"><span data-stu-id="79de1-123">From there, we can:</span></span>

- <span data-ttu-id="79de1-124">Fügen Sie Haltepunkte zum Bundsteg hinzu.</span><span class="sxs-lookup"><span data-stu-id="79de1-124">Add breakpoints to the gutter</span></span>

  ![Hinzufügen von Haltepunkten zum Bundsteg](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="79de1-126">Drücken Sie F5, um das PowerShell-Skript zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="79de1-126">Hit F5 to debug the PowerShell script.</span></span>

  ![Debuggen des lokalen PowerShell-Skripts](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="79de1-128">Sie können während des Debuggens mit der Debugging-Konsole interagieren, im Bereich auf der linken Seite die Variablen überprüfen und alle anderen standardmäßigen Debuggingtools verwenden.</span><span class="sxs-lookup"><span data-stu-id="79de1-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="79de1-129">Remotedateibearbeitung mit Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="79de1-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="79de1-130">Jetzt wenden wir uns Remotedateibearbeitung und -debuggen zu.</span><span class="sxs-lookup"><span data-stu-id="79de1-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="79de1-131">Die Schritte sind nahezu identisch, wir müssen nur zuerst eines tun: unsere PowerShell-Sitzung auf dem Remoteserver starten.</span><span class="sxs-lookup"><span data-stu-id="79de1-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="79de1-132">Hierfür gibt es ein Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79de1-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="79de1-133">Es heißt `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="79de1-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="79de1-134">Die vereinfachte Erläuterung des Cmdlets ist:</span><span class="sxs-lookup"><span data-stu-id="79de1-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="79de1-135">`Enter-PSSession -ComputerName foo` startet eine-Sitzung über WinRM</span><span class="sxs-lookup"><span data-stu-id="79de1-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="79de1-136">`Enter-PSSession -ContainerId foo` und `Enter-PSSession -VmId foo` starten eine Sitzung über PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="79de1-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="79de1-137">`Enter-PSSession -HostName foo` startet eine-Sitzung über SSH</span><span class="sxs-lookup"><span data-stu-id="79de1-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="79de1-138">Weitere Informationen finden Sie in der Dokumentation zu [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="79de1-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="79de1-139">Da wir von macOS aus auf eine Ubuntu-VM in Azure zugreifen, verwenden wir SSH für das Remoting.</span><span class="sxs-lookup"><span data-stu-id="79de1-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="79de1-140">Führen Sie zunächst in der integrierten Konsole `Enter-PSSession` aus.</span><span class="sxs-lookup"><span data-stu-id="79de1-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="79de1-141">Sie sind mit der Remotesitzung verbunden, wenn links neben Ihrer Eingabeaufforderung `[<hostname>]` angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="79de1-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![Der Aufruf von Enter-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="79de1-143">Jetzt können wir dieselben Schritte ausführen wie beim Bearbeiten eines lokalen Skripts.</span><span class="sxs-lookup"><span data-stu-id="79de1-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="79de1-144">Führen Sie `Open-EditorFile test.ps1` oder `psedit test.ps1` aus, um die Remotedatei `test.ps1` zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="79de1-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Datei „Open-EditorFile the test.ps1“](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="79de1-146">Bearbeiten Sie die Datei bzw. / legen Sie Haltepunkte fest.</span><span class="sxs-lookup"><span data-stu-id="79de1-146">Edit the file/set breakpoints</span></span>

   ![Bearbeiten und Festlegen von Haltepunkten](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="79de1-148">Beginnen Sie mit dem Debuggen (F5) der Remotedatei.</span><span class="sxs-lookup"><span data-stu-id="79de1-148">Start debugging (F5) the remote file</span></span>

   ![Debuggen der Remotedatei](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="79de1-150">Zur Lösung eventuell noch auftretender Probleme steht Ihnen das [GitHub-Repository](https://github.com/powershell/vscode-powershell) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="79de1-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
