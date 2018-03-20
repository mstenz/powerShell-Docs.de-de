---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Ausführen von Remotebefehlen"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 24648e8f35fbc28c9ba9f9b7176ac23e72ffbe78
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="running-remote-commands"></a><span data-ttu-id="6db86-103">Ausführen von Remotebefehlen</span><span class="sxs-lookup"><span data-stu-id="6db86-103">Running Remote Commands</span></span>

<span data-ttu-id="6db86-104">Mit einem einzigen Windows PowerShell-Befehl können Sie Befehle auf einem oder Hunderten von Computern ausführen.</span><span class="sxs-lookup"><span data-stu-id="6db86-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="6db86-105">Windows PowerShell unterstützt das Remotecomputing mithilfe verschiedener Technologien, unter anderem WMI, RPC und WS-Management.</span><span class="sxs-lookup"><span data-stu-id="6db86-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="6db86-106">Remoting in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6db86-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="6db86-107">PowerShell Core, die neuere Edition von PowerShell für Windows, macOS und Linux, unterstützt WMI, WS-Verwaltung und SSH-Remoting.</span><span class="sxs-lookup"><span data-stu-id="6db86-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="6db86-108">(RPC wird nicht mehr unterstützt.)</span><span class="sxs-lookup"><span data-stu-id="6db86-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="6db86-109">Weitere Informationen zur Einrichtung finden Sie in folgenden Artikeln:</span><span class="sxs-lookup"><span data-stu-id="6db86-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="6db86-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="6db86-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="6db86-111">[WinRM Remoting in PowerShell Core][winrm-remoting]</span><span class="sxs-lookup"><span data-stu-id="6db86-111">[WinRM Remoting in PowerShell Core][winrm-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="6db86-112">Remoting ohne Konfiguration</span><span class="sxs-lookup"><span data-stu-id="6db86-112">Remoting Without Configuration</span></span>
<span data-ttu-id="6db86-113">Viele Windows PowerShell-Cmdlets verfügen über einen „ComputerName“-Parameter, mit dessen Hilfe Sie Daten auf einem oder mehreren Remotecomputern sammeln und Einstellungsänderungen vornehmen können.</span><span class="sxs-lookup"><span data-stu-id="6db86-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="6db86-114">Sie verwenden eine Vielzahl von Kommunikationstechnologien und viele arbeiten ohne besondere Konfiguration unter allen Windows-Betriebssystemen, die Windows PowerShell unterstützen.</span><span class="sxs-lookup"><span data-stu-id="6db86-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="6db86-115">Zu diesem Cmdlets zählen:</span><span class="sxs-lookup"><span data-stu-id="6db86-115">These cmdlets include:</span></span>

* [<span data-ttu-id="6db86-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="6db86-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="6db86-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="6db86-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="6db86-118">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="6db86-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="6db86-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="6db86-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="6db86-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="6db86-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="6db86-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="6db86-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="6db86-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="6db86-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="6db86-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="6db86-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="6db86-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="6db86-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="6db86-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="6db86-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="6db86-126">In der Regel weisen Cmdlets, die Remoting ohne besondere Konfiguration unterstützen, den „ComputerName“-Parameter und nicht den „Session“-Parameter auf.</span><span class="sxs-lookup"><span data-stu-id="6db86-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="6db86-127">Um diese Cmdlets in Ihrer Sitzung zu finden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="6db86-127">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="6db86-128">Windows PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="6db86-128">Windows PowerShell Remoting</span></span>
<span data-ttu-id="6db86-129">Mit dem Windows PowerShell-Remoting, bei dem das WS-Verwaltungsprotokoll verwendet wird, können Sie jeden Windows PowerShell-Befehl auf einem oder mehreren Remotecomputern ausführen.</span><span class="sxs-lookup"><span data-stu-id="6db86-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="6db86-130">Sie können dauerhafte Verbindungen herstellen, interaktive 1:1-Sitzungen 1:1 starten und Skripts auf mehreren Computern ausführen.</span><span class="sxs-lookup"><span data-stu-id="6db86-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="6db86-131">Um Windows PowerShell-Remoting zu verwenden, muss der Remotecomputer für die Remoteverwaltung konfiguriert sein.</span><span class="sxs-lookup"><span data-stu-id="6db86-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="6db86-132">Weitere Informationen und Anweisungen hierzu finden Sie unter [Informationen zu Remoteanforderungen](https://technet.microsoft.com/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="6db86-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/library/dd315349.aspx).</span></span>

<span data-ttu-id="6db86-133">Nachdem Sie Windows PowerShell-Remoting konfiguriert haben, stehen Ihnen viele Remotingstrategien zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="6db86-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="6db86-134">Im weiteren Verlauf dieses Dokuments sind einige davon aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="6db86-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="6db86-135">Weitere Informationen finden Sie unter [about_Remote](https://technet.microsoft.com/library/dd347744.aspx) und [about_Remote_FAQ](https://technet.microsoft.com/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="6db86-135">For more information, see [About Remote](https://technet.microsoft.com/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="6db86-136">Starten einer interaktiven Sitzung</span><span class="sxs-lookup"><span data-stu-id="6db86-136">Start an Interactive Session</span></span>
<span data-ttu-id="6db86-137">Um eine interaktive Sitzung mit einem einzelnen Remotecomputer zu starten, verwenden Sie das Cmdlet [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).</span><span class="sxs-lookup"><span data-stu-id="6db86-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="6db86-138">Um beispielsweise eine interaktive Sitzung mit dem Remotecomputer „Server01“ zu starten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="6db86-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="6db86-139">Die Eingabeaufforderung ändert sich, und es wird der Name des Computers angezeigt, mit dem Sie verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="6db86-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="6db86-140">Von nun an werden alle Befehle, die Sie an der Eingabeaufforderung eingeben, auf dem Remotecomputer ausgeführt, und die Ergebnisse werden auf dem lokalen Computer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6db86-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="6db86-141">Um die interaktive Sitzung zu beenden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="6db86-141">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="6db86-142">Weitere Informationen über die Cmdlets „Enter-PSSession“ und „Exit-PSSession“ Sie unter [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) und [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="6db86-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="6db86-143">Ausführen eines Remotebefehls</span><span class="sxs-lookup"><span data-stu-id="6db86-143">Run a Remote Command</span></span>
<span data-ttu-id="6db86-144">Zum Ausführen eines Befehls auf einem oder mehreren Remotecomputern verwenden Sie das Cmdlet [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="6db86-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="6db86-145">Um beispielsweise einen [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806)-Befehl auf den Remotecomputern „Server01“ und „Server02“ auszuführen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="6db86-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="6db86-146">Die Ausgabe wird an den Computer zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="6db86-146">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```
<span data-ttu-id="6db86-147">Weitere Informationen zum Cmdlet „Invoke-Command“ finden Sie unter [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="6db86-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="6db86-148">Ausführen eines Skripts</span><span class="sxs-lookup"><span data-stu-id="6db86-148">Run a Script</span></span>
<span data-ttu-id="6db86-149">Zum Ausführen eines Skripts auf einem oder mehreren Remotecomputern verwenden Sie den Parameter „FilePath“ des Cmdlets „Invoke-Command“.</span><span class="sxs-lookup"><span data-stu-id="6db86-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="6db86-150">Das Skript muss sich auf dem lokalen Computer befinden oder für diesen verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="6db86-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="6db86-151">Die Ergebnisse werden an den lokalen Computer zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="6db86-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="6db86-152">Der folgende Befehl führt beispielsweise das Skript „DiskCollect.ps1“ auf den Remotecomputern „Server01“ und „Server02“ aus.</span><span class="sxs-lookup"><span data-stu-id="6db86-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="6db86-153">Weitere Informationen zum Cmdlet „Invoke-Command“ finden Sie unter [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="6db86-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="6db86-154">Herstellen einer dauerhaften Verbindung</span><span class="sxs-lookup"><span data-stu-id="6db86-154">Establish a Persistent Connection</span></span>
<span data-ttu-id="6db86-155">Um eine Reihe verwandter Befehle auszuführen, die Daten gemeinsam nutzen, erstellen Sie eine Sitzung auf dem Remotecomputer, und verwenden Sie dann das Cmdlet „Invoke-Command“ zum Ausführen der Befehle in der Sitzung, die Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="6db86-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="6db86-156">Um eine Remotesitzung zu erstellen, verwenden Sie das Cmdlet „New-PSSession“.</span><span class="sxs-lookup"><span data-stu-id="6db86-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="6db86-157">Mit dem folgenden Befehl erstellen Sie z. B. eine Remotesitzung auf dem Computer "Server01" und eine weitere Remotesitzung auf dem Computer "Server02".</span><span class="sxs-lookup"><span data-stu-id="6db86-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="6db86-158">Es speichert die Sitzungsobjekte in der Variablen „$s“.</span><span class="sxs-lookup"><span data-stu-id="6db86-158">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="6db86-159">Nachdem die Sitzungen nun hergestellt sind, können Sie jeden beliebigen Befehl in diesen ausführen.</span><span class="sxs-lookup"><span data-stu-id="6db86-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="6db86-160">Und da die Sitzungen dauerhaft sind, können Sie Daten in einem Befehl sammeln und diese in einem nachfolgenden Befehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="6db86-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="6db86-161">Beispielsweise führt der folgende Befehl einen „Get-HotFix“-Befehl in den Sitzungen in der Variablen „$s“ aus und speichert die Ergebnisse dann in der Variablen „$h“.</span><span class="sxs-lookup"><span data-stu-id="6db86-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="6db86-162">Die Variable „$h“ wird in jeder der Sitzungen in „$s“ erstellt, ist jedoch in der lokalen Sitzung nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="6db86-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="6db86-163">Sie können die Daten in der Variablen „$h“ jetzt in nachfolgenden Befehle verwenden, wie z. B. dem folgenden.</span><span class="sxs-lookup"><span data-stu-id="6db86-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="6db86-164">Die Ergebnisse werden auf dem lokalen Computer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6db86-164">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="6db86-165">Erweitertes Remoting</span><span class="sxs-lookup"><span data-stu-id="6db86-165">Advanced Remoting</span></span>
<span data-ttu-id="6db86-166">Dies sind nur die grundlegenden Möglichkeiten, die die Remoteverwaltung von Windows PowerShell bietet.</span><span class="sxs-lookup"><span data-stu-id="6db86-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="6db86-167">Mithilfe von Cmdlets, die mit Windows PowerShell installiert werden, können Sie Remotesitzungen sowohl von lokaler Seite als auch von Remoteseite aus einrichten und konfigurieren, angepasste und eingeschränkte Sitzungen erstellen, Benutzern über eine Remotesitzung den Import von Befehlen ermöglichen, die tatsächlich implizit in der Remotesitzung ausgeführt werden, die Sicherheit einer Remotesitzung konfigurieren und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="6db86-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="6db86-168">Um die Remotekonfiguration zu vereinfachen, umfasst Windows PowerShell einen WSMan-Anbieter.</span><span class="sxs-lookup"><span data-stu-id="6db86-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="6db86-169">Das vom Anbieter erstellte Laufwerk „WSMAN:“ ermöglicht Ihnen, durch eine Hierarchie von Konfigurationseinstellungen auf dem lokalen Computer und den Remotecomputern zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="6db86-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="6db86-170">Weitere Informationen zum WSMan-Anbieter finden Sie unter [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) und [About_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), oder indem Sie in der Windows PowerShell-Konsole „Get-Help wsman“ eingeben.</span><span class="sxs-lookup"><span data-stu-id="6db86-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="6db86-171">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="6db86-171">For more information, see:</span></span>
- [<span data-ttu-id="6db86-172">Häufig gestellte Fragen zu Remote</span><span class="sxs-lookup"><span data-stu-id="6db86-172">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="6db86-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6db86-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="6db86-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="6db86-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="6db86-175">Hilfe zu Remotingfehlern finden Sie unter [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="6db86-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="6db86-176">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6db86-176">See Also</span></span>
- [<span data-ttu-id="6db86-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="6db86-177">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="6db86-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="6db86-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="6db86-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="6db86-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="6db86-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="6db86-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="6db86-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="6db86-181">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="6db86-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="6db86-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="6db86-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="6db86-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="6db86-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="6db86-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="6db86-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="6db86-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="6db86-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6db86-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="6db86-187">WSMan-Anbieter</span><span class="sxs-lookup"><span data-stu-id="6db86-187">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-resmoting]: SSH-Remoting-in-PowerShell-Core.md
