---
ms.date: 2017-08-09
keywords: powershell,cmdlet,download,installieren,setup,windows 10, windows 8.1, windows 8.0,windows 7
title: Installieren von Windows PowerShell
ms.openlocfilehash: 781bf50b6ac649e72bcdbb708555275fb7422d94
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="8a61c-103">Installieren von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a61c-103">Installing Windows PowerShell</span></span>

<span data-ttu-id="8a61c-104">PowerShell ist ab Windows 7 SP1 und Windows Server 2008 R2 SP1 standardmäßig auf jedem Windows-Computer installiert.</span><span class="sxs-lookup"><span data-stu-id="8a61c-104">PowerShell comes installed by default in every Windows, starting with Windows 7 SP1 and Windows Server 2008 R2 SP1.</span></span>

<span data-ttu-id="8a61c-105">Benutzer von Linux, macOS und Windows, die **PowerShell 6** (Beta) auf ihren Computern installieren möchten, müssen Folgendes durchführen:</span><span class="sxs-lookup"><span data-stu-id="8a61c-105">Linux, macOS, and Windows users that would like to install **PowerShell 6** (beta), in their machines, need to:</span></span>

1. <span data-ttu-id="8a61c-106">PowerShell für ihr Betriebssystem und die entsprechende Version von [GitHub](https://github.com/powershell/powershell#get-powershell) herunterladen</span><span class="sxs-lookup"><span data-stu-id="8a61c-106">Get PowerShell for the specific OS and version, from [GitHub](https://github.com/powershell/powershell#get-powershell)</span></span>
1. <span data-ttu-id="8a61c-107">Den Installationsanweisungen folgen</span><span class="sxs-lookup"><span data-stu-id="8a61c-107">Follow the installation instructions</span></span>
  - [<span data-ttu-id="8a61c-108">Linux</span><span class="sxs-lookup"><span data-stu-id="8a61c-108">Linux</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md)
  - [<span data-ttu-id="8a61c-109">macOS</span><span class="sxs-lookup"><span data-stu-id="8a61c-109">macOS</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#macos-1012)
  - [<span data-ttu-id="8a61c-110">Windows</span><span class="sxs-lookup"><span data-stu-id="8a61c-110">Windows</span></span>](https://github.com/PowerShell/PowerShell/blob/master/docs/installation/windows.md#msi)

<span data-ttu-id="8a61c-111">PowerShell 6 ist auch für Docker verfügbar. Hier finden Sie Anweisungen zur [Installation von Docker](https://github.com/PowerShell/PowerShell/tree/master/docker).</span><span class="sxs-lookup"><span data-stu-id="8a61c-111">PowerShell 6 is also available for Docker; see [Docker installation](https://github.com/PowerShell/PowerShell/tree/master/docker) instructions.</span></span>

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a><span data-ttu-id="8a61c-112">Finden von PowerShell unter Windows 10, 8.1, 8.0 und 7</span><span class="sxs-lookup"><span data-stu-id="8a61c-112">Finding PowerShell in Windows 10, 8.1, 8.0, and 7</span></span>

<span data-ttu-id="8a61c-113">Manchmal kann es schwierig sein, die PowerShell-Konsole oder die ISE (integrierte Skriptumgebung) unter Windows zu finden, da sich der Speicherort je nach Windowsversion unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="8a61c-113">Sometimes locating PowerShell console or ISE (Integrated Scripting Environment) in Windows can be difficult, as it's location moves from one version of Windows to the next.</span></span>

<span data-ttu-id="8a61c-114">In den folgenden Tabellen erfahren Sie, wo sich PowerShell in Ihrer Windows-Version befindet.</span><span class="sxs-lookup"><span data-stu-id="8a61c-114">The following tables should help you find PowerShell in your Windows version.</span></span>
<span data-ttu-id="8a61c-115">Alle aufgelisteten Versionen sind die ursprünglich veröffentlichten Versionen ohne Updates.</span><span class="sxs-lookup"><span data-stu-id="8a61c-115">All versions listed here are the original version, as released, with no updates.</span></span>

### <a name="for-console"></a><span data-ttu-id="8a61c-116">Für die Konsole</span><span class="sxs-lookup"><span data-stu-id="8a61c-116">For Console</span></span>

<span data-ttu-id="8a61c-117">Version</span><span class="sxs-lookup"><span data-stu-id="8a61c-117">Version</span></span> | <span data-ttu-id="8a61c-118">Optionen</span><span class="sxs-lookup"><span data-stu-id="8a61c-118">Location</span></span>
-- | --
<span data-ttu-id="8a61c-119">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8a61c-119">Windows 10</span></span> | <span data-ttu-id="8a61c-120">Klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort „PowerShell“ ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-120">Click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="8a61c-121">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-121">Windows 8.1, 8.0</span></span> | <span data-ttu-id="8a61c-122">Geben Sie auf dem Startbildschirm „PowerShell“ ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-122">On the start screen, start typing PowerShell.</span></span><br/><span data-ttu-id="8a61c-123">Wenn Sie sich auf dem Desktop befinden, klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort „PowerShell“ ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-123">If on desktop, click left lower corner Windows icon, start typing PowerShell</span></span>
<span data-ttu-id="8a61c-124">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="8a61c-124">Windows 7 SP1</span></span> | <span data-ttu-id="8a61c-125">Klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie in der Suchleiste „PowerShell“ ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-125">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

### <a name="for-ise"></a><span data-ttu-id="8a61c-126">Für die ISE</span><span class="sxs-lookup"><span data-stu-id="8a61c-126">For ISE</span></span>

<span data-ttu-id="8a61c-127">Version</span><span class="sxs-lookup"><span data-stu-id="8a61c-127">Version</span></span> | <span data-ttu-id="8a61c-128">Optionen</span><span class="sxs-lookup"><span data-stu-id="8a61c-128">Location</span></span>
-- | --
<span data-ttu-id="8a61c-129">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8a61c-129">Windows 10</span></span> | <span data-ttu-id="8a61c-130">Klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort „ISE“ ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-130">Click left lower corner Windows icon, start typing ISE</span></span>
<span data-ttu-id="8a61c-131">Windows 8.1, 8.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-131">Windows 8.1, 8.0</span></span> | <span data-ttu-id="8a61c-132">Geben Sie auf dem Startbildschirm **PowerShell ISE** ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-132">On the start screen, type **PowerShell ISE**.</span></span><br/><span data-ttu-id="8a61c-133">Wenn Sie sich auf dem Desktop befinden, klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort **PowerShell ISE** ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-133">If on desktop, click left lower corner Windows icon, type **PowerShell ISE**</span></span>
<span data-ttu-id="8a61c-134">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="8a61c-134">Windows 7 SP1</span></span> | <span data-ttu-id="8a61c-135">Klicken Sie auf das Windows-Symbol in der linken unteren Ecke, geben Sie in der Suchleiste „PowerShell“ ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-135">Click left lower corner Windows icon, on the search box start typing PowerShell</span></span>

## <a name="finding-powershell-in-windows-server-versions"></a><span data-ttu-id="8a61c-136">Finden von PowerShell in Windows Server-Versionen</span><span class="sxs-lookup"><span data-stu-id="8a61c-136">Finding PowerShell in Windows Server versions</span></span>

<span data-ttu-id="8a61c-137">Ab Windows Server 2008 R2 kann ein Windows-Betriebssystem ohne die GUI (grafische Benutzeroberfläche) installiert werden.</span><span class="sxs-lookup"><span data-stu-id="8a61c-137">Starting with Windows Server 2008 R2, Windows operating system can be installed without the graphical user interface (GUI).</span></span>
<span data-ttu-id="8a61c-138">Editionen von Windows Server ohne die GUI werden als **Core**-Editionen bezeichnet. Editionen mit der GUI werden als **Desktop**-Editionen bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="8a61c-138">Editions of Windows Server without GUI are named **Core** editions, and editions with the GUI are named **Desktop**.</span></span>

### <a name="windows-server-core-editions"></a><span data-ttu-id="8a61c-139">Windows Server Core-Editionen</span><span class="sxs-lookup"><span data-stu-id="8a61c-139">Windows Server Core editions</span></span>

<span data-ttu-id="8a61c-140">In allen Core-Editionen wird ein Windows-Eingabeaufforderungsfenster geöffnet, wenn Sie sich beim Server anmelden.</span><span class="sxs-lookup"><span data-stu-id="8a61c-140">In all Core editions, when you log to the server you get a Windows command prompt window.</span></span>

<span data-ttu-id="8a61c-141">Geben Sie `powershell` ein, und drücken Sie auf **EINGABE**, um PowerShell in der Eingabeaufforderungssitzung zu starten.</span><span class="sxs-lookup"><span data-stu-id="8a61c-141">Type `powershell` and press **ENTER** to start PowerShell inside the command prompt session.</span></span> <span data-ttu-id="8a61c-142">Geben Sie `exit` ein, um die PowerShell-Sitzung zu beenden und zur Eingabeaufforderung zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="8a61c-142">Type `exit` to terminate the PowerShell session and return to command prompt.</span></span>

### <a name="windows-server-desktop-editions"></a><span data-ttu-id="8a61c-143">Windows Server Desktop-Editionen</span><span class="sxs-lookup"><span data-stu-id="8a61c-143">Windows Server Desktop editions</span></span>

<span data-ttu-id="8a61c-144">Klicken Sie in allen Desktop-Editionen auf das Windows-Symbol in der linken unteren Ecke, geben Sie dort „PowerShell“ ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-144">In all desktop editions, click the left lower corner Windows icon, start typing PowerShell.</span></span>
<span data-ttu-id="8a61c-145">Dann erhalten Sie sowohl Konsolen- als auch ISE-Optionen.</span><span class="sxs-lookup"><span data-stu-id="8a61c-145">You get both console and ISE options.</span></span>

<span data-ttu-id="8a61c-146">Von der oben genannten Regel ist nur die ISE in Windows Server 2008 R2 SP1 ausgenommen. Wenn Sie diese Version nutzen, klicken Sie auf das Windows-Symbol in der rechten unteren Ecke, und geben Sie „PowerShell ISE“ ein.</span><span class="sxs-lookup"><span data-stu-id="8a61c-146">The only exception to the above rule is the ISE in Windows Server 2008 R2 SP1; in this case, click the left lower corner Windows icon, type PowerShell ISE.</span></span>

## <a name="how-to-check-the-version-of-powershell"></a><span data-ttu-id="8a61c-147">Überprüfen der PowerShell-Version</span><span class="sxs-lookup"><span data-stu-id="8a61c-147">How to check the version of PowerShell</span></span>

<span data-ttu-id="8a61c-148">Um herauszufinden, welche Version von PowerShell installiert ist, starten Sie eine PowerShell-Konsole (oder die ISE), und geben Sie `$PSVersionTable` ein und drücken auf **EINGABE**.</span><span class="sxs-lookup"><span data-stu-id="8a61c-148">To find which version of PowerShell you have installed, start a PowerShell console (or the ISE) and type `$PSVersionTable` and press **ENTER**.</span></span>

## <a name="upgrading-existing-windows-powershell"></a><span data-ttu-id="8a61c-149">Aktualisieren einer vorhandenen Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a61c-149">Upgrading existing Windows PowerShell</span></span>

<span data-ttu-id="8a61c-150">Das Installationspaket für PowerShell befindet sich in einem WMF-Installer.</span><span class="sxs-lookup"><span data-stu-id="8a61c-150">The installation package for PowerShell comes inside a WMF installer.</span></span>
<span data-ttu-id="8a61c-151">Die Version des WMF-Installers entspricht der PowerShell-Version. Es gibt keinen eigenständigen Installer für Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a61c-151">The version of the WMF installer matches the version of PowerShell; there's no stand alone installer for Windows PowerShell.</span></span>

<span data-ttu-id="8a61c-152">Wenn Sie Ihre vorhandene Version in Windows aktualisieren müssen, können Sie in der folgenden Tabelle den Installer für die PowerShell-Version finden, auf die Sie aktualisieren möchten.</span><span class="sxs-lookup"><span data-stu-id="8a61c-152">If you need to update your existing version of PowerShell, in Windows, use the following table to locate the installer for the version of PowerShell you want to update to.</span></span>

<span data-ttu-id="8a61c-153">Windows</span><span class="sxs-lookup"><span data-stu-id="8a61c-153">Windows</span></span> | <span data-ttu-id="8a61c-154">PS 3.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-154">PS 3.0</span></span> | <span data-ttu-id="8a61c-155">PS 4.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-155">PS 4.0</span></span> | <span data-ttu-id="8a61c-156">PS 5.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-156">PS 5.0</span></span> | <span data-ttu-id="8a61c-157">PS 5.1</span><span class="sxs-lookup"><span data-stu-id="8a61c-157">PS 5.1</span></span> |
--|--|--|--|--|
<span data-ttu-id="8a61c-158">Windows 10 (siehe Hinweis 1)</span><span class="sxs-lookup"><span data-stu-id="8a61c-158">Windows 10 (see Note1)</span></span><br/><span data-ttu-id="8a61c-159">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="8a61c-159">Windows Server 2016</span></span> | - | - | - | <span data-ttu-id="8a61c-160">installiert</span><span class="sxs-lookup"><span data-stu-id="8a61c-160">installed</span></span>
<span data-ttu-id="8a61c-161">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="8a61c-161">Windows 8.1</span></span><br/><span data-ttu-id="8a61c-162">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8a61c-162">Windows Server 2012 R2</span></span> | - | <span data-ttu-id="8a61c-163">installiert</span><span class="sxs-lookup"><span data-stu-id="8a61c-163">installed</span></span> | [<span data-ttu-id="8a61c-164">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-164">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="8a61c-165">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="8a61c-165">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="8a61c-166">Windows 8</span><span class="sxs-lookup"><span data-stu-id="8a61c-166">Windows 8</span></span><br/><span data-ttu-id="8a61c-167">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="8a61c-167">Windows Server 2012</span></span> | <span data-ttu-id="8a61c-168">installiert</span><span class="sxs-lookup"><span data-stu-id="8a61c-168">installed</span></span> | [<span data-ttu-id="8a61c-169">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-169">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="8a61c-170">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-170">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="8a61c-171">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="8a61c-171">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
<span data-ttu-id="8a61c-172">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="8a61c-172">Windows 7 SP1</span></span><br/><span data-ttu-id="8a61c-173">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="8a61c-173">Windows Server 2008 R2 SP1</span></span> | [<span data-ttu-id="8a61c-174">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-174">WMF 3.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [<span data-ttu-id="8a61c-175">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-175">WMF 4.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [<span data-ttu-id="8a61c-176">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="8a61c-176">WMF 5.0</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [<span data-ttu-id="8a61c-177">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="8a61c-177">WMF 5.1</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> <span data-ttu-id="8a61c-178">**Hinweis 1**:</span><span class="sxs-lookup"><span data-stu-id="8a61c-178">**Note 1**:</span></span>
  >>
  >> <span data-ttu-id="8a61c-179">In der ersten Version von Windows 10 wird PowerShell von Version 5.0 auf 5.1 aktualisiert, wenn automatische Updates aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="8a61c-179">On the initial release of Windows 10, with automatic updates enabled, PowerShell gets updated from version 5.0 to 5.1.</span></span>
  >>
  >> <span data-ttu-id="8a61c-180">Wenn die ursprüngliche Version von Windows 10 nicht über Windows Updates aktualisiert wurde, ist die PowerShell-Version 5.0.</span><span class="sxs-lookup"><span data-stu-id="8a61c-180">If the original version of Windows 10 is not updated through Windows Updates, the version of PowerShell is 5.0.</span></span>

## <a name="need-azure-powershell"></a><span data-ttu-id="8a61c-181">Benötigen Sie Azure PowerShell?</span><span class="sxs-lookup"><span data-stu-id="8a61c-181">Need Azure PowerShell</span></span>

<span data-ttu-id="8a61c-182">Wenn Sie auf der Suche nach **Azure PowerShell** sind, können Sie sich zunächst den [Overview of Azure PowerShell (Überblick über Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure) anschauen.</span><span class="sxs-lookup"><span data-stu-id="8a61c-182">If you're looking for **Azure PowerShell**, you could start with [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure).</span></span>

<span data-ttu-id="8a61c-183">Ansonsten finden Sie hier weitere Informationen: [Install and configure Azure PowerShell (Installieren und Konfigurieren von Azure PowerShell)](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps).</span><span class="sxs-lookup"><span data-stu-id="8a61c-183">Otherwise, what you might need is [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)</span></span>

## <a name="see-also"></a><span data-ttu-id="8a61c-184">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8a61c-184">See Also</span></span>

- [<span data-ttu-id="8a61c-185">Windows PowerShell-Systemanforderungen</span><span class="sxs-lookup"><span data-stu-id="8a61c-185">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="8a61c-186">Starten von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a61c-186">Starting Windows PowerShell</span></span>](Starting-Windows-PowerShell.md)
