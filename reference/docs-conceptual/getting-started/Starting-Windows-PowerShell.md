---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Starten von Windows PowerShell
ms.openlocfilehash: d2cb77027f404c5b008a902c5147d018dd741a67
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030456"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="d0320-103">Starten von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0320-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="d0320-104">PowerShell ist eine Skript-Engine im DLL-Format, die in mehreren Hosts eingebettet ist.</span><span class="sxs-lookup"><span data-stu-id="d0320-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="d0320-105">Als Host werden am häufigsten die interaktive Befehlszeile „PowerShell.exe“ und die integrierte Skriptumgebung „PowerShell_ISE.exe“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="d0320-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="d0320-106">Informationen zum Starten von Windows PowerShell® unter Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 und Windows 8 finden Sie unter [Allgemeine Verwaltungsaufgaben und Navigation in Windows](https://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="d0320-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="d0320-107">Starten von Windows PowerShell unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="d0320-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="d0320-108">In diesem Abschnitt wird das Starten von Windows PowerShell und Windows PowerShell Integrated Scripting Environment (ISE) unter Windows® 7, Windows Server® 2008 R2 und Windows Server® 2008 erläutert.</span><span class="sxs-lookup"><span data-stu-id="d0320-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="d0320-109">Außerdem wird beschrieben, wie das optionale Feature für Windows PowerShell ISE in Windows PowerShell 2.0 in Windows Server® 2008 R2 und Windows Server® 2008 aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="d0320-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="d0320-110">Mit den folgenden Methoden können Sie die installierte Version von Windows PowerShell 3.0 oder Windows PowerShell 4.0 installieren, sofern zutreffend.</span><span class="sxs-lookup"><span data-stu-id="d0320-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="d0320-111">Über das Startmenü</span><span class="sxs-lookup"><span data-stu-id="d0320-111">From the Start Menu</span></span>

- <span data-ttu-id="d0320-112">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="d0320-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="d0320-113">Klicken Sie im **Start** Menü **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="d0320-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="d0320-114">An der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="d0320-114">At the Command Prompt</span></span>

<span data-ttu-id="d0320-115">Geben Sie zum Starten von Windows PowerShell in Cmd.exe, Windows PowerShell oder Windows PowerShell ISE Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="d0320-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="d0320-116">Sie können auch die Parameter des Programms „PowerShell.exe“ verwenden, um die Sitzung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="d0320-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="d0320-117">Weitere Informationen finden Sie unter [PowerShell.exe – Befehlszeilenhilfe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="d0320-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="d0320-118">Mit administrativen Berechtigungen (Als Administrator ausführen)</span><span class="sxs-lookup"><span data-stu-id="d0320-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="d0320-119">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie dann auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="d0320-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="d0320-120">Starten von Windows PowerShell ISE unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="d0320-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="d0320-121">Verwenden Sie eine der folgenden Methoden, um Windows PowerShell ISE zu starten:</span><span class="sxs-lookup"><span data-stu-id="d0320-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="d0320-122">Über das Startmenü</span><span class="sxs-lookup"><span data-stu-id="d0320-122">From the Start Menu</span></span>

- <span data-ttu-id="d0320-123">Klicken Sie auf **Start**, geben Sie **ISE** ein, und klicken Sie dann auf **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="d0320-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="d0320-124">Klicken Sie im **Menü** **Start** auf **Alle Programme**, danach auf **Zubehör**, anschließend auf den Ordner **Windows PowerShell** und schließlich auf **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="d0320-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="d0320-125">An der Eingabeaufforderung</span><span class="sxs-lookup"><span data-stu-id="d0320-125">At the Command Prompt</span></span>

<span data-ttu-id="d0320-126">Geben Sie zum Starten von Windows PowerShell in Cmd.exe, Windows PowerShell oder Windows PowerShell ISE Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="d0320-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="d0320-127">oder</span><span class="sxs-lookup"><span data-stu-id="d0320-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="d0320-128">Mit administrativen Berechtigungen (Als Administrator ausführen)</span><span class="sxs-lookup"><span data-stu-id="d0320-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="d0320-129">Klicken Sie auf **Start**, geben Sie **ISE** ein, klicken Sie mit der rechten Maustaste auf **Windows PowerShell ISE**, und klicken Sie dann auf **Als Administrator ausführen**.</span><span class="sxs-lookup"><span data-stu-id="d0320-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="d0320-130">Aktivieren von Windows PowerShell ISE unter früheren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="d0320-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="d0320-131">In Windows PowerShell 4.0 und Windows PowerShell 3.0 ist Windows PowerShell ISE standardmäßig für alle Versionen von Windows aktiviert.</span><span class="sxs-lookup"><span data-stu-id="d0320-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="d0320-132">Falls es nicht bereits aktiviert ist, erfolgt die Aktivierung mithilfe von Windows Management Framework 4.0 oder Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="d0320-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="d0320-133">In Windows PowerShell 2.0 ist Windows PowerShell ISE standardmäßig für Windows 7 aktiviert.</span><span class="sxs-lookup"><span data-stu-id="d0320-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="d0320-134">Allerdings ist es in Windows Server 2008 R2 und Windows Server 2008 ein optionales Feature.</span><span class="sxs-lookup"><span data-stu-id="d0320-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="d0320-135">Gehen Sie wie folgt vor, um Windows PowerShell ISE in Windows PowerShell 2.0 unter Windows Server 2008 R2 oder Windows Server 2008 zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d0320-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="d0320-136">So aktivieren Sie Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="d0320-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="d0320-137">Starten Sie den Server-Manager.</span><span class="sxs-lookup"><span data-stu-id="d0320-137">Start Server Manager.</span></span>
2. <span data-ttu-id="d0320-138">Klicken Sie auf **Features** und dann auf **Features hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="d0320-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="d0320-139">Klicken Sie unter „Features auswählen“ auf „Windows PowerShell Integrated Scripting Environment (ISE)“.</span><span class="sxs-lookup"><span data-stu-id="d0320-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="d0320-140">Starten der 32-Bit-Version von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d0320-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="d0320-141">Bei der Installation von Windows PowerShell auf einem 64-Bit-Computer wird **Windows PowerShell (x86)**, eine 32-Bit-Version von Windows PowerShell, zusätzlich zur 64-Bit-Version installiert.</span><span class="sxs-lookup"><span data-stu-id="d0320-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="d0320-142">Wenn Sie Windows PowerShell ausführen, wird standardmäßig die 64-Bit-Version ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="d0320-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="d0320-143">Es kann jedoch möglicherweise erforderlich sein, **Windows PowerShell (x86)** auszuführen, z.B. wenn Sie ein Modul verwenden, das die 32-Bit-Version verlangt, oder Sie eine Remoteverbindung mit einem 32-Bit-Computer herstellen.</span><span class="sxs-lookup"><span data-stu-id="d0320-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="d0320-144">Wählen Sie eines der folgenden Verfahren, um eine 32-Bit-Version von Windows PowerShell zu starten.</span><span class="sxs-lookup"><span data-stu-id="d0320-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="d0320-145">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d0320-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="d0320-146">Geben Sie im **Startbildschirm** **Windows PowerShell (x86)** ein.</span><span class="sxs-lookup"><span data-stu-id="d0320-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="d0320-147">Klicken Sie auf die Kachel **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="d0320-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="d0320-148">Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="d0320-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-149">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d0320-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-150">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d0320-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="d0320-151">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="d0320-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="d0320-152">Klicken Sie auf **Start**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d0320-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-153">Wählen Sie im **Server-Manager** im Menü **Extras** den Eintrag **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="d0320-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-154">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d0320-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-155">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d0320-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="d0320-156">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="d0320-156">In Windows® 8.1</span></span>

- <span data-ttu-id="d0320-157">Geben Sie im **Startbildschirm** **Windows PowerShell (x86)** ein.</span><span class="sxs-lookup"><span data-stu-id="d0320-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="d0320-158">Klicken Sie auf die Kachel **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="d0320-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="d0320-159">Falls Sie die [Remoteserver-Verwaltungstools](https://go.microsoft.com/fwlink/?LinkID=304145) für Windows 8.1 ausführen, können Sie Windows PowerShell x86 auch im Server-Manager-Menü **Extras** öffnen.</span><span class="sxs-lookup"><span data-stu-id="d0320-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="d0320-160">Wählen Sie **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="d0320-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-161">Bewegen Sie auf dem Desktop den Cursor in die rechte obere Ecke, klicken Sie auf **Suchen**, geben Sie **PowerShell x86** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d0320-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-162">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d0320-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="d0320-163">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="d0320-163">In Windows® 8</span></span>

- <span data-ttu-id="d0320-164">Bewegen Sie auf dem Bildschirm **Start** den Cursor in die rechte obere Ecke, klicken Sie auf **Einstellungen**, dann auf **Kacheln**, und bewegen Sie den Schieberegler **Verwaltungstools anzeigen** auf „Ja“.</span><span class="sxs-lookup"><span data-stu-id="d0320-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="d0320-165">Geben Sie dann **PowerShell** ein, und klicken Sie auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d0320-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-166">Falls Sie die [Remoteserver-Verwaltungstools](https://www.microsoft.com/download/details.aspx?id=28972) für Windows 8 ausführen, können Sie Windows PowerShell x86 auch im Server-Manager-Menü **Extras** öffnen.</span><span class="sxs-lookup"><span data-stu-id="d0320-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="d0320-167">Wählen Sie **Windows PowerShell (x86)** aus.</span><span class="sxs-lookup"><span data-stu-id="d0320-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-168">Geben Sie auf dem Bildschirm **Start** oder dem Desktop **PowerShell (x86)** ein, und klicken Sie dann auf **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="d0320-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="d0320-169">Geben Sie über die Befehlszeile Folgendes ein: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="d0320-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
