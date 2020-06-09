---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwenden der Windows PowerShell 2.0 Engine
ms.openlocfilehash: e00fb71c7fc32f5b48bc17ef5b25f910a846c893
ms.sourcegitcommit: 1748b2bdfae81d98097962c6c25c25df4bced1d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2020
ms.locfileid: "84262612"
---
# <a name="using-the-windows-powershell-20-engine"></a><span data-ttu-id="53c2e-103">Verwenden der Windows PowerShell 2.0 Engine</span><span class="sxs-lookup"><span data-stu-id="53c2e-103">Using the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="53c2e-104">Windows PowerShell darauf ausgelegt, mit früheren Versionen abwärtskompatibel zu sein.</span><span class="sxs-lookup"><span data-stu-id="53c2e-104">Windows PowerShell is designed to be backward compatible with previous versions.</span></span> <span data-ttu-id="53c2e-105">Cmdlets, Anbieter, Snap-Ins, Module und Skripts, die für Windows PowerShell 2.0 geschrieben wurden, können unverändert in neueren Versionen von Windows PowerShell ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="53c2e-105">Cmdlets, providers, snap-ins, modules, and scripts written for Windows PowerShell 2.0 run unchanged in newer versions Windows PowerShell.</span></span> <span data-ttu-id="53c2e-106">In Microsoft .NET Framework 4 wurde jedoch die Richtlinie für die Laufzeitaktivierung geändert.</span><span class="sxs-lookup"><span data-stu-id="53c2e-106">However, Microsoft .NET Framework 4 changed the runtime activation policy.</span></span>
<span data-ttu-id="53c2e-107">Windows PowerShell-Hostprogramme, die für Windows PowerShell 2.0 geschrieben und mit Common Language Runtime (CLR) 2.0 kompiliert wurden, können nicht unverändert in neuen Versionen von Windows PowerShell ausgeführt werden, die mit CLR 4.0 (oder höher) kompiliert wurden.</span><span class="sxs-lookup"><span data-stu-id="53c2e-107">Windows PowerShell host programs written for Windows PowerShell 2.0 and compiled with Common Language Runtime (CLR) 2.0 cannot run without modification in new versions Windows PowerShell that are compiled with CLR 4.0 (or higher).</span></span>

<span data-ttu-id="53c2e-108">Die Windows PowerShell 2.0 Engine sollte nur verwendet werden, wenn ein vorhandenes Skript oder Hostprogramm nicht ausgeführt werden kann, da es inkompatibel mit Windows PowerShell 5.1 ist.</span><span class="sxs-lookup"><span data-stu-id="53c2e-108">The Windows PowerShell 2.0 Engine is intended to be used only when an existing script or host program cannot run because it is incompatible with Windows PowerShell 5.1.</span></span> <span data-ttu-id="53c2e-109">Beispiele hierfür sind ältere Versionen von Exchange oder SQL Server-Modulen.</span><span class="sxs-lookup"><span data-stu-id="53c2e-109">Examples of this include older versions of Exchange or SQL Server modules.</span></span> <span data-ttu-id="53c2e-110">Solche Fälle sind allerdings eher selten.</span><span class="sxs-lookup"><span data-stu-id="53c2e-110">Such cases are expected to be rare.</span></span>

<span data-ttu-id="53c2e-111">Viele Programme, die Windows PowerShell 2.0 Engine benötigen, starten sie automatisch.</span><span class="sxs-lookup"><span data-stu-id="53c2e-111">Many programs that require the Windows PowerShell 2.0 Engine start it automatically.</span></span> <span data-ttu-id="53c2e-112">Diese Anweisungen gelten für die seltenen Fälle, in denen Sie die Engine manuell starten müssen.</span><span class="sxs-lookup"><span data-stu-id="53c2e-112">These instructions are included for the rare situations in which you need to start the engine manually.</span></span>

## <a name="deprecation-and-security-concerns"></a><span data-ttu-id="53c2e-113">Eingestellte Unterstützung und Sicherheitsaspekte</span><span class="sxs-lookup"><span data-stu-id="53c2e-113">Deprecation and security concerns</span></span>

<span data-ttu-id="53c2e-114">Windows PowerShell 2.0 wurde im August 2017 eingestellt.</span><span class="sxs-lookup"><span data-stu-id="53c2e-114">Windows PowerShell 2.0 was deprecated in August, 2017.</span></span> <span data-ttu-id="53c2e-115">Weitere Informationen finden Sie in der [Ankündigung][] im PowerShell-Blog.</span><span class="sxs-lookup"><span data-stu-id="53c2e-115">For more information, see the [announcement][] on the PowerShell blog.</span></span>

<span data-ttu-id="53c2e-116">In Windows PowerShell 2.0 fehlt eine beträchtliche Menge der Härtungs- und Sicherheitsfeatures, die in den Versionen 3, 4 und 5 hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="53c2e-116">Windows PowerShell 2.0 is missing a significant amount of the hardening and security features added in versions 3, 4, and 5.</span></span> <span data-ttu-id="53c2e-117">Es wird dringend empfohlen, dass Benutzer diese Version nicht verwenden, wenn dies möglich ist.</span><span class="sxs-lookup"><span data-stu-id="53c2e-117">We highly, highly recommend that users not use it if they can help it.</span></span> <span data-ttu-id="53c2e-118">Weitere Informationen finden Sie unter [Ein Vergleich der Sicherheit von Shell- und Skriptsprachen][] und [PowerShell ♥ The Blue Team][blueteam].</span><span class="sxs-lookup"><span data-stu-id="53c2e-118">For more information, see [A Comparison of Shell and Scripting Language Security][] and [PowerShell ♥ the Blue Team][blueteam].</span></span>

## <a name="installing-and-enabling-required-programs"></a><span data-ttu-id="53c2e-119">Installieren und Aktivieren erforderlicher Programme</span><span class="sxs-lookup"><span data-stu-id="53c2e-119">Installing and Enabling Required Programs</span></span>

<span data-ttu-id="53c2e-120">Aktivieren Sie Windows PowerShell 2.0 Engine und Microsoft .NET Framework 3.5 mit Service Pack 1, bevor Sie Windows PowerShell 2.0 Engine starten.</span><span class="sxs-lookup"><span data-stu-id="53c2e-120">Before starting the Windows PowerShell 2.0 Engine, enable the Windows PowerShell 2.0 Engine and Microsoft .NET Framework 3.5 with Service Pack 1.</span></span> <span data-ttu-id="53c2e-121">Anweisungen hierzu finden Sie unter [Installieren von Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="53c2e-121">For instructions, see [Installing Windows PowerShell][].</span></span>

<span data-ttu-id="53c2e-122">Systeme, auf denen Windows Management Framework 3.0 oder höher installiert ist, verfügen über alle erforderlichen Komponenten.</span><span class="sxs-lookup"><span data-stu-id="53c2e-122">Systems on which Windows Management Framework 3.0 or higher is installed have all of the required components.</span></span> <span data-ttu-id="53c2e-123">Es ist keine weitere Konfiguration erforderlich.</span><span class="sxs-lookup"><span data-stu-id="53c2e-123">No further configuration is necessary.</span></span> <span data-ttu-id="53c2e-124">Informationen zum Installieren von Windows Management Framework finden Sie unter [Installieren und Konfigurieren von WMF][].</span><span class="sxs-lookup"><span data-stu-id="53c2e-124">For information about installing Windows Management Framework, see [Install and configure WMF][].</span></span>

## <a name="how-to-start-the-windows-powershell-20-engine"></a><span data-ttu-id="53c2e-125">So starten Sie Windows PowerShell 2.0 Engine</span><span class="sxs-lookup"><span data-stu-id="53c2e-125">How to start the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="53c2e-126">Beim Starten von Windows PowerShell wird die neueste Version standardmäßig gestartet.</span><span class="sxs-lookup"><span data-stu-id="53c2e-126">When you start Windows PowerShell the newest version starts by default.</span></span> <span data-ttu-id="53c2e-127">Verwenden Sie den „Version“-Parameter von `PowerShell.exe`, um Windows PowerShell mit Windows PowerShell 2.0 Engine zu starten.</span><span class="sxs-lookup"><span data-stu-id="53c2e-127">To start Windows PowerShell with the Windows PowerShell 2.0 Engine, use the Version parameter of `PowerShell.exe`.</span></span> <span data-ttu-id="53c2e-128">Sie können den Befehl an jeder Eingabeaufforderung einschließlich Windows PowerShell und „Cmd.exe“ ausführen.</span><span class="sxs-lookup"><span data-stu-id="53c2e-128">You can run the command at any command prompt, including Windows PowerShell and Cmd.exe.</span></span>

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a><span data-ttu-id="53c2e-129">So starten Sie eine Remotesitzung mit Windows PowerShell 2.0 Engine</span><span class="sxs-lookup"><span data-stu-id="53c2e-129">How to start a remote session with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="53c2e-130">Erstellen Sie auf dem Remotecomputer eine Sitzungskonfiguration (auch _Endpunkt_ genannt), die Windows PowerShell 2.0 Engine lädt, um Windows PowerShell 2.0 Engine in einer Remotesitzung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="53c2e-130">To run the Windows PowerShell 2.0 Engine in a remote session, create a session configuration (also known as an _endpoint_) on the remote computer that loads the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="53c2e-131">Die Sitzungskonfiguration wird auf dem Remotecomputer gespeichert und kann von jedem autorisierten Benutzer verwendet werden, um Sitzungen zu erstellen, die Windows PowerShell 2.0 Engine verwenden.</span><span class="sxs-lookup"><span data-stu-id="53c2e-131">The session configuration is saved on the remote computer and can be used by any authorized user to create sessions that use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="53c2e-132">Dies ist eine komplexe Aufgabe, die in der Regel von einem Systemadministrator ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="53c2e-132">This is an advanced task that is typically performed by a system administrator.</span></span>

<span data-ttu-id="53c2e-133">Im folgenden Verfahren wird der **PSVersion**-Parameter des Cmdlets [Register-PSSessionConfiguration][] zum Erstellen einer Sitzungskonfiguration verwendet, die Windows PowerShell 2.0 Engine nutzt.</span><span class="sxs-lookup"><span data-stu-id="53c2e-133">The following procedure uses the **PSVersion** parameter of the [Register-PSSessionConfiguration][] cmdlet to create a session configuration that uses the Windows PowerShell 2.0 Engine.</span></span> <span data-ttu-id="53c2e-134">Sie können auch den **PowerShellVersion**-Parameter des Cmdlets [New-PSSessionConfigurationFile][] verwenden, um eine Sitzungskonfigurationsdatei für eine Sitzung zu erstellen, die Windows PowerShell 2.0 Engine lädt. Sie können auch den **PSVersion**-Parameter des Parameters [Set-PSSessionConfiguration][] verwenden, um eine Sitzungskonfiguration so zu ändern, dass Windows PowerShell 2.0 Engine verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="53c2e-134">You can also use the **PowerShellVersion** parameter of the [New-PSSessionConfigurationFile][] cmdlet to create a session configuration file for a session that loads the Windows PowerShell 2.0 Engine and you can use the **PSVersion** parameter of the [Set-PSSessionConfiguration][] parameter to change a session configuration to use the Windows PowerShell 2.0 Engine.</span></span>

<span data-ttu-id="53c2e-135">Weitere Informationen zu Sitzungskonfigurationsdateien finden Sie unter [about_Session_Configuration_Files][].</span><span class="sxs-lookup"><span data-stu-id="53c2e-135">For more information about session configuration files, see [about_Session_Configuration_Files][].</span></span>
<span data-ttu-id="53c2e-136">Informationen zu Sitzungskonfigurationen, einschließlich Einrichtung und Sicherheit, finden Sie unter [about_Session_Configurations][].</span><span class="sxs-lookup"><span data-stu-id="53c2e-136">For information about session configurations, including setup and security, see [about_Session_Configurations][].</span></span>

### <a name="to-start-a-remote-windows-powershell-20-session"></a><span data-ttu-id="53c2e-137">Gehen Sie folgendermaßen vor, um eine Remotesitzung von Windows PowerShell 2.0 zu starten</span><span class="sxs-lookup"><span data-stu-id="53c2e-137">To start a remote Windows PowerShell 2.0 session</span></span>

1. <span data-ttu-id="53c2e-138">Verwenden Sie den **PSVersion**-Parameter des Cmdlets `Register-PSSessionConfiguration` mit dem Wert `2.0`, um eine Sitzungskonfiguration zu erstellen, die Windows PowerShell 2.0 Engine erfordert.</span><span class="sxs-lookup"><span data-stu-id="53c2e-138">To create a session configuration that requires the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet with a value of `2.0`.</span></span>
   <span data-ttu-id="53c2e-139">Führen Sie diesen Befehl auf dem Computer auf der Serverseite oder dem empfangenden Ende der Verbindung aus.</span><span class="sxs-lookup"><span data-stu-id="53c2e-139">Run this command on the computer at the "server side" or receiving end of the connection.</span></span>

   <span data-ttu-id="53c2e-140">Der folgende Befehl erstellt die PS2-Sitzungskonfiguration auf dem Computer „Server01“.</span><span class="sxs-lookup"><span data-stu-id="53c2e-140">The following sample command creates the PS2 session configuration on the Server01 computer.</span></span> <span data-ttu-id="53c2e-141">Starten Sie Windows PowerShell mit der Option **Als Administrator ausführen**, um diesen Befehl auszuführen.</span><span class="sxs-lookup"><span data-stu-id="53c2e-141">To run this command, start Windows PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. <span data-ttu-id="53c2e-142">Zum Erstellen einer Sitzung auf dem Computer „Server01“, der die PS2-Sitzungskonfiguration nutzt, verwenden Sie den **ConfigurationName**-Parameter von Cmdlets, die eine Remotesitzung aufbauen, wie z. B. das Cmdlet „New-PSSession“.</span><span class="sxs-lookup"><span data-stu-id="53c2e-142">To create a session on the Server01 computer that uses the PS2 session configuration, use the **ConfigurationName** parameter of cmdlets that create a remote session, such as the \`New-PSSession cmdlet.</span></span>

   <span data-ttu-id="53c2e-143">Wenn eine Sitzung gestartet wird, die die Sitzungskonfiguration verwendet, wird Windows PowerShell 2.0 Engine automatisch in die Sitzung geladen.</span><span class="sxs-lookup"><span data-stu-id="53c2e-143">When a session that uses the session configuration starts, the Windows PowerShell 2.0 Engine is automatically loaded into the session.</span></span>

   <span data-ttu-id="53c2e-144">Der folgende Befehl erstellt eine Sitzung auf dem Computer „Server01“, die die PS2-Sitzungskonfiguration verwendet.</span><span class="sxs-lookup"><span data-stu-id="53c2e-144">The following command starts a session on the Server01 computer that uses the PS2 session configuration.</span></span> <span data-ttu-id="53c2e-145">Der Befehl speichert die Sitzung in der Variablen `$s`.</span><span class="sxs-lookup"><span data-stu-id="53c2e-145">The command saves the session in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a><span data-ttu-id="53c2e-146">So starten Sie einen Hintergrundauftrags mit Windows PowerShell 2.0 Engine</span><span class="sxs-lookup"><span data-stu-id="53c2e-146">How to start a background job with the Windows PowerShell 2.0 Engine</span></span>

<span data-ttu-id="53c2e-147">Verwenden Sie den **PSVersion**-Parameter des Cmdlets [Start-Job][] zum Starten eines Hintergrundauftrags mit Windows PowerShell 2.0 Engine.</span><span class="sxs-lookup"><span data-stu-id="53c2e-147">To start a background job with the Windows PowerShell 2.0 Engine, use the **PSVersion** parameter of the [Start-Job][] cmdlet.</span></span>

<span data-ttu-id="53c2e-148">Der folgende Befehl startet einen Hintergrundauftrag mit Windows PowerShell 2.0 Engine</span><span class="sxs-lookup"><span data-stu-id="53c2e-148">The following command starts a background job with the Windows PowerShell 2.0 Engine</span></span>

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

<span data-ttu-id="53c2e-149">Weitere Informationen zu Hintergrundaufträgen finden Sie unter [about_Jobs][].</span><span class="sxs-lookup"><span data-stu-id="53c2e-149">For more information about background jobs, see [about_Jobs][].</span></span>

<!-- link references -->
[Ankündigung]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[announcement]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Ein Vergleich der Sicherheit von Shell- und Skriptsprachen]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[A Comparison of Shell and Scripting Language Security]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Installieren von Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installing Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installieren und Konfigurieren von WMF]: wmf/setup/install-configure.md
[Install and configure WMF]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfiguration
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
