---
title: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
description: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655606"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="2c117-103">Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen</span><span class="sxs-lookup"><span data-stu-id="2c117-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="2c117-104">Für diejenigen unter Ihnen, die mit der ISE vertraut waren, denken Sie daran, dass Sie ausführen könnten `psedit file.ps1` über die integrierte Konsole zum Öffnen von Dateien – lokal oder remote - rechten Maustaste in der ISE.</span><span class="sxs-lookup"><span data-stu-id="2c117-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="2c117-105">Wie sich herausstellt, ist dieses Feature auch in der PowerShell-Erweiterung für VSCode verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2c117-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="2c117-106">Diesem Leitfaden erfahren Sie, wie es geht.</span><span class="sxs-lookup"><span data-stu-id="2c117-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2c117-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2c117-107">Prerequisites</span></span>

<span data-ttu-id="2c117-108">Dieses Handbuch setzt voraus, dass Sie haben:</span><span class="sxs-lookup"><span data-stu-id="2c117-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="2c117-109">eine Remoteressource (z. B.: eine VM, einen Container), dass Sie Zugriff haben</span><span class="sxs-lookup"><span data-stu-id="2c117-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="2c117-110">PowerShell, die darauf, und der Hostcomputer ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="2c117-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="2c117-111">VSCode und der PowerShell-Erweiterung für VSCode</span><span class="sxs-lookup"><span data-stu-id="2c117-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="2c117-112">Dieses Feature funktioniert auf Windows PowerShell und PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="2c117-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="2c117-113">Dieses Feature funktioniert auch bei der Verbindung von eines Remotecomputer über WinRM, PowerShell Direct oder SSH.</span><span class="sxs-lookup"><span data-stu-id="2c117-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="2c117-114">Wenn Sie SSH verwenden möchten, aber Windows verwenden, sehen Sie sich die [Win32-Version von SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="2c117-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="2c117-115">Los geht's!</span><span class="sxs-lookup"><span data-stu-id="2c117-115">Let's go</span></span>

<span data-ttu-id="2c117-116">In diesem Abschnitt erläutere ich, wie remote bearbeiten und Debuggen, die aus meinem MacBook Pro, auf einer Ubuntu-VM in Azure ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="2c117-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="2c117-117">Ich kann keine werden mithilfe von Windows, aber **der Prozess ist identisch**.</span><span class="sxs-lookup"><span data-stu-id="2c117-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="2c117-118">Lokale Datei mit Open-EditorFile bearbeiten</span><span class="sxs-lookup"><span data-stu-id="2c117-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="2c117-119">Mit der PowerShell-Erweiterung für VSCode gestartet und die integrierte PowerShell-Konsole geöffnet, gebe `Open-EditorFile foo.ps1` oder `psedit foo.ps1` auf die lokalen foo. ps1-Datei direkt im Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2c117-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo. ps1 funktioniert lokal.](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="2c117-121">foo. ps1 muss bereits vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="2c117-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="2c117-122">Von dort aus können wir folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="2c117-122">From there, we can:</span></span>

<span data-ttu-id="2c117-123">Haltepunkte hinzufügen, um den Bundsteg ![Breakpoint um Bundsteg hinzufügen](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="2c117-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="2c117-124">ein, und drücken Sie F5, um das PowerShell-Skript zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="2c117-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="2c117-125">![Debuggen lokale PowerShell-Skript](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="2c117-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="2c117-126">Sie können während des Debuggens die Debugging-Konsole interagieren, sehen Sie sich die Variablen im Bereich auf der linken Seite und alle anderen standardmäßigen debugging-Tools.</span><span class="sxs-lookup"><span data-stu-id="2c117-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="2c117-127">Remote-Datei mit Open-EditorFile bearbeiten</span><span class="sxs-lookup"><span data-stu-id="2c117-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="2c117-128">Jetzt wenden wir uns in remote-Datei bearbeiten und Debuggen.</span><span class="sxs-lookup"><span data-stu-id="2c117-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="2c117-129">Die Schritte sind nahezu identisch, gibt es nur einen Aspekt benötigten zuerst tun – geben unsere PowerShell-Sitzung mit dem Remoteserver.</span><span class="sxs-lookup"><span data-stu-id="2c117-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="2c117-130">Es ist ein Cmdlet für die zu diesem Zweck ein.</span><span class="sxs-lookup"><span data-stu-id="2c117-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="2c117-131">Es heißt `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="2c117-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="2c117-132">Die unten watered Erläuterung des-Cmdlets ist:</span><span class="sxs-lookup"><span data-stu-id="2c117-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="2c117-133">`Enter-PSSession -ComputerName foo` Startet eine-Sitzung über WinRM</span><span class="sxs-lookup"><span data-stu-id="2c117-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="2c117-134">`Enter-PSSession -ContainerId foo` und `Enter-PSSession -VmId foo` starten Sie eine Sitzung über PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="2c117-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="2c117-135">`Enter-PSSession -HostName foo` Startet eine-Sitzung über SSH</span><span class="sxs-lookup"><span data-stu-id="2c117-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="2c117-136">Weitere Informationen zur `Enter-PSSession`, sehen Sie sich die Dokumentation [hier](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="2c117-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="2c117-137">Ich verwende SSH für das Remoting, da ich auf einem Ubuntu-VM in Azure über MacOS werde.</span><span class="sxs-lookup"><span data-stu-id="2c117-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="2c117-138">Zunächst in der integrierten Konsole führen wir unsere Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="2c117-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="2c117-139">Wissen Sie, dass Sie in der Sitzung sind da `[something]` wird auf der linken Seite Ihre Eingabeaufforderung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2c117-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Der Aufruf von Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="2c117-141">Von dort aus können wir die genauen Schritte tun, als ob es ein lokales Skript bearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="2c117-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="2c117-142">Führen Sie `Open-EditorFile test.ps1` oder `psedit test.ps1` , öffnen Sie die Remote `test.ps1` Datei ![Open-EditorFile die test.ps1-Datei](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="2c117-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="2c117-143">Bearbeiten Sie die Datei/Set-Haltepunkte</span><span class="sxs-lookup"><span data-stu-id="2c117-143">Edit the file/set breakpoints</span></span> ![Bearbeiten, und legen Sie Haltepunkte fest](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="2c117-145">Starten des Debuggens (F5) der remote-Datei</span><span class="sxs-lookup"><span data-stu-id="2c117-145">Start debugging (F5) the remote file</span></span>

![Debuggen der remote-Datei](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="2c117-147">Das ist alles schon!</span><span class="sxs-lookup"><span data-stu-id="2c117-147">That's all there's to it!</span></span> <span data-ttu-id="2c117-148">Wir hoffen, dass in der vorliegenden, bereinigen Sie Fragen geholfen zu remote Debuggen und Bearbeiten von PowerShell in Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2c117-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="2c117-149">Wenn Sie Probleme haben, können Sie Probleme öffnen [GitHub-Repository](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="2c117-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
