---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Starten von Windows PowerShell
ms.openlocfilehash: 97b15a4cd79c77a391451ba917f985f9d99db3f5
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953822"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="369bb-103">Starten von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="369bb-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="369bb-104">Windows PowerShell ist eine Skript-Engine im `.DLL`-Format, die in mehreren Hosts eingebettet ist.</span><span class="sxs-lookup"><span data-stu-id="369bb-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="369bb-105">Als Host werden am häufigsten die interaktive Befehlszeile **PowerShell.exe** und die integrierte Skriptumgebung **PowerShell_ISE.exe** verwendet.</span><span class="sxs-lookup"><span data-stu-id="369bb-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="369bb-106">Informationen zum Starten von Windows PowerShell® unter Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 und Windows 8 finden Sie unter [Allgemeine Verwaltungsaufgaben und Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="369bb-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="369bb-107">Umbenannte Binärdatei in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="369bb-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="369bb-108">PowerShell Core, auch als PowerShell bezeichnet, ist die Open-Source-Version 6 und höher, die .NET Core verwendet.</span><span class="sxs-lookup"><span data-stu-id="369bb-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="369bb-109">Die unterstützten Versionen sind unter Windows, macOS und Linux verfügbar.</span><span class="sxs-lookup"><span data-stu-id="369bb-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="369bb-110">Ab PowerShell 6 wurde die PowerShell-Binärdatei für Windows in **pwsh.exe** und für macOS und Linux in **pwsh** umbenannt.</span><span class="sxs-lookup"><span data-stu-id="369bb-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="369bb-111">Sie können PowerShell-Vorschauversionen mit **pwsh-preview** starten.</span><span class="sxs-lookup"><span data-stu-id="369bb-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="369bb-112">Weitere Informationen finden Sie unter [Neuigkeiten in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) und [Über pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="369bb-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="369bb-113">Verwenden Sie die folgenden Links, um die Cmdlet-Referenz und die Installationsdokumentation für PowerShell 7 zu finden:</span><span class="sxs-lookup"><span data-stu-id="369bb-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="369bb-114">Dokument</span><span class="sxs-lookup"><span data-stu-id="369bb-114">Document</span></span> | <span data-ttu-id="369bb-115">Link</span><span class="sxs-lookup"><span data-stu-id="369bb-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="369bb-116">Cmdlet-Referenz</span><span class="sxs-lookup"><span data-stu-id="369bb-116">Cmdlet reference</span></span> | [<span data-ttu-id="369bb-117">PowerShell-Modulbrowser</span><span class="sxs-lookup"><span data-stu-id="369bb-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="369bb-118">Windows-Installation</span><span class="sxs-lookup"><span data-stu-id="369bb-118">Windows installation</span></span> | [<span data-ttu-id="369bb-119">Installing PowerShell Core on Windows (Installieren von PowerShell Core unter Windows)</span><span class="sxs-lookup"><span data-stu-id="369bb-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="369bb-120">macOS-Installation</span><span class="sxs-lookup"><span data-stu-id="369bb-120">macOS installation</span></span> | [<span data-ttu-id="369bb-121">Installieren von PowerShell Core unter macOS</span><span class="sxs-lookup"><span data-stu-id="369bb-121">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| <span data-ttu-id="369bb-122">Linux-Installation</span><span class="sxs-lookup"><span data-stu-id="369bb-122">Linux installation</span></span> | [<span data-ttu-id="369bb-123">Installieren von PowerShell Core unter Linux</span><span class="sxs-lookup"><span data-stu-id="369bb-123">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

<span data-ttu-id="369bb-124">Zur Ansicht des Inhalts anderer PowerShell-Versionen finden Sie weitere Informationen unter [Verwenden der PowerShell-Dokumentation](../how-to-use-docs.md).</span><span class="sxs-lookup"><span data-stu-id="369bb-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="369bb-125">Starten von Windows PowerShell unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="369bb-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="369bb-126">In diesem Abschnitt wird das Starten von Windows PowerShell und Windows PowerShell Integrated Scripting Environment (ISE) unter Windows® 7, Windows Server® 2008 R2 und Windows Server® 2008 erläutert.</span><span class="sxs-lookup"><span data-stu-id="369bb-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="369bb-127">Außerdem wird beschrieben, wie das optionale Feature für Windows PowerShell ISE in Windows PowerShell 2.0 in Windows Server® 2008 R2 und Windows Server® 2008 aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="369bb-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="369bb-128">Mit den folgenden Methoden können Sie die installierte Version von Windows PowerShell 3.0 oder Windows PowerShell 4.0 installieren, sofern zutreffend.</span><span class="sxs-lookup"><span data-stu-id="369bb-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="369bb-129">Über das Startmenü</span><span class="sxs-lookup"><span data-stu-id="369bb-129">From the Start Menu</span></span>

- <span data-ttu-id="369bb-130">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="369bb-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="369bb-131">Klicken Sie im **Start** Menü **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="369bb-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="369bb-132">An der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="369bb-132">At the Command Prompt</span></span>

<span data-ttu-id="369bb-133">Geben Sie zum Starten von Windows PowerShell in **Cmd.exe** Windows PowerShell oder Windows PowerShell ISE Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="369bb-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="369bb-134">Sie können auch die Parameter des Programms **PowerShell.exe** verwenden, um die Sitzung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="369bb-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="369bb-135">Weitere Informationen finden Sie unter [PowerShell.exe – Befehlszeilenhilfe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="369bb-135">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="369bb-136">Mit administrativen Berechtigungen (Als Administrator ausführen)</span><span class="sxs-lookup"><span data-stu-id="369bb-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="369bb-137">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie dann auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="369bb-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="369bb-138">Starten von Windows PowerShell ISE unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="369bb-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="369bb-139">Verwenden Sie eine der folgenden Methoden, um Windows PowerShell ISE zu starten:</span><span class="sxs-lookup"><span data-stu-id="369bb-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="369bb-140">Über das Startmenü</span><span class="sxs-lookup"><span data-stu-id="369bb-140">From the Start Menu</span></span>

- <span data-ttu-id="369bb-141">Klicken Sie auf **Start**, geben Sie **ISE** ein, und klicken Sie dann auf **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="369bb-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="369bb-142">Klicken Sie im **Menü** **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="369bb-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="369bb-143">An der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="369bb-143">At the Command Prompt</span></span>

<span data-ttu-id="369bb-144">Geben Sie zum Starten von Windows PowerShell in **Cmd.exe** Windows PowerShell oder Windows PowerShell ISE Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="369bb-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="369bb-145">oder</span><span class="sxs-lookup"><span data-stu-id="369bb-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="369bb-146">Mit administrativen Berechtigungen (Als Administrator ausführen)</span><span class="sxs-lookup"><span data-stu-id="369bb-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="369bb-147">Klicken Sie auf **Start**, geben Sie **ISE** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell ISE**, und klicken Sie dann auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="369bb-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="369bb-148">Aktivieren von Windows PowerShell ISE unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="369bb-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="369bb-149">In Windows PowerShell 4.0 und Windows PowerShell 3.0 ist Windows PowerShell ISE standardmäßig für alle Versionen von Windows aktiviert.</span><span class="sxs-lookup"><span data-stu-id="369bb-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="369bb-150">Falls es nicht bereits aktiviert ist, erfolgt die Aktivierung mithilfe von Windows Management Framework 4.0 oder Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="369bb-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="369bb-151">In Windows PowerShell 2.0 ist Windows PowerShell ISE standardmäßig für Windows 7 aktiviert.</span><span class="sxs-lookup"><span data-stu-id="369bb-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="369bb-152">Allerdings ist es in Windows Server 2008 R2 und Windows Server 2008 ein optionales Feature.</span><span class="sxs-lookup"><span data-stu-id="369bb-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="369bb-153">Gehen Sie wie folgt vor, um Windows PowerShell ISE in Windows PowerShell 2.0 unter Windows Server 2008 R2 oder Windows Server 2008 zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="369bb-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="369bb-154">So aktivieren Sie Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="369bb-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="369bb-155">Starten Sie den Server-Manager.</span><span class="sxs-lookup"><span data-stu-id="369bb-155">Start Server Manager.</span></span>
2. <span data-ttu-id="369bb-156">Klicken Sie auf **Features** und dann auf **Features hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="369bb-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="369bb-157">Klicken Sie unter „Features auswählen“ auf „Windows PowerShell Integrated Scripting Environment (ISE)“.</span><span class="sxs-lookup"><span data-stu-id="369bb-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="369bb-158">Starten der 32-Bit-Version von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="369bb-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="369bb-159">Bei der Installation von Windows PowerShell auf einem 64-Bit-Computer wird **Windows PowerShell (x86)** , eine 32-Bit-Version von Windows PowerShell, zusätzlich zur 64-Bit-Version installiert.</span><span class="sxs-lookup"><span data-stu-id="369bb-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="369bb-160">Wenn Sie Windows PowerShell ausführen, wird standardmäßig die 64-Bit-Version ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="369bb-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="369bb-161">Es kann jedoch möglicherweise erforderlich sein, **Windows PowerShell (x86)** auszuführen, z. B. wenn Sie ein Modul verwenden, das die 32-Bit-Version verlangt, oder Sie eine Remoteverbindung mit einem 32-Bit-Computer herstellen.</span><span class="sxs-lookup"><span data-stu-id="369bb-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="369bb-162">Wählen Sie eines der folgenden Verfahren, um eine 32-Bit-Version von Windows PowerShell zu starten.</span><span class="sxs-lookup"><span data-stu-id="369bb-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="369bb-163">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="369bb-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="369bb-164">Geben Sie im **Startbildschirm** **Windows PowerShell (x86)** ein.</span><span class="sxs-lookup"><span data-stu-id="369bb-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="369bb-165">Klicken Sie auf die Kachel **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="369bb-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="369bb-166">Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="369bb-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-167">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369bb-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-168">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="369bb-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="369bb-169">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="369bb-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="369bb-170">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369bb-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-171">Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="369bb-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-172">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369bb-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-173">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="369bb-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="369bb-174">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="369bb-174">In Windows® 8.1</span></span>

- <span data-ttu-id="369bb-175">Geben Sie im **Startbildschirm** **Windows PowerShell (x86)** ein.</span><span class="sxs-lookup"><span data-stu-id="369bb-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="369bb-176">Klicken Sie auf die Kachel **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="369bb-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="369bb-177">Falls Sie die [Remoteserver-Verwaltungstools](https://go.microsoft.com/fwlink/?LinkID=304145) für Windows 8.1 ausführen, können Sie Windows PowerShell x86 auch im Menü **Server Manager Tools** (Server-Managertools) öffnen.</span><span class="sxs-lookup"><span data-stu-id="369bb-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="369bb-178">Wählen Sie **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="369bb-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-179">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369bb-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-180">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="369bb-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="369bb-181">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="369bb-181">In Windows® 8</span></span>

- <span data-ttu-id="369bb-182">Bewegen Sie auf dem Bildschirm **Start** den Cursor in die rechte obere Ecke, klicken Sie auf **Einstellungen**, dann auf **Kacheln**, und bewegen Sie den Schieberegler **Verwaltungstools anzeigen** auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="369bb-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="369bb-183">Geben Sie dann **PowerShell** ein, und klicken Sie auf **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369bb-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-184">Falls Sie die [Remoteserver-Verwaltungstools](https://www.microsoft.com/download/details.aspx?id=28972) für Windows 8 ausführen, können Sie Windows PowerShell x86 auch im Menü **Server Manager Tools** (Server-Managertools) öffnen.</span><span class="sxs-lookup"><span data-stu-id="369bb-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="369bb-185">Wählen Sie **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="369bb-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-186">Geben Sie auf dem Bildschirm **Start** oder dem Desktop **PowerShell (x86)** ein, und klicken Sie dann auf **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="369bb-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="369bb-187">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="369bb-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
