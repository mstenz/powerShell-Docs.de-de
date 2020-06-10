---
title: Erste Schritte mit PowerShell
description: Informationen, wo Sie als neuer Benutzer PowerShell finden und wie Sie sie starten können.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 0f72fb5baf5b829142b18ed774261e9b3b66291b
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438021"
---
# <a name="chapter-1---getting-started-with-powershell"></a><span data-ttu-id="c823b-103">Kapitel 1: Erste Schritte mit PowerShell</span><span class="sxs-lookup"><span data-stu-id="c823b-103">Chapter 1 - Getting Started with PowerShell</span></span>

<span data-ttu-id="c823b-104">Ich stelle häufig fest, dass bei Referenten auf Konferenzen und bei Benutzergruppenbesprechungen PowerShell bereits läuft, wenn sie mit einer Präsentation für Einsteiger beginnen.</span><span class="sxs-lookup"><span data-stu-id="c823b-104">I often find that presenters at conferences and user group meetings already have PowerShell running when they start entry-level presentations.</span></span> <span data-ttu-id="c823b-105">Dieses Buch beginnt mit dem Beantworten der Fragen, die ich in solchen Sitzungen von Teilnehmern gehört habe, die PowerShell noch nie benutzt hatten.</span><span class="sxs-lookup"><span data-stu-id="c823b-105">This book begins by answering the questions I've heard attendees who haven't previously used PowerShell ask in those sessions.</span></span>

<span data-ttu-id="c823b-106">Dieses Kapitel konzentriert sich insbesondere auf das Auffinden und Starten von PowerShell sowie das Lösen einiger der anfänglichen Probleme, die bei neuen Benutzern von PowerShell auftreten können.</span><span class="sxs-lookup"><span data-stu-id="c823b-106">Specifically, this chapter focuses on finding and launching PowerShell, and solving some of the initial pain points that new users experience with PowerShell.</span></span> <span data-ttu-id="c823b-107">Stellen Sie sicher, dass Sie die in diesem Kapitel gezeigten Beispiele auf Ihrem Windows 10-Laborumgebungscomputer durchlaufen und nachvollziehen.</span><span class="sxs-lookup"><span data-stu-id="c823b-107">Be sure to follow along and walk through the examples shown in this chapter on your Windows 10 lab environment computer.</span></span>

## <a name="what-do-i-need-to-get-started-with-powershell"></a><span data-ttu-id="c823b-108">Was benötige ich für den Einstieg bei PowerShell?</span><span class="sxs-lookup"><span data-stu-id="c823b-108">What do I need to get started with PowerShell?</span></span>

<span data-ttu-id="c823b-109">Alle modernen Versionen von Windows-Betriebssystemen werden mit einer vorinstallierten PowerShell ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="c823b-109">All modern versions of Windows operating systems ship with PowerShell installed.</span></span> <span data-ttu-id="c823b-110">Wenn Sie eine ältere Version als 5.1 ausführen, sollten Sie die neueste Version installieren.</span><span class="sxs-lookup"><span data-stu-id="c823b-110">If you're running a version older than 5.1, you should install the latest version.</span></span>

- <span data-ttu-id="c823b-111">Informationen für ein Upgrade auf Windows PowerShell 5.1 finden Sie unter [Aktualisieren einer vorhandenen Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="c823b-111">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][]</span></span>
- <span data-ttu-id="c823b-112">Informationen zur Installation der neuesten Version von PowerShell finden Sie unter [Installieren von PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="c823b-112">To install the latest version of PowerShell, see [Installing PowerShell][]</span></span>

## <a name="where-do-i-find-powershell"></a><span data-ttu-id="c823b-113">Wo finde ich PowerShell?</span><span class="sxs-lookup"><span data-stu-id="c823b-113">Where do I find PowerShell?</span></span>

<span data-ttu-id="c823b-114">Die einfachste Möglichkeit, um PowerShell unter Windows 10 zu finden, besteht darin, **PowerShell** in die Suchleiste einzugeben, wie in Abbildung 1-1 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c823b-114">The easiest way to find PowerShell on Windows 10 is to type **PowerShell** into the search bar as shown in Figure 1-1.</span></span>

![Abbildung 1-1](media/figure1-1.png)

<span data-ttu-id="c823b-116">Beachten Sie, dass in Abbildung 1-1 vier verschiedene Tastenkombinationen für PowerShell gezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c823b-116">Notice that four different shortcuts for PowerShell are shown in Figure 1-1.</span></span> <span data-ttu-id="c823b-117">Auf dem Computer, der zu Demonstrationszwecken in diesem Buch verwendet wird, wird die 64-Bit-Version von Windows 10 ausgeführt, weshalb es eine 64-Bit-Version der PowerShell-Konsole und der PowerShell ISE (Integrated Scripting Environment) gibt sowie eine 32-Bit-Version von diesen beiden Komponenten, die durch das Suffix (x86) bei den Tastenkombinationen kenntlich ist.</span><span class="sxs-lookup"><span data-stu-id="c823b-117">The computer used for demonstration purposes in this book is running the 64-bit version of Windows 10 so there's a 64-bit version of the PowerShell console and the PowerShell ISE (Integrated Scripting Environment), and a 32-bit version of each one as denoted by the (x86) suffix on the shortcuts.</span></span> <span data-ttu-id="c823b-118">Wenn Sie eine 32-Bit-Version von Windows 10 ausführen, haben Sie nur zwei Tastenkombinationen.</span><span class="sxs-lookup"><span data-stu-id="c823b-118">If you happen to be running a 32-bit version of Windows 10, you'll only have two shortcuts.</span></span> <span data-ttu-id="c823b-119">Diese Elemente haben nicht das Suffix (x86) und sind 32-Bit-Versionen.</span><span class="sxs-lookup"><span data-stu-id="c823b-119">Those items don't have the (x86) suffix, but are 32-bit versions.</span></span> <span data-ttu-id="c823b-120">Wenn Sie über ein 64-Bit-Betriebssystem verfügen, empfehle ich Ihnen, die 64-Bit-Version von PowerShell auszuführen, es sei denn, Sie haben einen bestimmten Grund für die Ausführung der 32-Bit-Version.</span><span class="sxs-lookup"><span data-stu-id="c823b-120">If you have a 64-bit operating system, my recommendation is to run the 64-bit version of PowerShell unless you have a specific reason for running the 32-bit version.</span></span>

<span data-ttu-id="c823b-121">Informationen zum Starten von PowerShell auf anderen Versionen von Windows finden Sie unter [Starten von Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="c823b-121">For information about starting PowerShell on other versions of Windows, see [Starting Windows PowerShell][].</span></span>

## <a name="how-do-i-launch-powershell"></a><span data-ttu-id="c823b-122">Wie starte ich PowerShell?</span><span class="sxs-lookup"><span data-stu-id="c823b-122">How do I launch PowerShell?</span></span>

<span data-ttu-id="c823b-123">In den von mir unterstützten Produktionsumgebungen für Unternehmen verwende ich drei verschiedene Active Directory-Benutzerkonten.</span><span class="sxs-lookup"><span data-stu-id="c823b-123">In the production enterprise environments that I support, I use three different Active Directory user accounts.</span></span> <span data-ttu-id="c823b-124">Ich benutze eben diese Konten in der in diesem Buch verwendeten Laborumgebung.</span><span class="sxs-lookup"><span data-stu-id="c823b-124">I've mirrored those accounts in the lab environment used in this book.</span></span> <span data-ttu-id="c823b-125">Ich melde mich bei dem Windows 10-Computer als Domänenbenutzer an, der kein Domänen- oder lokaler Administrator ist.</span><span class="sxs-lookup"><span data-stu-id="c823b-125">I log into the Windows 10 computer as a domain user who is not a domain or local administrator.</span></span>

<span data-ttu-id="c823b-126">Ich habe die PowerShell-Konsole durch Klicken auf die Verknüpfung „Windows PowerShell“ gestartet, wie in Abbildung 1-1 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c823b-126">I've launched the PowerShell console by clicking on the "Windows PowerShell" shortcut as shown in Figure 1-1.</span></span>

![Abbildung 1-4](media/figure1-4.png)

<span data-ttu-id="c823b-128">Beachten Sie, dass in der Titelleiste der PowerShell-Konsole „Windows PowerShell“ steht, wie in Abbildung 1-4 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c823b-128">Notice that the title bar of the PowerShell console says "Windows PowerShell" as shown in Figure 1-4.</span></span> <span data-ttu-id="c823b-129">Einige Befehle werden zwar einwandfrei ausgeführt, doch PowerShell kann nicht die Benutzerkontensteuerung (User Access Control, UAC) nutzen.</span><span class="sxs-lookup"><span data-stu-id="c823b-129">Some commands run fine, but PowerShell can't participate in User Access Control (UAC).</span></span> <span data-ttu-id="c823b-130">Dies bedeutet, dass es nicht zur Erhöhung der Rechte bei Aufgaben auffordern kann, die die Genehmigung eines Administrators erfordern.</span><span class="sxs-lookup"><span data-stu-id="c823b-130">That means it's unable to prompt for elevation for tasks that require the approval of an administrator.</span></span>
<span data-ttu-id="c823b-131">Die folgende Fehlermeldung wird generiert:</span><span class="sxs-lookup"><span data-stu-id="c823b-131">The following error message is generated:</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

<span data-ttu-id="c823b-132">Die Lösung für dieses Problem besteht darin, PowerShell als Domänenbenutzer auszuführen, der lokaler Administrator ist.</span><span class="sxs-lookup"><span data-stu-id="c823b-132">The solution to this problem is to run PowerShell as a domain user who is a local administrator.</span></span>
<span data-ttu-id="c823b-133">Auf diese Weise ist mein zweites Domänenbenutzerkonto konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="c823b-133">This is how my second domain user account is configured.</span></span> <span data-ttu-id="c823b-134">Bei Verwendung des Prinzips der geringsten Rechte sollte dieses Konto WEDER Domänenadministrator sein NOCH über erhöhte Rechte in der Domäne verfügen.</span><span class="sxs-lookup"><span data-stu-id="c823b-134">Using the principal of least privilege, this account should NOT be a domain administrator, or have any elevated privileges in the domain.</span></span>

<span data-ttu-id="c823b-135">Schließen Sie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c823b-135">Close PowerShell.</span></span> <span data-ttu-id="c823b-136">Starten Sie die PowerShell-Konsole neu, wobei Sie aber diesmal mit der rechten Maustaste auf die Verknüpfung **Windows PowerShell** klicken, und wählen Sie **Als Administrator ausführen** aus, wie in Abbildung 1-5 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c823b-136">Relaunch the PowerShell console, except this time right-click on the **Windows PowerShell** shortcut and select **Run as administrator** as shown in Figure 1-5.</span></span>

![Abbildung 1-5](media/figure1-5.png)

<span data-ttu-id="c823b-138">Wenn Sie als normaler Benutzer bei Windows angemeldet sind, werden Sie zur Eingabe von Anmeldeinformationen aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="c823b-138">If you're logged into Windows as a normal user, you'll be prompted for credentials.</span></span> <span data-ttu-id="c823b-139">Ich gebe die Anmeldeinformationen für mein Benutzerkonto ein, das Domänenbenutzer und lokaler Administrator ist, wie in Abbildung 1-6 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c823b-139">I'll enter the credentials for my user account who is a domain user and local admin as shown in Figure 1-6.</span></span>

![Abbildung 1-6](media/figure1-6.png)

<span data-ttu-id="c823b-141">Nachdem PowerShell als Administrator neu gestartet wurde, sollte in der Titelleiste „Administrator: Windows PowerShell“ stehen, wie in Abbildung 1-7 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c823b-141">Once PowerShell is relaunched as an administrator, the title bar should say "Administrator: Windows PowerShell" as shown in Figure 1-7.</span></span>

![Abbildung 1-7](media/figure1-7.png)

<span data-ttu-id="c823b-143">Nachdem PowerShell nun mit erhöhten Rechten als lokaler Administrator ausgeführt wird, stellt die Benutzerkontensteuerung kein Problem mehr dar, wenn auf dem lokalen Computer ein Befehl ausgeführt wird, der normalerweise eine Aufforderung zur Erhöhung der Rechte erfordern würde.</span><span class="sxs-lookup"><span data-stu-id="c823b-143">Now that PowerShell is being run elevated as a local administrator, UAC will no longer be a problem when a command is run on the local computer that would normally require a prompt for elevation.</span></span> <span data-ttu-id="c823b-144">Denken Sie jedoch daran, dass jeder Befehl, der aus dieser PowerShell-Konsoleninstanz mit erhöhten Rechten ausgeführt wird, ebenfalls mit diesen erhöhten Rechten ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c823b-144">Keep in mind though that any command run from this elevated instance of the PowerShell console, also runs elevated.</span></span>

<span data-ttu-id="c823b-145">Um das Auffinden von PowerShell und deren Start als Administrator zu vereinfachen, empfehle ich, sie an die Taskleiste anzuheften und für sie festzulegen, dass Sie bei jeder Ausführung automatisch als Administrator gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="c823b-145">To simplify finding PowerShell and launching it as an administrator, I recommend pinning it to the taskbar and setting it to automatically launch as an admin each time it's run.</span></span>

<span data-ttu-id="c823b-146">Suchen Sie erneut nach PowerShell, klicken Sie nur diesmal mit der rechten Maustaste darauf, und wählen Sie „An Taskleiste anheften“ aus, wie in Abbildung 1-8 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c823b-146">Search for PowerShell again, except this time right-click on it and select "Pin to taskbar" as shown in Figure 1-8.</span></span>

![Abbildung 1-8](media/figure1-8.png)

<span data-ttu-id="c823b-148">Klicken Sie mit der rechten Maustaste auf die PowerShell-Verknüpfung, die nun an die Taskleiste angeheftet ist, und wählen Sie „Eigenschaften“ aus, wie in Abbildung 1-9 dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c823b-148">Right-click on the PowerShell shortcut that's now pinned to the taskbar and select properties as shown in Figure 1-9.</span></span>

![Abbildung 1-9](media/figure1-9.png)

<span data-ttu-id="c823b-150">Klicken Sie auf „Erweitert“, wie durch #1 in Abbildung 1-10 markiert, aktivieren Sie dann das Kontrollkästchen „Als Administrator ausführen“, wie durch #2 in Abbildung 1-10 markiert, und klicken Sie dann zweimal auf „OK“, um die Änderungen zu übernehmen und beide Dialogfelder zu schließen.</span><span class="sxs-lookup"><span data-stu-id="c823b-150">Click on "Advanced" as denoted by #1 in Figure 1-10, then check the "Run as administrator" checkbox as denoted by #2 in Figure 1-10, and then click OK twice to accept the changes and exit out of both dialog boxes.</span></span>

![Abbildung 1-10](media/figure1-10.png)

<span data-ttu-id="c823b-152">Sie müssen sich nun keine Gedanken mehr über das Auffinden von PowerShell zu machen oder darüber, ob sie als Administrator ausgeführt wird oder nicht.</span><span class="sxs-lookup"><span data-stu-id="c823b-152">You'll never have to worry about finding PowerShell or whether or not it's running as an administrator again.</span></span>

<span data-ttu-id="c823b-153">Wenn Sie PowerShell mit erhöhten Rechten als Administrator ausführen, um Probleme mit der Benutzerkontensteuerung zu verhindern, wirkt sich dies nur auf Befehle aus, die auf dem lokalen Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c823b-153">Running PowerShell elevated as an administrator to prevent having problems with UAC only impacts commands that are run against the local computer.</span></span> <span data-ttu-id="c823b-154">Es hat keine Auswirkungen auf Befehle, die sich auf Remotecomputer beziehen.</span><span class="sxs-lookup"><span data-stu-id="c823b-154">It has no effect on commands that target remote computers.</span></span>

## <a name="what-version-of-powershell-am-i-running"></a><span data-ttu-id="c823b-155">Welche PowerShell-Version führe ich aus?</span><span class="sxs-lookup"><span data-stu-id="c823b-155">What version of PowerShell am I running?</span></span>

<span data-ttu-id="c823b-156">Es gibt eine Reihe automatischer Variablen in PowerShell, die Zustandsinformationen speichern.</span><span class="sxs-lookup"><span data-stu-id="c823b-156">There are a number of automatic variables in PowerShell that store state information.</span></span> <span data-ttu-id="c823b-157">Eine dieser Variablen ist `$PSVersionTable`, die eine Hashtabelle enthält, die zum Anzeigen der relevanten PowerShell-Versionsinformationen verwendet werden kann:</span><span class="sxs-lookup"><span data-stu-id="c823b-157">One of these variables is `$PSVersionTable`, which contains a hashtable that can be used to display the relevant PowerShell version information:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="c823b-158">Neuere Versionen von Windows PowerShell werden als Bestandteil des Windows Management Frameworks (WMF) verteilt.</span><span class="sxs-lookup"><span data-stu-id="c823b-158">Newer versions of Windows PowerShell are distributed as part of the Windows Management Framework (WMF).</span></span> <span data-ttu-id="c823b-159">In Abhängigkeit von der WMF-Version ist eine bestimmte Version von .NET Framework erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c823b-159">A specific version of the .NET Framework is required depending on the WMF version.</span></span> <span data-ttu-id="c823b-160">Informationen für ein Upgrade auf Windows PowerShell 5.1 finden Sie unter [Aktualisieren einer vorhandenen Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="c823b-160">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][].</span></span>

## <a name="execution-policy"></a><span data-ttu-id="c823b-161">Ausführungsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="c823b-161">Execution Policy</span></span>

<span data-ttu-id="c823b-162">Entgegen der gängigen Annahme, stellt die Ausführungsrichtlinie in PowerShell keine Sicherheitsgrenze dar.</span><span class="sxs-lookup"><span data-stu-id="c823b-162">Contrary to popular belief, the execution policy in PowerShell is not a security boundary.</span></span> <span data-ttu-id="c823b-163">Sie ist darauf ausgelegt, einen Benutzer daran zu hindern, unwissentlich ein Skript auszuführen.</span><span class="sxs-lookup"><span data-stu-id="c823b-163">It's designed to prevent a user from unknowingly running a script.</span></span> <span data-ttu-id="c823b-164">Ein entschlossener Benutzer kann die Ausführungsrichtlinie in PowerShell mühelos umgehen.</span><span class="sxs-lookup"><span data-stu-id="c823b-164">A determined user can easily bypass the execution policy in PowerShell.</span></span> <span data-ttu-id="c823b-165">In Tabelle 1-2 wird die Standardausführungsrichtlinie für die aktuellen Windows-Betriebssysteme angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c823b-165">Table 1-2 shows the default execution policy for current Windows operating systems.</span></span>

| <span data-ttu-id="c823b-166">Windows-Betriebssystemversion</span><span class="sxs-lookup"><span data-stu-id="c823b-166">Windows Operating System Version</span></span> | <span data-ttu-id="c823b-167">Standardausführungsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="c823b-167">Default Execution Policy</span></span> |
| -------------------------------- | ------------------------ |
| <span data-ttu-id="c823b-168">Server 2019</span><span class="sxs-lookup"><span data-stu-id="c823b-168">Server 2019</span></span>                      | <span data-ttu-id="c823b-169">Remote signiert</span><span class="sxs-lookup"><span data-stu-id="c823b-169">Remote Signed</span></span>            |
| <span data-ttu-id="c823b-170">Server 2016</span><span class="sxs-lookup"><span data-stu-id="c823b-170">Server 2016</span></span>                      | <span data-ttu-id="c823b-171">Remote signiert</span><span class="sxs-lookup"><span data-stu-id="c823b-171">Remote Signed</span></span>            |
| <span data-ttu-id="c823b-172">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c823b-172">Windows 10</span></span>                       | <span data-ttu-id="c823b-173">Eingeschränkt</span><span class="sxs-lookup"><span data-stu-id="c823b-173">Restricted</span></span>               |

<span data-ttu-id="c823b-174">Unabhängig von der Einstellung der Ausführungsrichtlinie können alle PowerShell-Befehle interaktiv ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c823b-174">Regardless of the execution policy setting, any PowerShell command can be run interactively.</span></span> <span data-ttu-id="c823b-175">Die Ausführungsrichtlinie gilt nur für Befehle, die in einem Skript ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="c823b-175">The execution policy only affects commands running in a script.</span></span> <span data-ttu-id="c823b-176">Das Cmdlet `Get-ExecutionPolicy` wird verwendet, um zu bestimmen, wie die aktuelle Ausführungsrichtlinieneinstellung lautet, und das Cmdlet `Set-ExecutionPolicy` wird verwendet, um die Ausführungsrichtlinie zu ändern.</span><span class="sxs-lookup"><span data-stu-id="c823b-176">The `Get-ExecutionPolicy` cmdlet is used to determine what the current execution policy setting is and the `Set-ExecutionPolicy` cmdlet is used to change the execution policy.</span></span> <span data-ttu-id="c823b-177">Meine Empfehlung ist es, die **RemoteSigned**-Richtlinie zu verwenden, die erfordert, dass heruntergeladene Skripts von einem vertrauenswürdigen Herausgeber signiert sind, damit Sie ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="c823b-177">My recommendation is to use the **RemoteSigned** policy, which requires downloaded scripts to be signed by a trusted publisher in order to be run.</span></span>

<span data-ttu-id="c823b-178">Überprüfen Sie die aktuelle Ausführungsrichtlinie:</span><span class="sxs-lookup"><span data-stu-id="c823b-178">Check the current execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

<span data-ttu-id="c823b-179">PowerShell-Skripts können gar nicht ausgeführt werden, wenn die Ausführungsrichtlinie auf **Eingeschränkt** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c823b-179">PowerShell scripts can't be run at all when the execution policy is set to **Restricted**.</span></span> <span data-ttu-id="c823b-180">Dies ist die Standardeinstellung in allen Windows-Clientbetriebssystemen.</span><span class="sxs-lookup"><span data-stu-id="c823b-180">This is the default setting on all Windows client operating systems.</span></span> <span data-ttu-id="c823b-181">Um das Problem zu veranschaulichen, speichern Sie den folgenden Code als `.ps1`-Datei namens `Stop-TimeService.ps1`.</span><span class="sxs-lookup"><span data-stu-id="c823b-181">To demonstrate the problem, save the following code as a `.ps1` file named `Stop-TimeService.ps1`.</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

<span data-ttu-id="c823b-182">Dieser Befehl wird interaktiv ohne Fehler ausgeführt, solange PowerShell mit erhöhten Rechten als Administrator ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c823b-182">That command runs interactively without error as long as PowerShell is run elevated as an administrator.</span></span> <span data-ttu-id="c823b-183">Sobald er aber als Skriptdatei gespeichert wird und Sie versuchen, das Skript auszuführen, wird ein Fehler generiert:</span><span class="sxs-lookup"><span data-stu-id="c823b-183">But as soon as it's saved as a script file and you try to execute the script, it generates an error:</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="c823b-184">Beachten Sie, dass der Fehler, der im vorherigen Resultset zu sehen ist, genau angibt, wo das Problem liegt (das Ausführen von Skripts ist auf diesem System deaktiviert).</span><span class="sxs-lookup"><span data-stu-id="c823b-184">Notice that the error shown in the previous set of results tells you exactly what the problem is (running scripts is disabled on this system).</span></span> <span data-ttu-id="c823b-185">Wenn Sie einen Befehl in PowerShell ausführen, der eine Fehlermeldung generiert, achten Sie darauf, dass Sie die Fehlermeldung lesen, anstatt einfach nur den Befehl erneut auszuführen und zu hoffen, dass er diesmal erfolgreich ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c823b-185">When you run a command in PowerShell that generates an error message, be sure to read the error message instead of just rerunning the command and hoping that it runs successfully.</span></span>

<span data-ttu-id="c823b-186">Ändern Sie die PowerShell-Ausführungsrichtlinie auf „Remote signiert“.</span><span class="sxs-lookup"><span data-stu-id="c823b-186">Change the PowerShell execution policy to remote signed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

<span data-ttu-id="c823b-187">Lesen Sie unbedingt die Warnung, die angezeigt wird, wenn Sie die Ausführungsrichtlinie ändern.</span><span class="sxs-lookup"><span data-stu-id="c823b-187">Be sure to read the warning that's displayed when changing the execution policy.</span></span> <span data-ttu-id="c823b-188">Ich empfehle Ihnen außerdem, sich das Hilfethema [about_Execution_Policies][] anzusehen, um sicherzustellen, dass Sie die Sicherheitsimplikationen verstehen, die mit der Änderung der Ausführungsrichtlinie einhergehen.</span><span class="sxs-lookup"><span data-stu-id="c823b-188">I also recommend taking a look at the [about_Execution_Policies][] help topic to make sure you understand the security implications of changing the execution policy.</span></span>

<span data-ttu-id="c823b-189">Nun, da die Ausführungsrichtlinie auf **RemoteSigned** festgelegt ist, wird das Skript `Stop-TimeService.ps1` fehlerfrei ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c823b-189">Now that the execution policy has been set to **RemoteSigned**, the `Stop-TimeService.ps1` script runs error free.</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

<span data-ttu-id="c823b-190">Stellen Sie sicher, dass Sie Ihren Windows-Zeitdienst starten, bevor Sie fortfahren, da sonst unvorhersehbare Probleme auftreten können.</span><span class="sxs-lookup"><span data-stu-id="c823b-190">Be sure to start your Windows Time service before continuing otherwise you may run into unforeseen problems.</span></span>

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a><span data-ttu-id="c823b-191">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="c823b-191">Summary</span></span>

<span data-ttu-id="c823b-192">In diesem Kapitel haben Sie erfahren, wie Sie PowerShell finden und starten, und wie Sie eine Verknüpfung erstellen, mit der PowerShell als Administrator gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="c823b-192">In this chapter, you've learned how to find and launch PowerShell, and how to create a shortcut that launches PowerShell as an administrator.</span></span> <span data-ttu-id="c823b-193">Außerdem haben Sie Informationen über die Standardausführungsrichtlinie erhalten und erfahren, wie man diese ändert.</span><span class="sxs-lookup"><span data-stu-id="c823b-193">You've also learned about the default execution policy and how to change it.</span></span>

## <a name="review"></a><span data-ttu-id="c823b-194">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="c823b-194">Review</span></span>

1. <span data-ttu-id="c823b-195">Wie bestimmen Sie, welche PowerShell-Version auf einem Computer ausgeführt wird?</span><span class="sxs-lookup"><span data-stu-id="c823b-195">How do you determine what PowerShell version a computer is running?</span></span>
1. <span data-ttu-id="c823b-196">Warum ist es wichtig, PowerShell mit erhöhten Rechten als Administrator zu starten?</span><span class="sxs-lookup"><span data-stu-id="c823b-196">Why is it important to launch PowerShell elevated as an administrator?</span></span>
1. <span data-ttu-id="c823b-197">Wie bestimmen Sie die aktuelle Ausführungsrichtlinie von PowerShell?</span><span class="sxs-lookup"><span data-stu-id="c823b-197">How do you determine the current PowerShell execution policy?</span></span>
1. <span data-ttu-id="c823b-198">Was verhindert die Standardausführungsrichtlinie von PowerShell auf Windows-Clientcomputern?</span><span class="sxs-lookup"><span data-stu-id="c823b-198">What does the default PowerShell execution policy on Windows client computers prevent from occurring?</span></span>
1. <span data-ttu-id="c823b-199">Wie ändern Sie die PowerShell-Ausführungsrichtlinie?</span><span class="sxs-lookup"><span data-stu-id="c823b-199">How do you change the PowerShell execution policy?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="c823b-200">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="c823b-200">Recommended Reading</span></span>

<span data-ttu-id="c823b-201">Wenn Sie weitere Informationen zu den in diesem Kapitel behandelten Themen wünschen, empfehle ich Ihnen, die folgenden PowerShell-Hilfethemen zu lesen.</span><span class="sxs-lookup"><span data-stu-id="c823b-201">For those who want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="c823b-202">[about_Automatic_Variables][]</span><span class="sxs-lookup"><span data-stu-id="c823b-202">[about_Automatic_Variables][]</span></span>
- <span data-ttu-id="c823b-203">[about_Execution_Policies][]</span><span class="sxs-lookup"><span data-stu-id="c823b-203">[about_Execution_Policies][]</span></span>

<span data-ttu-id="c823b-204">Im nächsten Kapitel erfahren Sie mehr über die Auffindbarkeit von Befehlen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c823b-204">In the next chapter, you'll learn about the discoverability of commands in PowerShell.</span></span> <span data-ttu-id="c823b-205">Einer der Aspekte, der behandelt wird, ist, wie Sie PowerShell so aktualisieren, dass diese Hilfethemen direkt innerhalb der PowerShell angezeigt werden können, anstatt sie im Internet lesen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="c823b-205">One of the things that will be covered is how to update PowerShell so those help topics can be viewed right from within PowerShell instead of having to view them on the internet.</span></span>

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Execution_Policies]: /powershell//powershell/module/microsoft.powershell.core/about/about_execution_policies
[Aktualisieren einer vorhandenen Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Upgrading existing Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Installieren von PowerShell]: /powershell/scripting/install/installing-powershell
[Installing PowerShell]: /powershell/scripting/install/installing-powershell
[Starten von Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
[Starting Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
