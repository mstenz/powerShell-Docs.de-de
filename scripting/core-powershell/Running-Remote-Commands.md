---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Ausführen von Remotebefehlen"
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: a8645a348ebc25533f60cd049ed5872e49565b96
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="1d7bf-103">Ausführen von Remotebefehlen</span><span class="sxs-lookup"><span data-stu-id="1d7bf-103">Running Remote Commands</span></span>
<span data-ttu-id="1d7bf-104">Mit einem einzigen Windows PowerShell-Befehl können Sie Befehle auf einem oder Hunderten von Computern ausführen.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="1d7bf-105">Windows PowerShell unterstützt das Remotecomputing mithilfe verschiedener Technologien, unter anderem WMI, RPC und WS-Management.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="1d7bf-106">Remoting ohne Konfiguration</span><span class="sxs-lookup"><span data-stu-id="1d7bf-106">Remoting Without Configuration</span></span>
<span data-ttu-id="1d7bf-107">Viele Windows PowerShell-Cmdlets verfügen über einen „ComputerName“-Parameter, mit dessen Hilfe Sie Daten auf einem oder mehreren Remotecomputern sammeln und Einstellungsänderungen vornehmen können.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="1d7bf-108">Sie verwenden eine Vielzahl von Kommunikationstechnologien und viele arbeiten ohne besondere Konfiguration unter allen Windows-Betriebssystemen, die Windows PowerShell unterstützen.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="1d7bf-109">Zu diesem Cmdlets zählen:</span><span class="sxs-lookup"><span data-stu-id="1d7bf-109">These cmdlets include:</span></span>

-   [<span data-ttu-id="1d7bf-110">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="1d7bf-110">Restart-Computer</span></span>](https://technet.microsoft.com/en-us/library/dd315301.aspx)

-   [<span data-ttu-id="1d7bf-111">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="1d7bf-111">Test-Connection</span></span>](https://technet.microsoft.com/en-us/library/dd315259.aspx)

-   [<span data-ttu-id="1d7bf-112">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="1d7bf-112">Clear-EventLog</span></span>](https://technet.microsoft.com/en-us/library/dd347552.aspx)

-   [<span data-ttu-id="1d7bf-113">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="1d7bf-113">Get-EventLog</span></span>](https://technet.microsoft.com/en-us/library/dd315250.aspx)

-   [<span data-ttu-id="1d7bf-114">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="1d7bf-114">Get-HotFix</span></span>](https://technet.microsoft.com/en-us/library/e1ef636f-5170-4675-b564-199d9ef6f101)

-   [<span data-ttu-id="1d7bf-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="1d7bf-115">Get-Process</span></span>](https://technet.microsoft.com/en-us/library/dd347630.aspx)

-   [<span data-ttu-id="1d7bf-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="1d7bf-116">Get-Service</span></span>](https://technet.microsoft.com/en-us/library/dd347591.aspx)

-   [<span data-ttu-id="1d7bf-117">Set-Service</span><span class="sxs-lookup"><span data-stu-id="1d7bf-117">Set-Service</span></span>](https://technet.microsoft.com/en-us/library/dd315324.aspx)

-   [<span data-ttu-id="1d7bf-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="1d7bf-118">Get-WinEvent</span></span>](https://technet.microsoft.com/en-us/library/dd315358.aspx)

-   [<span data-ttu-id="1d7bf-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="1d7bf-119">Get-WmiObject</span></span>](https://technet.microsoft.com/en-us/library/dd315295.aspx)

<span data-ttu-id="1d7bf-120">In der Regel weisen Cmdlets, die Remoting ohne besondere Konfiguration unterstützen, den „ComputerName“-Parameter und nicht den „Session“-Parameter auf.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="1d7bf-121">Um diese Cmdlets in Ihrer Sitzung zu finden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="1d7bf-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="1d7bf-122">Windows PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="1d7bf-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="1d7bf-123">Mit dem Windows PowerShell-Remoting, bei dem das WS-Verwaltungsprotokoll verwendet wird, können Sie jeden Windows PowerShell-Befehl auf einem oder mehreren Remotecomputern ausführen.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="1d7bf-124">Sie können dauerhafte Verbindungen herstellen, interaktive 1:1-Sitzungen 1:1 starten und Skripts auf mehreren Computern ausführen.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="1d7bf-125">Um Windows PowerShell-Remoting zu verwenden, muss der Remotecomputer für die Remoteverwaltung konfiguriert sein.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="1d7bf-126">Weitere Informationen und Anweisungen hierzu finden Sie unter [Informationen zu Remoteanforderungen](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="1d7bf-127">Nachdem Sie Windows PowerShell-Remoting konfiguriert haben, stehen Ihnen viele Remotingstrategien zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="1d7bf-128">Im weiteren Verlauf dieses Dokuments sind einige davon aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="1d7bf-129">Weitere Informationen finden Sie unter [about_Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) und [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="1d7bf-130">Starten einer interaktiven Sitzung</span><span class="sxs-lookup"><span data-stu-id="1d7bf-130">Start an Interactive Session</span></span>
<span data-ttu-id="1d7bf-131">Um eine interaktive Sitzung mit einem einzelnen Remotecomputer zu starten, verwenden Sie das Cmdlet [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) cmdlet.</span></span> <span data-ttu-id="1d7bf-132">Um beispielsweise eine interaktive Sitzung mit dem Remotecomputer „Server01“ zu starten, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="1d7bf-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="1d7bf-133">Die Eingabeaufforderung ändert sich, und es wird der Name des Computers angezeigt, mit dem Sie verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="1d7bf-134">Von nun an werden alle Befehle, die Sie an der Eingabeaufforderung eingeben, auf dem Remotecomputer ausgeführt, und die Ergebnisse werden auf dem lokalen Computer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="1d7bf-135">Um die interaktive Sitzung zu beenden, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="1d7bf-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="1d7bf-136">Weitere Informationen über die Cmdlets „Enter-PSSession“ und „Exit-PSSession“ Sie unter [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) und [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) and [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="1d7bf-137">Ausführen eines Remotebefehls</span><span class="sxs-lookup"><span data-stu-id="1d7bf-137">Run a Remote Command</span></span>
<span data-ttu-id="1d7bf-138">Zum Ausführen eines Befehls auf einem oder mehreren Remotecomputern verwenden Sie das Cmdlet [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-138">To run any command on one or many remote computers, use the [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx) cmdlet.</span></span>
<span data-ttu-id="1d7bf-139">Um beispielsweise einen [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx)-Befehl auf den Remotecomputern „Server01“ und „Server02“ auszuführen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="1d7bf-139">For example, to run a [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 {Get-UICulture}
```

<span data-ttu-id="1d7bf-140">Die Ausgabe wird an den Computer zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

<span data-ttu-id="1d7bf-141">Weitere Informationen zum Cmdlet „Invoke-Command“ finden Sie unter [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="1d7bf-142">Ausführen eines Skripts</span><span class="sxs-lookup"><span data-stu-id="1d7bf-142">Run a Script</span></span>
<span data-ttu-id="1d7bf-143">Zum Ausführen eines Skripts auf einem oder mehreren Remotecomputern verwenden Sie den Parameter „FilePath“ des Cmdlets „Invoke-Command“.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="1d7bf-144">Das Skript muss sich auf dem lokalen Computer befinden oder für diesen verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="1d7bf-145">Die Ergebnisse werden an den lokalen Computer zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="1d7bf-146">Der folgende Befehl führt beispielsweise das Skript „DiskCollect.ps1“ auf den Remotecomputern „Server01“ und „Server02“ aus.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="1d7bf-147">Weitere Informationen zum Cmdlet „Invoke-Command“ finden Sie unter [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="1d7bf-148">Herstellen einer dauerhaften Verbindung</span><span class="sxs-lookup"><span data-stu-id="1d7bf-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="1d7bf-149">Um eine Reihe verwandter Befehle auszuführen, die Daten gemeinsam nutzen, erstellen Sie eine Sitzung auf dem Remotecomputer, und verwenden Sie dann das Cmdlet „Invoke-Command“ zum Ausführen der Befehle in der Sitzung, die Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="1d7bf-150">Um eine Remotesitzung zu erstellen, verwenden Sie das Cmdlet „New-PSSession“.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="1d7bf-151">Mit dem folgenden Befehl erstellen Sie z. B. eine Remotesitzung auf dem Computer "Server01" und eine weitere Remotesitzung auf dem Computer "Server02".</span><span class="sxs-lookup"><span data-stu-id="1d7bf-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="1d7bf-152">Es speichert die Sitzungsobjekte in der Variablen „$s“.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="1d7bf-153">Nachdem die Sitzungen nun hergestellt sind, können Sie jeden beliebigen Befehl in diesen ausführen.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="1d7bf-154">Und da die Sitzungen dauerhaft sind, können Sie Daten in einem Befehl sammeln und diese in einem nachfolgenden Befehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="1d7bf-155">Beispielsweise führt der folgende Befehl einen „Get-HotFix“-Befehl in den Sitzungen in der Variablen „$s“ aus und speichert die Ergebnisse dann in der Variablen „$h“.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="1d7bf-156">Die Variable „$h“ wird in jeder der Sitzungen in „$s“ erstellt, ist jedoch in der lokalen Sitzung nicht vorhanden.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="1d7bf-157">Sie können die Daten in der Variablen „$h“ jetzt in nachfolgenden Befehle verwenden, wie z. B. dem folgenden.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="1d7bf-158">Die Ergebnisse werden auf dem lokalen Computer angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="1d7bf-159">Erweitertes Remoting</span><span class="sxs-lookup"><span data-stu-id="1d7bf-159">Advanced Remoting</span></span>
<span data-ttu-id="1d7bf-160">Dies sind nur die grundlegenden Möglichkeiten, die die Remoteverwaltung von Windows PowerShell bietet.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="1d7bf-161">Mithilfe von Cmdlets, die mit Windows PowerShell installiert werden, können Sie Remotesitzungen sowohl von lokaler Seite als auch von Remoteseite aus einrichten und konfigurieren, angepasste und eingeschränkte Sitzungen erstellen, Benutzern über eine Remotesitzung den Import von Befehlen ermöglichen, die tatsächlich implizit in der Remotesitzung ausgeführt werden, die Sicherheit einer Remotesitzung konfigurieren und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="1d7bf-162">Um die Remotekonfiguration zu vereinfachen, umfasst Windows PowerShell einen WSMan-Anbieter.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="1d7bf-163">Das vom Anbieter erstellte Laufwerk „WSMAN:“ ermöglicht Ihnen, durch eine Hierarchie von Konfigurationseinstellungen auf dem lokalen Computer und den Remotecomputern zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="1d7bf-164">Weitere Informationen zum WSMan-Anbieter finden Sie unter [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) und   [About_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), oder indem Sie in der Windows PowerShell-Konsole „Get-Help wsman“ eingeben.</span><span class="sxs-lookup"><span data-stu-id="1d7bf-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and   [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="1d7bf-165">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="1d7bf-165">For more information, see:</span></span>
- [<span data-ttu-id="1d7bf-166">Häufig gestellte Fragen zu Remote</span><span class="sxs-lookup"><span data-stu-id="1d7bf-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="1d7bf-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d7bf-167">Register-PSSessionConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dd819496.aspx)
- <span data-ttu-id="1d7bf-168">[Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-168">[Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx).</span></span> 

<span data-ttu-id="1d7bf-169">Hilfe zu Remotingfehlern finden Sie unter [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="1d7bf-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d7bf-170">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1d7bf-170">See Also</span></span>
- [<span data-ttu-id="1d7bf-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1d7bf-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="1d7bf-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="1d7bf-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="1d7bf-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="1d7bf-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="1d7bf-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="1d7bf-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="1d7bf-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="1d7bf-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="1d7bf-176">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1d7bf-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="1d7bf-177">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1d7bf-177">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
- [<span data-ttu-id="1d7bf-178">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="1d7bf-178">Import-PSSession</span></span>](https://technet.microsoft.com/en-us/library/048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
- [<span data-ttu-id="1d7bf-179">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="1d7bf-179">New-PSSession</span></span>](https://technet.microsoft.com/en-us/library/59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
- [<span data-ttu-id="1d7bf-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="1d7bf-180">Register-PSSessionConfiguration</span></span>](https://technet.microsoft.com/en-us/library/af68867a-d201-4b19-a1de-594015ed8a25)
- [<span data-ttu-id="1d7bf-181">WSMan-Anbieter</span><span class="sxs-lookup"><span data-stu-id="1d7bf-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

