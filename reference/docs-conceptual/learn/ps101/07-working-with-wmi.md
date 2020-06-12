---
title: Arbeiten mit WMI
description: PowerShell verfügt seit jeher über Cmdlets für die Arbeit mit WMI.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 243685efa1f976ddb46a0d0efc4ed0635844606d
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438291"
---
# <a name="chapter-7---working-with-wmi"></a><span data-ttu-id="2db90-103">Kapitel 7: Arbeiten mit WMI</span><span class="sxs-lookup"><span data-stu-id="2db90-103">Chapter 7 - Working with WMI</span></span>

## <a name="wmi-and-cim"></a><span data-ttu-id="2db90-104">WMI und CIM</span><span class="sxs-lookup"><span data-stu-id="2db90-104">WMI and CIM</span></span>

<span data-ttu-id="2db90-105">PowerShell wird standardmäßig mit Cmdlets für die Arbeit mit anderen Technologien wie Windows-Verwaltungsinstrumentation (WMI) ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="2db90-105">PowerShell ships by default with cmdlets for working with other technologies such as Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="2db90-106">Es gibt mehrere native WMI-Cmdlets, die in PowerShell vorhanden sind, ohne dass zusätzliche Software oder Module installiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2db90-106">There are several native WMI cmdlets that exist in PowerShell without having to install any additional software or modules.</span></span>

<span data-ttu-id="2db90-107">PowerShell verfügt seit jeher über Cmdlets für die Arbeit mit WMI.</span><span class="sxs-lookup"><span data-stu-id="2db90-107">PowerShell has had cmdlets for working with WMI since the beginning.</span></span> <span data-ttu-id="2db90-108">`Get-Command` kann verwendet werden, um zu ermitteln, welche WMI-Cmdlets in PowerShell vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="2db90-108">`Get-Command` can be used to determine what WMI cmdlets exist in PowerShell.</span></span> <span data-ttu-id="2db90-109">Die folgenden Ergebnisse stammen von meinem Computer in der Windows 10-Laborumgebung, auf dem PowerShell, Version 5.1., ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2db90-109">The following results are from my Windows 10 lab environment computer that is running PowerShell version 5.1.</span></span> <span data-ttu-id="2db90-110">Ihre Ergebnisse können je nach ausgeführter PowerShell-Version variieren.</span><span class="sxs-lookup"><span data-stu-id="2db90-110">Your results may differ depending on what PowerShell version you're running.</span></span>

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

<span data-ttu-id="2db90-111">CIM-Cmdlets (Common Information Model) wurden in PowerShell-Version 3.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="2db90-111">Common Information Model (CIM) cmdlets were introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="2db90-112">Die CIM-Cmdlets sind so konzipiert, dass sie sowohl auf Windows- als auch auf Nicht-Windows-Computern verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="2db90-112">The CIM cmdlets are designed so they can be used on both Windows and non-Windows machines.</span></span> <span data-ttu-id="2db90-113">Die WMI-Cmdlets werden nicht mehr unterstützt, weshalb ich empfehle, die CIM-Cmdlets anstelle der älteren WMI-Cmdlets zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2db90-113">The WMI cmdlets are deprecated so my recommendation is to use the CIM cmdlets instead of the older WMI ones.</span></span>

<span data-ttu-id="2db90-114">Die CIM-Cmdlets sind alle in einem Modul enthalten.</span><span class="sxs-lookup"><span data-stu-id="2db90-114">The CIM cmdlets are all contained within a module.</span></span> <span data-ttu-id="2db90-115">Verwenden Sie zum Abrufen einer Liste der CIM-Cmdlets `Get-Command` mit dem Parameter **Module**, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="2db90-115">To obtain a list of the CIM cmdlets, use `Get-Command` with the **Module** parameter as shown in the following example.</span></span>

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

<span data-ttu-id="2db90-116">Die CIM-Cmdlets ermöglichen es Ihnen weiterhin, mit WMI zu arbeiten. Lassen Sie sich also nicht verwirren, wenn jemand die Aussage trifft: „Wenn ich WMI mit den CIM-Cmdlets von PowerShell abfrage...“.</span><span class="sxs-lookup"><span data-stu-id="2db90-116">The CIM cmdlets still allow you to work with WMI so don't be confused when someone makes the statement "When I query WMI with the PowerShell CIM cmdlets..."</span></span>

<span data-ttu-id="2db90-117">Wie bereits erwähnt, ist WMI eine gesonderte Technologie von PowerShell, und Sie verwenden lediglich die CIM-Cmdlets für den Zugriff auf WMI.</span><span class="sxs-lookup"><span data-stu-id="2db90-117">As I previously mentioned, WMI is a separate technology from PowerShell and you're just using the CIM cmdlets for accessing WMI.</span></span> <span data-ttu-id="2db90-118">Möglicherweise finden Sie ein altes VBScript, das die WMI-Abfragesprache (WQL) zum Abfragen von WMI verwendet, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="2db90-118">You may find an old VBScript that uses WMI Query Language (WQL) to query WMI such as in the following example.</span></span>

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

<span data-ttu-id="2db90-119">Sie können die WQL-Abfrage aus diesem VBScript nehmen und ohne Änderungen mit dem Cmdlet `Get-CimInstance` verwenden.</span><span class="sxs-lookup"><span data-stu-id="2db90-119">You can take the WQL query from that VBScript and use it with the `Get-CimInstance` cmdlet without any modifications.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="2db90-120">Dies ist allerdings nicht das Standardverfahren, mit dem ich WMI in PowerShell abfrage.</span><span class="sxs-lookup"><span data-stu-id="2db90-120">That's not how I typically query WMI with PowerShell.</span></span> <span data-ttu-id="2db90-121">Aber es funktioniert und gestattet Ihnen, vorhandene VBScripts auf einfache Weise zu PowerShell zu migrieren.</span><span class="sxs-lookup"><span data-stu-id="2db90-121">But it does work and allows you to easily migrate existing VBScripts to PowerShell.</span></span> <span data-ttu-id="2db90-122">Wenn ich mit dem Schreiben eines Einzeilers zum Abfragen von WMI beginne, verwende ich die folgende Syntax.</span><span class="sxs-lookup"><span data-stu-id="2db90-122">When I start out writing a one-liner to query WMI, I use the following syntax.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="2db90-123">Wenn ich nur die Seriennummer benötige, kann ich die Ausgabe per Pipeline an `Select-Object` weiterleiten und nur die Eigenschaft **SerialNumber** angeben.</span><span class="sxs-lookup"><span data-stu-id="2db90-123">If I only want the serial number, I can pipe the output to `Select-Object` and specify only the **SerialNumber** property.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="2db90-124">Standardmäßig gibt es mehrere Eigenschaften, die hinter den Kulissen abgerufen werden, die nie verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="2db90-124">By default, there are several properties that are retrieved behind the scenes that are never used.</span></span>
<span data-ttu-id="2db90-125">Dies mag keine große Rolle spielen, wenn Sie WMI auf dem lokalen Computer abfragen.</span><span class="sxs-lookup"><span data-stu-id="2db90-125">It may not matter much when querying WMI on the local computer.</span></span> <span data-ttu-id="2db90-126">Sobald Sie aber mit dem Abfragen von Remotecomputern beginnen, handelt es sich dabei nicht nur um zusätzliche Verarbeitungszeit, um diese Informationen zurückzugeben, sondern auch um zusätzliche unnötige Informationen, die über das Netzwerk abgerufen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="2db90-126">But once you start querying remote computers, it's not only additional processing time to return that information, but also additional unnecessary information to have to pull across the network.</span></span> <span data-ttu-id="2db90-127">`Get-CimInstance` verfügt über einen Parameter **Eigenschaft**, der die Informationen einschränkt, die abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="2db90-127">`Get-CimInstance` has a **Property** parameter that limits the information that's retrieved.</span></span> <span data-ttu-id="2db90-128">Dadurch wird die WMI-Abfrage effizienter.</span><span class="sxs-lookup"><span data-stu-id="2db90-128">This makes the query to WMI more efficient.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="2db90-129">Die vorherigen Ergebnisse haben ein Objekt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="2db90-129">The previous results returned an object.</span></span> <span data-ttu-id="2db90-130">Um eine einfache Zeichenfolge zurückzugeben, verwenden Sie den Parameter **ExpandProperty**.</span><span class="sxs-lookup"><span data-stu-id="2db90-130">To return a simple string, use the **ExpandProperty** parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="2db90-131">Sie können auch den Strich-Stil der Syntax verwenden, um eine einfache Zeichenfolge zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="2db90-131">You could also use the dotted style of syntax to return a simple string.</span></span> <span data-ttu-id="2db90-132">Hierdurch entfällt die Notwendigkeit einer Weitergabe per Pipeline an `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="2db90-132">This eliminates the need to pipe to `Select-Object`.</span></span>

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a><span data-ttu-id="2db90-133">Abfragen von Remotecomputern mit den CIM-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="2db90-133">Query Remote Computers with the CIM cmdlets</span></span>

<span data-ttu-id="2db90-134">Ich führe PowerShell immer noch als lokaler Administrator aus, der ein Domänenbenutzer ist.</span><span class="sxs-lookup"><span data-stu-id="2db90-134">I'm still running PowerShell as a local admin who is a domain user.</span></span> <span data-ttu-id="2db90-135">Wenn ich versuche, Informationen von einem Remotecomputer mithilfe des Cmdlets `Get-CimInstance` abzufragen, erhalte ich die Fehlermeldung „Zugriff verweigert“.</span><span class="sxs-lookup"><span data-stu-id="2db90-135">When I try to query information from a remote computer using the `Get-CimInstance` cmdlet, I receive an access denied error message.</span></span>

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

<span data-ttu-id="2db90-136">Viele Leute haben Sicherheitsbedenken, wenn es um PowerShell geht, aber die Wahrheit ist, dass Sie in PowerShell exakt dieselben Berechtigungen wie in der grafischen Benutzeroberfläche haben.</span><span class="sxs-lookup"><span data-stu-id="2db90-136">Many people have security concerns when it comes to PowerShell, but the truth is you have exactly the same permissions in PowerShell as you do in the GUI.</span></span> <span data-ttu-id="2db90-137">Nicht mehr und nicht weniger.</span><span class="sxs-lookup"><span data-stu-id="2db90-137">No more and no less.</span></span> <span data-ttu-id="2db90-138">Das Problem im vorherigen Beispiel besteht darin, dass der Benutzer, der PowerShell ausführt, nicht über die Berechtigung zum Abfragen von WMI-Informationen vom Server „DC01“ verfügt.</span><span class="sxs-lookup"><span data-stu-id="2db90-138">The problem in the previous example is that the user running PowerShell doesn't have rights to query WMI information from the DC01 server.</span></span> <span data-ttu-id="2db90-139">Ich könnte PowerShell als Domänenadministrator neu starten, da `Get-CimInstance` keinen Parameter **Credential** besitzt.</span><span class="sxs-lookup"><span data-stu-id="2db90-139">I could relaunch PowerShell as a domain administrator since `Get-CimInstance` doesn't have a **Credential** parameter.</span></span> <span data-ttu-id="2db90-140">Aber glauben Sie mir, dass das keine gute Idee ist, weil dann alles, was ich von PowerShell aus ausführe, als Domänenadministrator ausgeführt würde. Dies könnte hinsichtlich der Sicherheit, je nach Situation, gefährlich sein.</span><span class="sxs-lookup"><span data-stu-id="2db90-140">But, trust me, that isn't a good idea because then anything that I run from PowerShell would be running as a domain admin. That could be dangerous from a security standpoint depending on the situation.</span></span>

<span data-ttu-id="2db90-141">Unter Anwendung des Prinzips der geringsten Rechte führe ich pro Befehl eine Erhöhung der Rechte zum Domänenadministrator durch, indem ich den Parameter **Credential** verwenden, wenn ein Befehl diesen besitzt.</span><span class="sxs-lookup"><span data-stu-id="2db90-141">Using the principle of least privilege, I elevate to my domain admin account on a per command basis using the **Credential** parameter, if a command has one.</span></span> <span data-ttu-id="2db90-142">`Get-CimInstance` besitzt keinen Parameter **Credential**, sodass die Lösung in diesem Szenario darin besteht, zuerst eine **CimSession** zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2db90-142">`Get-CimInstance` doesn't have a **Credential** parameter so the solution in this scenario is to create a **CimSession** first.</span></span> <span data-ttu-id="2db90-143">Dann verwende ich die **CimSession-** anstelle eines Computernamens, um WMI auf dem Remotecomputer abzufragen.</span><span class="sxs-lookup"><span data-stu-id="2db90-143">Then I use the **CimSession** instead of a computer name to query WMI on the remote computer.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="2db90-144">Die CIM-Sitzung wurde in einer Variablen namens `$CimSession` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="2db90-144">The CIM session was stored in a variable named `$CimSession`.</span></span> <span data-ttu-id="2db90-145">Beachten Sie, dass ich auch das Cmdlet `Get-Credential` in Klammern angegeben habe, damit es zuerst ausgeführt wird und mich vor der Erstellung der neuen Sitzung zur Eingabe von alternativen Anmeldeinformationen auffordert.</span><span class="sxs-lookup"><span data-stu-id="2db90-145">Notice that I also specified the `Get-Credential` cmdlet in parentheses so that it executes first, prompting me for alternate credentials, before creating the new session.</span></span> <span data-ttu-id="2db90-146">Später in diesem Kapitel zeige ich Ihnen noch eine andere, effizientere Methode, um alternative Anmeldeinformationen anzugeben. Aber es ist wichtig, dieses grundlegende Konzept zu verstehen, bevor es komplizierter wird.</span><span class="sxs-lookup"><span data-stu-id="2db90-146">I'll show you another more efficient way to specify alternate credentials later in this chapter, but it's important to understand this basic concept before making it more complicated.</span></span>

<span data-ttu-id="2db90-147">Die im vorherigen Beispiel erstellte CIM-Sitzung kann nun mit dem Cmdlet `Get-CimInstance` verwendet werden, um die BIOS-Informationen von WMI auf dem Remotecomputer abzufragen.</span><span class="sxs-lookup"><span data-stu-id="2db90-147">The CIM session created in the previous example can now be used with the `Get-CimInstance` cmdlet to query the BIOS information from WMI on the remote computer.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

<span data-ttu-id="2db90-148">Die Verwendung von CIM-Sitzungen bietet mehrere zusätzliche Vorteile gegenüber dem reinen Angeben eines Computernamens.</span><span class="sxs-lookup"><span data-stu-id="2db90-148">There are several additional benefits to using CIM sessions instead of just specifying a computer name.</span></span> <span data-ttu-id="2db90-149">Wenn Sie mehrere Abfragen auf demselben Computer ausführen, ist die Verwendung einer CIM-Sitzung effizienter als die Verwendung des Computernamens bei jeder einzelnen Abfrage.</span><span class="sxs-lookup"><span data-stu-id="2db90-149">When running multiple queries to the same computer, using a CIM session is more efficient than using the computer name for each query.</span></span> <span data-ttu-id="2db90-150">Beim Erstellen einer CIM-Sitzung wird die Verbindung nur einmal eingerichtet.</span><span class="sxs-lookup"><span data-stu-id="2db90-150">Creating a CIM session only sets up the connection once.</span></span>
<span data-ttu-id="2db90-151">Anschließend verwenden mehrere Abfragen dieselbe Sitzung, um Informationen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="2db90-151">Then, multiple queries use that same session to retrieve information.</span></span> <span data-ttu-id="2db90-152">Die Verwendung des Computernamens erfordert, dass die Cmdlets die Verbindung bei jeder einzelnen Abfrage herstellen und wieder beenden.</span><span class="sxs-lookup"><span data-stu-id="2db90-152">Using the computer name requires the cmdlets to set up and tear down the connection with each individual query.</span></span>

<span data-ttu-id="2db90-153">Das Cmdlet `Get-CimInstance` verwendet standardmäßig das WSMan-Protokoll, was bedeutet, dass der Remotecomputer PowerShell, Version 3.0 oder höher, benötigt, um eine Verbindung herzustellen.</span><span class="sxs-lookup"><span data-stu-id="2db90-153">The `Get-CimInstance` cmdlet uses the WSMan protocol by default, which means the remote computer needs PowerShell version 3.0 or higher to connect.</span></span> <span data-ttu-id="2db90-154">Tatsächlich ist nicht die PowerShell-Version relevant, sondern die Stapelversion.</span><span class="sxs-lookup"><span data-stu-id="2db90-154">It's actually not the PowerShell version that matters, it's the stack version.</span></span> <span data-ttu-id="2db90-155">Die Stapelversion lässt sich mit dem Cmdlet `Test-WSMan` bestimmen.</span><span class="sxs-lookup"><span data-stu-id="2db90-155">The stack version can be determined using the `Test-WSMan` cmdlet.</span></span>
<span data-ttu-id="2db90-156">Es muss Version 3.0 sein.</span><span class="sxs-lookup"><span data-stu-id="2db90-156">It needs to be version 3.0.</span></span> <span data-ttu-id="2db90-157">Das ist die Version, die Sie bei PowerShell, Version 3.0 und höher, vorfinden.</span><span class="sxs-lookup"><span data-stu-id="2db90-157">That's the version you'll find with PowerShell version 3.0 and higher.</span></span>

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

<span data-ttu-id="2db90-158">Die älteren WMI-Cmdlets verwenden das DCOM-Protokoll, das mit älteren Versionen von Windows kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="2db90-158">The older WMI cmdlets use the DCOM protocol, which is compatible with older versions of Windows.</span></span> <span data-ttu-id="2db90-159">DCOM wird aber in der Regel von der Firewall auf neueren Versionen von Windows blockiert.</span><span class="sxs-lookup"><span data-stu-id="2db90-159">But DCOM is typically blocked by the firewall on newer versions of Windows.</span></span> <span data-ttu-id="2db90-160">Mit dem Cmdlet `New-CimSessionOption` können Sie eine DCOM-Protokollverbindung für die Verwendung mit `New-CimSession` erstellen.</span><span class="sxs-lookup"><span data-stu-id="2db90-160">The `New-CimSessionOption` cmdlet allows you to create a DCOM protocol connection for use with `New-CimSession`.</span></span> <span data-ttu-id="2db90-161">Dies gestattet, das Cmdlet `Get-CimInstance` für die Kommunikation mit Versionen von Windows zu verwenden, die älter sind als Windows Server 2000.</span><span class="sxs-lookup"><span data-stu-id="2db90-161">This allows the `Get-CimInstance` cmdlet to be used to communicate with versions of Windows as old as Windows Server 2000.</span></span> <span data-ttu-id="2db90-162">Dies bedeutet auch, dass PowerShell auf dem Remotecomputer nicht erforderlich ist, wenn das Cmdlet `Get-CimInstance` mit einer CimSession verwendet wird, die für die Verwendung des DCOM-Protokolls konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="2db90-162">This also means that PowerShell is not required on the remote computer when using the `Get-CimInstance` cmdlet with a CimSession that's configured to use the DCOM protocol.</span></span>

<span data-ttu-id="2db90-163">Erstellen Sie die DCOM-Protokolloption mithilfe des Cmdlets `New-CimSessionOption`, und speichern Sie sie in einer Variablen.</span><span class="sxs-lookup"><span data-stu-id="2db90-163">Create the DCOM protocol option using the `New-CimSessionOption` cmdlet and store it in a variable.</span></span>

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

<span data-ttu-id="2db90-164">Aus Gründen der Effizienz können Sie Ihre Domänenadministrator- oder erhöhten Anmeldeinformationen in einer Variablen speichern, damit Sie sie nicht bei jedem Befehl erneut eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="2db90-164">For efficiency, you can store your domain administrator or elevated credentials in a variable so you don't have to constantly enter them for each command.</span></span>

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="2db90-165">Ich verfüge über einen Server namens „SQL03“, auf dem Windows Server 2008 (nicht R2) ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2db90-165">I have a server named SQL03 that runs Windows Server 2008 (non-R2).</span></span> <span data-ttu-id="2db90-166">Dabei handelt es sich um das neueste Windows Server-Betriebssystem, auf dem PowerShell nicht standardmäßig installiert ist.</span><span class="sxs-lookup"><span data-stu-id="2db90-166">It's the newest Windows Server operating system that doesn't have PowerShell installed by default.</span></span>

<span data-ttu-id="2db90-167">Erstellen Sie mithilfe des DCOM-Protokolls eine **CimSession** zu SQL03.</span><span class="sxs-lookup"><span data-stu-id="2db90-167">Create a **CimSession** to SQL03 using the DCOM protocol.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

<span data-ttu-id="2db90-168">Beachten Sie im vorherigen Befehl, dass ich diesmal die Variable namens `$Cred` als Wert für den Parameter **Credential** angegeben habe, anstatt sie erneut manuell eingeben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="2db90-168">Notice in the previous command, this time I specified the variable named `$Cred` as the value for the **Credential** parameter instead of having to enter them manually again.</span></span>

<span data-ttu-id="2db90-169">Die Ausgabe der Abfrage ist unabhängig vom verwendeten, zugrunde liegenden Protokoll identisch.</span><span class="sxs-lookup"><span data-stu-id="2db90-169">The output of the query is the same regardless of the underlying protocol being used.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="2db90-170">Das Cmdlet `Get-CimSession` wird verwendet, um zu sehen, welche **CimSessions** derzeit verbunden sind und welche Protokolle diese verwenden.</span><span class="sxs-lookup"><span data-stu-id="2db90-170">The `Get-CimSession` cmdlet is used to see what **CimSessions** are currently connected and what protocols they're using.</span></span>

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

<span data-ttu-id="2db90-171">Rufen Sie die beiden zuvor erstellten **CimSessions** ab, und speichern Sie sie in einer Variablen mit dem Namen `$CimSession`.</span><span class="sxs-lookup"><span data-stu-id="2db90-171">Retrieve and store both of the previously created **CimSessions** in a variable named `$CimSession`.</span></span>

```powershell
$CimSession = Get-CimSession
```

<span data-ttu-id="2db90-172">Fragen Sie beide Computer mit jeweils einem Befehl ab, mit einem, der das WSMan-Protokoll verwendet, und einem, der DCOM verwendet.</span><span class="sxs-lookup"><span data-stu-id="2db90-172">Query both of the computers with one command, one using the WSMan protocol and the other one with DCOM.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="2db90-173">Ich habe zahlreiche Blogartikel zu den WMI- und CIM-Cmdlets verfasst.</span><span class="sxs-lookup"><span data-stu-id="2db90-173">I've written numerous blog articles about the WMI and CIM cmdlets.</span></span> <span data-ttu-id="2db90-174">Einer der nützlichsten behandelt eine Funktion, die ich erstellt habe, um automatisch festzustellen, ob WSMan oder DCOM verwendet werden sollte, und um die CIM-Sitzung automatisch einzurichten, ohne manuell herausfinden zu müssen, welches.</span><span class="sxs-lookup"><span data-stu-id="2db90-174">One of the most useful ones is about a function that I created to automatically determine if WSMan or DCOM should be used and set up the CIM session automatically without having to figure out which one manually.</span></span> <span data-ttu-id="2db90-175">Dieser Blogartikel trägt den Titel [PowerShell-Funktion zum Erstellen von CimSessions für Remotecomputer mit Fallback auf DCOM][].</span><span class="sxs-lookup"><span data-stu-id="2db90-175">That blog article is titled [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].</span></span>

<span data-ttu-id="2db90-176">Wenn Sie mit den CIM-Sitzungen fertig sind, sollten Sie sie mit dem Cmdlet `Remove-CimSession` entfernen.</span><span class="sxs-lookup"><span data-stu-id="2db90-176">When you're finished with the CIM sessions, you should remove them with the `Remove-CimSession` cmdlet.</span></span> <span data-ttu-id="2db90-177">Um alle CIM-Sitzungen zu entfernen, leiten Sie einfach `Get-CimSession` per Pipeline an `Remove-CimSession` weiter.</span><span class="sxs-lookup"><span data-stu-id="2db90-177">To remove all CIM sessions, simply pipe `Get-CimSession` to `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a><span data-ttu-id="2db90-178">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="2db90-178">Summary</span></span>

<span data-ttu-id="2db90-179">In diesem Kapitel haben Sie erfahren, wie Sie PowerShell verwenden, um sowohl auf lokalen als auch auf Remotecomputern mit WMI zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2db90-179">In this chapter, you've learned about using PowerShell to work with WMI on both local and remote computers.</span></span> <span data-ttu-id="2db90-180">Sie haben ferner erfahren, wie Sie die CIM-Cmdlets verwenden, um mit Remotecomputern sowohl mit dem WSMan- als auch mit dem DCOM-Protokoll zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2db90-180">You've also learned how to use the CIM cmdlets to work with remote computers with both the WSMan or DCOM protocol.</span></span>

## <a name="review"></a><span data-ttu-id="2db90-181">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="2db90-181">Review</span></span>

1. <span data-ttu-id="2db90-182">Worin besteht der Unterschied zwischen WMI- und CIM-Cmdlets?</span><span class="sxs-lookup"><span data-stu-id="2db90-182">What is the difference in the WMI and CIM cmdlets?</span></span>
1. <span data-ttu-id="2db90-183">Welches Protokoll verwendet das `Get-CimInstance`-Cmdlet standardmäßig?</span><span class="sxs-lookup"><span data-stu-id="2db90-183">By default, what protocol does the `Get-CimInstance` cmdlet use?</span></span>
1. <span data-ttu-id="2db90-184">Was sind einige der Vorteile bei der Verwendung einer CIM-Sitzung, anstatt einen Computernamen mit `Get-CimInstance` anzugeben?</span><span class="sxs-lookup"><span data-stu-id="2db90-184">What are some of the benefits of using a CIM session instead of specifying a computer name with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="2db90-185">Wie geben Sie ein alternatives Protokoll an, das nicht das Standardprotokoll für die Verwendung mit `Get-CimInstance` ist?</span><span class="sxs-lookup"><span data-stu-id="2db90-185">How do you specify an alternate protocol other than the default one for use with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="2db90-186">Wie schließen oder entfernen Sie CIM-Sitzungen?</span><span class="sxs-lookup"><span data-stu-id="2db90-186">How do you close or remove CIM sessions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="2db90-187">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="2db90-187">Recommended Reading</span></span>

- <span data-ttu-id="2db90-188">[about_WMI][]</span><span class="sxs-lookup"><span data-stu-id="2db90-188">[about_WMI][]</span></span>
- <span data-ttu-id="2db90-189">[about_WMI_Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="2db90-189">[about_WMI_Cmdlets][]</span></span>
- <span data-ttu-id="2db90-190">[about_WQL][]</span><span class="sxs-lookup"><span data-stu-id="2db90-190">[about_WQL][]</span></span>
- <span data-ttu-id="2db90-191">[CimCmdlets-Modul][]</span><span class="sxs-lookup"><span data-stu-id="2db90-191">[CimCmdlets Module][]</span></span>
- <span data-ttu-id="2db90-192">[Video: Verwenden von CIM-Cmdlets und CIM-Sitzungen][]</span><span class="sxs-lookup"><span data-stu-id="2db90-192">[Video: Using CIM Cmdlets and CIM Sessions][]</span></span>

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets-Modul]: /powershell/module/cimcmdlets/
[CimCmdlets Module]: /powershell/module/cimcmdlets/
[Video: Verwenden von CIM-Cmdlets und CIM-Sitzungen]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Video: Using CIM Cmdlets and CIM Sessions]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[PowerShell-Funktion zum Erstellen von CimSessions für Remotecomputer mit Fallback auf DCOM]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
[PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
