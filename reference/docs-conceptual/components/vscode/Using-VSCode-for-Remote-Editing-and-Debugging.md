---
title: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
description: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086669"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="a92ce-103">Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen</span><span class="sxs-lookup"><span data-stu-id="a92ce-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="a92ce-104">Wenn Sie mit der ISE vertraut waren, erinnern Sie sich vielleicht daran, dass Sie `psedit file.ps1` über die integrierte Konsole ausführen konnten, um Dateien – lokal oder remote – direkt in der ISE zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a92ce-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="a92ce-105">Dieses Feature ist auch in der PowerShell-Erweiterung für VSCode verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a92ce-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="a92ce-106">In diesem Handbuch erfahren Sie, Sie dabei vorgehen.</span><span class="sxs-lookup"><span data-stu-id="a92ce-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a92ce-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="a92ce-107">Prerequisites</span></span>

<span data-ttu-id="a92ce-108">Dieses Handbuch setzt Folgendes voraus:</span><span class="sxs-lookup"><span data-stu-id="a92ce-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="a92ce-109">eine Remoteressource (z.B. eine VM, einen Container), auf die Sie Zugriff haben</span><span class="sxs-lookup"><span data-stu-id="a92ce-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="a92ce-110">Ausführung von PowerShell auf dieser Ressource und dem Hostcomputer</span><span class="sxs-lookup"><span data-stu-id="a92ce-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="a92ce-111">VSCode und PowerShell-Erweiterung für VSCode</span><span class="sxs-lookup"><span data-stu-id="a92ce-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="a92ce-112">Dieses Feature funktioniert unter Windows PowerShell und PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="a92ce-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="a92ce-113">Dieses Feature funktioniert auch beim Herstellen der Verbindung mit einem Remotecomputer über WinRM, PowerShell Direct oder SSH.</span><span class="sxs-lookup"><span data-stu-id="a92ce-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="a92ce-114">Wenn Sie SSH verwenden möchten, aber Windows verwenden, informieren Sie sich über die [Win32-Version von SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="a92ce-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="a92ce-115">Los geht's!</span><span class="sxs-lookup"><span data-stu-id="a92ce-115">Let's go</span></span>

<span data-ttu-id="a92ce-116">In diesem Abschnitt werden Remotebearbeitung und -debuggen von einem MacBook Pro aus auf einer in Azure ausgeführten Ubuntu-VM demonstriert.</span><span class="sxs-lookup"><span data-stu-id="a92ce-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="a92ce-117">Obwohl nicht Windows verwendet wird, **ist der Prozess identisch**.</span><span class="sxs-lookup"><span data-stu-id="a92ce-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="a92ce-118">Lokale Dateibearbeitung mit Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="a92ce-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="a92ce-119">Nach Starten der PowerShell-Erweiterung für VSCode und Öffnen der integrierten PowerShell-Konsole können wir `Open-EditorFile foo.ps1` oder `psedit foo.ps1` eingeben, um die lokale Datei „foo.ps1“ direkt im Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a92ce-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Bearbeitung von „foo.ps1“ in Open-EditorFile funktioniert lokal](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="a92ce-121">„foo.ps1“ muss bereits vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="a92ce-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="a92ce-122">Von dort aus können wir:</span><span class="sxs-lookup"><span data-stu-id="a92ce-122">From there, we can:</span></span>

<span data-ttu-id="a92ce-123">dem Bundsteg Haltepunkte hinzufügen ![Hinzufügen eines Haltepunkts zum Bundsteg](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="a92ce-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="a92ce-124">und F5 drücken, um das PowerShell-Skript zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="a92ce-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="a92ce-125">![Debuggen des lokalen PowerShell-Skripts](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="a92ce-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="a92ce-126">Sie können während des Debuggens mit der Debugging-Konsole interagieren, im Bereich auf der linken Seite die Variablen überprüfen und alle anderen standardmäßigen Debuggingtools verwenden.</span><span class="sxs-lookup"><span data-stu-id="a92ce-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="a92ce-127">Remotedateibearbeitung mit Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="a92ce-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="a92ce-128">Jetzt wenden wir uns Remotedateibearbeitung und -debuggen zu.</span><span class="sxs-lookup"><span data-stu-id="a92ce-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="a92ce-129">Die Schritte sind nahezu identisch, wir müssen nur zuerst eines tun – unsere PowerShell-Sitzung auf dem Remoteserver starten.</span><span class="sxs-lookup"><span data-stu-id="a92ce-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="a92ce-130">Hierfür gibt es ein Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a92ce-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="a92ce-131">Es heißt `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="a92ce-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="a92ce-132">Die vereinfachte Erläuterung des Cmdlets ist:</span><span class="sxs-lookup"><span data-stu-id="a92ce-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="a92ce-133">`Enter-PSSession -ComputerName foo` startet eine-Sitzung über WinRM</span><span class="sxs-lookup"><span data-stu-id="a92ce-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="a92ce-134">`Enter-PSSession -ContainerId foo` und `Enter-PSSession -VmId foo` starten eine Sitzung über PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="a92ce-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="a92ce-135">`Enter-PSSession -HostName foo` startet eine-Sitzung über SSH</span><span class="sxs-lookup"><span data-stu-id="a92ce-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="a92ce-136">Weitere Informationen zu `Enter-PSSession` finden Sie [hier](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6) in der Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="a92ce-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="a92ce-137">Ich verwende SSH für das Remoting, da ich von macOS aus auf eine Ubuntu-VM in Azure zugreife.</span><span class="sxs-lookup"><span data-stu-id="a92ce-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="a92ce-138">Zunächst führen wir in der integrierten Konsole Enter-PSSession aus.</span><span class="sxs-lookup"><span data-stu-id="a92ce-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="a92ce-139">Sie wissen, dass Sie sich in der Sitzung befinden, weil `[something]` links von Ihrer Eingabeaufforderung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a92ce-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Der Aufruf von Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="a92ce-141">Von dort aus können wir genau dieselben Schritte ausführen wie beim Bearbeiten eines lokalen Skripts.</span><span class="sxs-lookup"><span data-stu-id="a92ce-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="a92ce-142">Führen Sie `Open-EditorFile test.ps1` oder `psedit test.ps1` aus, um die Remotedatei `test.ps1` zu öffnen. ![Datei „test.ps1“ in Open-EditorFile](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="a92ce-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="a92ce-143">Bearbeiten Sie die Datei / legen Sie Haltepunkte fest.</span><span class="sxs-lookup"><span data-stu-id="a92ce-143">Edit the file/set breakpoints</span></span> ![Bearbeiten und Festlegen von Haltepunkten](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="a92ce-145">Beginnen Sie mit dem Debuggen (F5) der Remotedatei.</span><span class="sxs-lookup"><span data-stu-id="a92ce-145">Start debugging (F5) the remote file</span></span>

![Debuggen der Remotedatei](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="a92ce-147">Das ist schon alles!</span><span class="sxs-lookup"><span data-stu-id="a92ce-147">That's all there's to it!</span></span> <span data-ttu-id="a92ce-148">Wir hoffen, dass wir mit dieser Anleitung Ihre Fragen zu Remotedebuggen und -bearbeitung mit PowerShell in VSCode beantwortet haben.</span><span class="sxs-lookup"><span data-stu-id="a92ce-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="a92ce-149">Zur Lösung evtl. noch auftretender Probleme steht Ihnen das [GitHub-Repository](http://github.com/powershell/vscode-powershell) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="a92ce-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
