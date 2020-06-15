---
title: Einzeiler und die Pipeline
description: Ein PowerShell-Einzeiler ist eine kontinuierliche Pipeline, die mehrere Befehle enthält, um eine einzelne Aufgabe zu erledigen.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4244c34628e8f2ee8d54471fc2d5ad81a870e739
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438061"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a><span data-ttu-id="de329-103">Kapitel 4: Einzeiler und die Pipeline</span><span class="sxs-lookup"><span data-stu-id="de329-103">Chapter 4 - One-liners and the pipeline</span></span>

<span data-ttu-id="de329-104">Als ich mich zum ersten Mal mit PowerShell beschäftigt habe, habe ich, wenn ich eine Aufgabe nicht mit einem PowerShell-Einzeiler ausführen konnte, auf die grafische Benutzeroberfläche (GUI) zurückgegriffen.</span><span class="sxs-lookup"><span data-stu-id="de329-104">When I first started learning PowerShell, if I couldn't accomplish a task with a PowerShell one-liner, I went back to the GUI.</span></span> <span data-ttu-id="de329-105">Im Laufe der Zeit habe ich meine Kenntnisse auf das Schreiben von Skripts, Funktionen und Modulen erweitert.</span><span class="sxs-lookup"><span data-stu-id="de329-105">Over time, I built my skills up to writing scripts, functions, and modules.</span></span> <span data-ttu-id="de329-106">Lassen Sie sich von einigen der umfangreicheren Beispiele, die Sie möglicherweise im Internet sehen, nicht abschrecken.</span><span class="sxs-lookup"><span data-stu-id="de329-106">Don't allow yourself to become overwhelmed by some of the more advanced examples you may see on the internet.</span></span> <span data-ttu-id="de329-107">Niemand kommt als PowerShell-Experte auf die Welt.</span><span class="sxs-lookup"><span data-stu-id="de329-107">No one is a natural expert with PowerShell.</span></span> <span data-ttu-id="de329-108">Jeder von uns hat einmal angefangen.</span><span class="sxs-lookup"><span data-stu-id="de329-108">We were all beginners at one time.</span></span>

<span data-ttu-id="de329-109">Ich möchten denjenigen, die immer noch die grafische Benutzeroberfläche (GUI) für Verwaltungszwecke verwenden, ein paar Ratschläge anbieten: Installieren Sie die Verwaltungstools auf ihrer Administrator-Arbeitsstation, und verwalten Sie Ihre Server remote.</span><span class="sxs-lookup"><span data-stu-id="de329-109">I have a bit of advice to offer those of you who are still using the GUI for administration: install the management tools on your admin workstation and manage your servers remotely.</span></span> <span data-ttu-id="de329-110">Auf diese Weise ist es unerheblich, ob auf dem Server eine GUI- oder Server Core-Installation des Betriebssystems ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="de329-110">This way it won't matter if the server is running a GUI or Server Core installation of the operating system.</span></span>
<span data-ttu-id="de329-111">Dies wird Ihnen dabei helfen, sich auf die Remoteverwaltung von Servern mit PowerShell vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="de329-111">It's going to help prepare you for managing servers remotely with PowerShell.</span></span>

<span data-ttu-id="de329-112">Stellen Sie wie in vorherigen Kapiteln sicher, dass Sie die Abläufe auf Ihrem Windows 10-Laborumgebungscomputer durchlaufen und nachvollziehen.</span><span class="sxs-lookup"><span data-stu-id="de329-112">As with previous chapters, be sure to follow along on your Windows 10 lab environment computer.</span></span>

## <a name="one-liners"></a><span data-ttu-id="de329-113">Einzeiler</span><span class="sxs-lookup"><span data-stu-id="de329-113">One-Liners</span></span>

<span data-ttu-id="de329-114">Ein PowerShell-Einzeiler ist eine kontinuierliche Pipeline, nicht notwendigerweise ein Befehl, der in einer physischen Zeile steht.</span><span class="sxs-lookup"><span data-stu-id="de329-114">A PowerShell one-liner is one continuous pipeline and not necessarily a command that’s on one physical line.</span></span> <span data-ttu-id="de329-115">Nicht alle Befehle, die in einer physischen Zeile stehen, sind Einzeiler.</span><span class="sxs-lookup"><span data-stu-id="de329-115">Not all commands that are on one physical line are one-liners.</span></span>

<span data-ttu-id="de329-116">Obwohl sich der folgende Befehl auf mehrere physische Zeilen verteilt, handelt es sich um einen PowerShell-Einzeiler, weil er eine kontinuierliche Pipeline ist.</span><span class="sxs-lookup"><span data-stu-id="de329-116">Even though the following command is on multiple physical lines, it's a PowerShell one-liner because it's one continuous pipeline.</span></span> <span data-ttu-id="de329-117">Er könnte in einer physischen Zeile geschrieben werden, aber ich habe mich entschieden, die Zeilen am Pipe-Symbol zu umbrechen.</span><span class="sxs-lookup"><span data-stu-id="de329-117">It could be written on one physical line, but I've chosen to line break at the pipe symbol.</span></span> <span data-ttu-id="de329-118">Das Pipe-Symbol ist eins der Zeichen, bei denen ein natürlicher Zeilenumbruch in PowerShell zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="de329-118">The pipe symbol is one of the characters where a natural line break is allowed in PowerShell.</span></span>

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

<span data-ttu-id="de329-119">Natürliche Zeilenumbrüche können bei häufig verwendeten Zeichen auftreten, einschließlich Komma (`,`) sowie öffnenden eckigen (`[`), geschweiften (`{`) und runden Klammern (`(`).</span><span class="sxs-lookup"><span data-stu-id="de329-119">Natural line breaks can occur at commonly used characters including comma (`,`) and opening brackets (`[`), braces (`{`), and parenthesis (`(`).</span></span> <span data-ttu-id="de329-120">Andere Zeichen, die nicht so häufig vorkommen, umfassen das Semikolon (`;`), das Gleichheitszeichen (`=`) sowie öffnende einfache als auch doppelte Anführungszeichen (`'`, `"`).</span><span class="sxs-lookup"><span data-stu-id="de329-120">Others that aren't so common include the semicolon (`;`), equals sign (`=`), and both opening single and double quotes (`'`,`"`).</span></span>

<span data-ttu-id="de329-121">Die Verwendung des Graviszeichens (`` ` ``) als Zeilenfortsetzungszeichen ist ein umstrittenes Thema.</span><span class="sxs-lookup"><span data-stu-id="de329-121">Using the backtick (`` ` ``) or grave accent character as a line continuation character is a controversial topic.</span></span> <span data-ttu-id="de329-122">Ich empfehle Ihnen, die Verwendung dieses Zeichens vollständig zu vermeiden, falls möglich.</span><span class="sxs-lookup"><span data-stu-id="de329-122">My recommendation is to try to avoid it if at all possible.</span></span> <span data-ttu-id="de329-123">Ich sehe häufig PowerShell-Befehle, die ein Graviszeichen direkt hinter einem natürlichen Zeilenumbruchzeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="de329-123">I often see PowerShell commands written using a backtick immediately after a natural line break character.</span></span>
<span data-ttu-id="de329-124">Dafür gibt es keinen Grund.</span><span class="sxs-lookup"><span data-stu-id="de329-124">There's no reason for it to be there.</span></span>

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="de329-125">Die in den vorherigen zwei Beispielen gezeigten Befehle funktionieren in der PowerShell-Konsole einwandfrei.</span><span class="sxs-lookup"><span data-stu-id="de329-125">The commands shown in the previous two examples work fine in the PowerShell console.</span></span> <span data-ttu-id="de329-126">Wenn Sie aber versuchen, sie im Konsolenbereich der PowerShell ISE auszuführen, wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="de329-126">But if you try to run them in the console pane of the PowerShell ISE, they'll generate an error.</span></span> <span data-ttu-id="de329-127">Der Konsolenbereich der PowerShell ISE wartet nicht, bis der restliche Befehl in der nächsten Zeile eingegeben wird, wie es die PowerShell-Konsole macht.</span><span class="sxs-lookup"><span data-stu-id="de329-127">The console pane of the PowerShell ISE doesn't wait for the rest of the command to be entered on the next line like the PowerShell console does.</span></span> <span data-ttu-id="de329-128">Um dieses Problem im Konsolenbereich der PowerShell ISE zu vermeiden, verwenden Sie <kbd>Umschalt</kbd>+<kbd>EINGABE</kbd>, anstatt nur die <kbd>EINGABETASTE</kbd> zu drücken, wenn Sie einen Befehl in einer anderen Zeile fortsetzen möchten.</span><span class="sxs-lookup"><span data-stu-id="de329-128">To avoid this problem in the console pane of the PowerShell ISE, use <kbd>Shift</kbd>+<kbd>Enter</kbd> instead of just pressing <kbd>Enter</kbd> when continuing a command on another line.</span></span>

<span data-ttu-id="de329-129">Das nächste Beispiel ist kein PowerShell-Einzeiler, weil es sich nicht um eine kontinuierliche Pipeline handelt.</span><span class="sxs-lookup"><span data-stu-id="de329-129">This next example isn't a PowerShell one-liner because it's not one continuous pipeline.</span></span> <span data-ttu-id="de329-130">Es handelt sich um zwei getrennte Befehle in einer Zeile, die durch ein Semikolon getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="de329-130">It's two separate commands on one line, separated by a semicolon.</span></span>

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="de329-131">Viele Programmier- und Skriptsprachen erfordern am Ende jeder Zeile ein Semikolon.</span><span class="sxs-lookup"><span data-stu-id="de329-131">Many programming and scripting languages require a semicolon at the end of each line.</span></span> <span data-ttu-id="de329-132">Zwar können Sie dies so auch in PowerShell handhaben, doch wird dies nicht empfohlen, da es unnötig ist.</span><span class="sxs-lookup"><span data-stu-id="de329-132">While they can be used that way in PowerShell, it's not recommended because they're not needed.</span></span>

## <a name="filtering-left"></a><span data-ttu-id="de329-133">Links filtern</span><span class="sxs-lookup"><span data-stu-id="de329-133">Filtering Left</span></span>

<span data-ttu-id="de329-134">Die Ergebnisse der in diesem Kapitel gezeigten Befehle wurden zu einer Teilmenge gefiltert.</span><span class="sxs-lookup"><span data-stu-id="de329-134">The results of the commands shown in this chapter have been filtered down to a subset.</span></span> <span data-ttu-id="de329-135">Beispielsweise wurde `Get-Service` mit dem Parameter **Name** verwendet, um die Liste der zurückgegebenen Dienste auf nur den Windows-Zeitdienst zu filtern.</span><span class="sxs-lookup"><span data-stu-id="de329-135">For example, `Get-Service` was used with the **Name** parameter to filter the list of services that were returned to only the Windows Time service.</span></span>

<span data-ttu-id="de329-136">In der Pipeline sollten Sie die Ergebnisse immer so früh wie möglich auf das Gesuchte filtern.</span><span class="sxs-lookup"><span data-stu-id="de329-136">In the pipeline, you always want to filter the results down to what you're looking for as early as possible.</span></span> <span data-ttu-id="de329-137">Dies erfolgt mithilfe von Parametern beim ersten Befehl oder dem am weitesten links stehenden.</span><span class="sxs-lookup"><span data-stu-id="de329-137">This is accomplished using parameters on the first command or, the one to the far left.</span></span>
<span data-ttu-id="de329-138">Dies wird manchmal auch als _Links filtern_ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="de329-138">This is sometimes called _filtering left_.</span></span>

<span data-ttu-id="de329-139">Im folgenden Beispiel wird der Parameter **Name** von `Get-Service` verwendet, um die Ergebnisse sofort nur auf den Windows-Zeitdienst zu filtern.</span><span class="sxs-lookup"><span data-stu-id="de329-139">The following example uses the **Name** parameter of `Get-Service` to immediately filter the results to the Windows Time service only.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="de329-140">Es ist nicht ungewöhnlich, dass in Beispielen der Befehl per Pipeline an `Where-Object` weitergeleitet wird, um die Filterung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="de329-140">It's not uncommon to see examples where the command is piped to `Where-Object` to perform the filtering.</span></span>

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

<span data-ttu-id="de329-141">Im ersten Beispiel wird an der Quelle gefiltert, und es werden nur die Ergebnisse für den Windows-Zeitdienst zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="de329-141">The first example filters at the source and only returns the results for the Windows Time service.</span></span>
<span data-ttu-id="de329-142">Im zweiten Beispiel werden alle Dienste zurückgegeben, die dann per Pipeline an einen anderen Befehl weitergeleitet werden, um die Filterung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="de329-142">The second example returns all the services then pipes them to another command to perform the filtering.</span></span> <span data-ttu-id="de329-143">Dies mag in diesem Beispiel nicht wie ein großer Unterschied aussehen, doch stellen Sie sich vor, dass Sie eine Liste von Active Directory-Benutzern abfragen.</span><span class="sxs-lookup"><span data-stu-id="de329-143">While this may not seem like a big deal in this example, imagine if you were querying a list of Active Directory users.</span></span> <span data-ttu-id="de329-144">Möchten Sie wirklich die Informationen für viele Tausende von Benutzerkonten aus Active Directory zurückgeben, nur um diese per Pipeline an einen anderen Befehl weiterzuleiten, der sie dann zu einer kleinen Teilmenge filtert?</span><span class="sxs-lookup"><span data-stu-id="de329-144">Do you really want to return the information for many thousands of user accounts from Active Directory only to pipe them to another command that filters them down to a tiny subset?</span></span> <span data-ttu-id="de329-145">Meine Empfehlung ist, immer links zu filtern, auch wenn dies bedeutungslos zu sein scheint.</span><span class="sxs-lookup"><span data-stu-id="de329-145">My recommendation is to always filter left even when it doesn't seem to matter.</span></span> <span data-ttu-id="de329-146">Sie gewöhnen sich dies so an, dass Sie später automatisch links filtern, wenn es wirklich darauf ankommt.</span><span class="sxs-lookup"><span data-stu-id="de329-146">You'll be so use to it that you'll automatically filter left when it really does matter.</span></span>

<span data-ttu-id="de329-147">Mit hat mal jemand gesagt, dass die Reihenfolge, in der Sie die Befehle angeben, keine Rolle spielt.</span><span class="sxs-lookup"><span data-stu-id="de329-147">I once had someone tell me that the order you specify the commands in doesn't matter.</span></span> <span data-ttu-id="de329-148">Das entspricht jedoch in keiner Weise den Tatsachen.</span><span class="sxs-lookup"><span data-stu-id="de329-148">That couldn't be further from the truth.</span></span> <span data-ttu-id="de329-149">Die Reihenfolge, in der die Befehle angegeben werden, ist allerdings von Bedeutung, nämlich beim Filtern.</span><span class="sxs-lookup"><span data-stu-id="de329-149">The order that the commands are specified in does indeed matter when performing filtering.</span></span> <span data-ttu-id="de329-150">Nehmen Sie beispielsweise ein Szenario an, in dem Sie `Select-Object` verwenden, um nur ein paar Eigenschaften auszuwählen, und `Where-Object` verwenden, um nach Eigenschaften zu filtern, die nicht in der Auswahl sein sollen.</span><span class="sxs-lookup"><span data-stu-id="de329-150">For example, consider the scenario where you are using `Select-Object` to select only a few properties and `Where-Object` to filter on properties that won't be in the selection.</span></span> <span data-ttu-id="de329-151">In diesem Szenario muss die Filterung zuerst erfolgen, da die Eigenschaft andernfalls nicht in der Pipeline vorhanden sein wird, wenn Sie versuchen, die Filterung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="de329-151">In that scenario, the filtering must occur first, otherwise the property won't exist in the pipeline when try to perform the filtering.</span></span>

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

<span data-ttu-id="de329-152">Der Befehl im vorherigen Beispiel gibt keine Ergebnisse zurück, weil die Eigenschaft **CanStopAndContinue-** nicht vorhanden ist, wenn die Ergebnisse von `Select-Object` per Pipeline an `Where-Object` weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="de329-152">The command in the previous example doesn't return any results because the **CanStopAndContinue** property doesn't exist when the results of `Select-Object` are piped to `Where-Object`.</span></span> <span data-ttu-id="de329-153">Diese spezifische Eigenschaft wurde nicht „ausgewählt“.</span><span class="sxs-lookup"><span data-stu-id="de329-153">That particular property wasn't "selected".</span></span> <span data-ttu-id="de329-154">Im Wesentlichen wurde sie herausgefiltert. Wenn Sie die Reihenfolge von `Select-Object` und `Where-Object` umkehren, erzeugt dies die gewünschten Ergebnisse.</span><span class="sxs-lookup"><span data-stu-id="de329-154">In essence, it was filtered out. Reversing the order of `Select-Object` and `Where-Object` produces the desired results.</span></span>

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a><span data-ttu-id="de329-155">Die Pipeline</span><span class="sxs-lookup"><span data-stu-id="de329-155">The Pipeline</span></span>

<span data-ttu-id="de329-156">Wie Sie in vielen der bisher gezeigten Beispiele in diesem Buch gesehen haben, kann die Ausgabe eines Befehls oft als Eingabe für einen anderen Befehl verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="de329-156">As you've seen in many of the examples shown so far throughout this book, many times the output of one command can be used as input for another command.</span></span> <span data-ttu-id="de329-157">In Kapitel 3 wurde `Get-Member` verwendet, um zu bestimmen, welcher Objekttyp von einem Befehl erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="de329-157">In Chapter 3, `Get-Member` was used to determine what type of object a command produces.</span></span> <span data-ttu-id="de329-158">In Kapitel 3 wird auch die Verwendung des Parameters **ParameterType** von `Get-Command` gezeigt, um zu bestimmen, welche Befehle diesen Typ von Eingabe akzeptieren, obwohl dies nicht notwendigerweise durch eine Pipelineeingabe erfolgt sein muss.</span><span class="sxs-lookup"><span data-stu-id="de329-158">Chapter 3 also showed using the **ParameterType** parameter of `Get-Command` to determine what commands accepted that type of input, although not necessarily by pipeline input.</span></span>

<span data-ttu-id="de329-159">Abhängig davon, wie gründlich die Hilfe eines Befehls ist, kann sie einen Abschnitt **INPUTS** (Eingaben) und **OUTPUTS** (Ausgaben) enthalten.</span><span class="sxs-lookup"><span data-stu-id="de329-159">Depending on how thorough a commands help is, it may include an **INPUTS** and **OUTPUTS** section.</span></span>

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

<span data-ttu-id="de329-160">In den vorherigen Ergebnissen wird nur der relevante Abschnitt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="de329-160">Only the relevant section of the help is shown in the previous results.</span></span> <span data-ttu-id="de329-161">Wie Sie sehen können, wird im Abschnitt **INPUTS** angegeben, dass ein **ServiceController**- oder ein **String**-Objekt per Pipeline an das Cmdlet `Stop-Service` weitergeleitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="de329-161">As you can see, the **INPUTS** section states that a **ServiceController** or a **String** object can be piped to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="de329-162">Sie erfahren nicht, welche Parameter diese Art von Eingabe akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="de329-162">It doesn't tell you which parameters accept that type of input.</span></span> <span data-ttu-id="de329-163">Eine der einfachsten Methoden, um diese Information zu ermitteln, besteht darin, die verschiedenen Parameter in der vollständigen Version der Hilfe für das Cmdlet `Stop-Service` durchzusehen.</span><span class="sxs-lookup"><span data-stu-id="de329-163">One of the easiest ways to determine that information is to look through the different parameters in the full version of the help for the `Stop-Service` cmdlet.</span></span>

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

<span data-ttu-id="de329-164">Noch einmal: Ich habe hier nur den relevanten Teil der Hilfe im vorherigen Resultset angezeigt.</span><span class="sxs-lookup"><span data-stu-id="de329-164">Once again, I've only shown the relevant portion of the help in the previous set of results.</span></span> <span data-ttu-id="de329-165">Beachten Sie Folgendes: Der Parameter **DisplayName** akzeptiert keine Pipelineeingabe, der Parameter **InputObject** akzeptiert Pipelineeingaben **als Wert** für **ServiceController**-Objekte, und der Parameter **Name** akzeptiert Pipelineeingaben **als Wert** für **String**-Objekte.</span><span class="sxs-lookup"><span data-stu-id="de329-165">Notice that the **DisplayName** parameter doesn't accept pipeline input, the **InputObject** parameter accepts pipeline input **by value** for **ServiceController** objects, and the **Name** parameter accepts pipeline input **by value** for **string** objects.</span></span> <span data-ttu-id="de329-166">Er akzeptiert auch Pipelineeingaben **als Eigenschaftsname**.</span><span class="sxs-lookup"><span data-stu-id="de329-166">It also accepts pipeline input **by property name**.</span></span>

<span data-ttu-id="de329-167">Wenn ein Parameter Pipelineeingaben sowohl als Eigenschaftsnamen als auch als Wert akzeptiert, wird immer zuerst **als Wert** ausprobiert.</span><span class="sxs-lookup"><span data-stu-id="de329-167">When a parameter accepts pipeline input by both property name and by value, it always tries **by value** first.</span></span> <span data-ttu-id="de329-168">Schlägt **als Wert** fehl, wird **als Eigenschaftsname** versucht.</span><span class="sxs-lookup"><span data-stu-id="de329-168">If **by value** fails, then it tries **by property name**.</span></span> <span data-ttu-id="de329-169">**Als Wert** ist ein wenig irreführend.</span><span class="sxs-lookup"><span data-stu-id="de329-169">**By value** is a little misleading.</span></span> <span data-ttu-id="de329-170">Ich ziehe es vor, hier von **als Typ** zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="de329-170">I prefer to call it **by type**.</span></span> <span data-ttu-id="de329-171">Dies bedeutet, dass, wenn Sie die Ergebnisse eines Befehls, der einen **ServiceController**-Objekttyp erzeugt, per Pipeline an `Stop-Service` weiterleiten, diese Eingabe an den Parameter **InputObject** gebunden wird.</span><span class="sxs-lookup"><span data-stu-id="de329-171">This means if you pipe the results of a command that produces a **ServiceController** object type to `Stop-Service`, it binds that input to the **InputObject** parameter.</span></span> <span data-ttu-id="de329-172">Wenn Sie aber die Ergebnisse eines Befehls, der eine **String**-Ausgabe erzeugt, per Pipeline an `Stop-Service` weiterleiten, werden diese an den Parameter **Name** gebunden.</span><span class="sxs-lookup"><span data-stu-id="de329-172">But if you pipe the results of a command that produces **String** output to `Stop-Service`, it binds it to the **Name** parameter.</span></span> <span data-ttu-id="de329-173">Wenn Sie die Ergebnisse eines Befehls, der weder ein **ServiceController**- noch ein **String**-Objekt erzeugt, per Pipeline an `Stop-Service` weiterleiten, dieser aber eine Ausgabe erzeugt, die eine Eigenschaft namens **Name** enthält, wird die Eigenschaft **Name** der Ausgabe an den Parameter **Name** von `Stop-Service` gebunden.</span><span class="sxs-lookup"><span data-stu-id="de329-173">If you pipe the results of a command that doesn't produce a **ServiceController** or **String** object to `Stop-Service`, but it does produce output containing a property called **Name**, then it binds the **Name** property from the output to the **Name** parameter of `Stop-Service`.</span></span>

<span data-ttu-id="de329-174">Bestimmen Sie, welchen Typ von Ausgabe der Befehl `Get-Service` erzeugt.</span><span class="sxs-lookup"><span data-stu-id="de329-174">Determine what type of output the `Get-Service` command produces.</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

<span data-ttu-id="de329-175">`Get-Service` erzeugt einen ServiceController-Objekttyp.</span><span class="sxs-lookup"><span data-stu-id="de329-175">`Get-Service` produces a ServiceController object type.</span></span>

<span data-ttu-id="de329-176">Wie zuvor in der Hilfe gesehen, akzeptiert der Parameter **InputObject** von `Stop-Service` **ServiceController**-Objekte über die Pipeline **als Wert** (als Typ).</span><span class="sxs-lookup"><span data-stu-id="de329-176">As you previously saw in the help, the **InputObject** parameter of `Stop-Service` accepts **ServiceController** objects via the pipeline **by value** (by type).</span></span> <span data-ttu-id="de329-177">Dies bedeutet Folgendes: Wenn die Ergebnisse des Cmdlets`Get-Service` per Pipeline an `Stop-Service` weitergeleitet werden, werden sie an den Parameter **InputObject** von `Stop-Service` gebunden.</span><span class="sxs-lookup"><span data-stu-id="de329-177">This means that when the results of the `Get-Service` cmdlet are piped to `Stop-Service`, they bind to the **InputObject** parameter of `Stop-Service`.</span></span>

```powershell
Get-Service -Name w32time | Stop-Service
```

<span data-ttu-id="de329-178">Nun probieren wir String-Eingaben aus.</span><span class="sxs-lookup"><span data-stu-id="de329-178">Now to try string input.</span></span> <span data-ttu-id="de329-179">Leiten Sie `w32time` per Pipeline an `Get-Member` weiter, lediglich um zu bestätigen, dass es eine Zeichenfolge (string) ist.</span><span class="sxs-lookup"><span data-stu-id="de329-179">Pipe `w32time` to `Get-Member` just to confirm that it's a string.</span></span>

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

<span data-ttu-id="de329-180">Wie zuvor in der Hilfe gezeigt, wird eine Zeichenfolge durch ihre Weiterleitung per Pipeline an `Stop-Service` **als Wert** an den Parameter **Name** von `Stop-Service` gebunden.</span><span class="sxs-lookup"><span data-stu-id="de329-180">As previously shown in the help, piping a string to `Stop-Service` binds it **by value** to the **Name** parameter of `Stop-Service`.</span></span> <span data-ttu-id="de329-181">Testen Sie dies, indem Sie `w32time` per Pipeline an `Stop-Service` weiterleiten.</span><span class="sxs-lookup"><span data-stu-id="de329-181">Test this by piping `w32time` to `Stop-Service`.</span></span>

```powershell
'w32time' | Stop-Service
```

<span data-ttu-id="de329-182">Beachten Sie, dass ich im vorherigen Beispiel einfache Anführungszeichen um die Zeichenfolge `w32time` verwendet habe.</span><span class="sxs-lookup"><span data-stu-id="de329-182">Notice that in the previous example, I used single quotes around the string `w32time`.</span></span> <span data-ttu-id="de329-183">In PowerShell sollten Sie immer einfache Anführungszeichen anstelle von doppelten Anführungszeichen verwenden, es sei denn, der Inhalt der Zeichenfolge in Anführungszeichen enthält eine Variable, die auf ihren tatsächlichen Wert erweitert werden muss.</span><span class="sxs-lookup"><span data-stu-id="de329-183">In PowerShell, you should always use single quotes instead of double quotes unless the contents of the quoted string contains a variable that needs to be expanded to its actual value.</span></span> <span data-ttu-id="de329-184">Wenn Sie einfache Anführungszeichen verwenden, muss PowerShell den in den Anführungszeichen stehenden Inhalt nicht analysieren, weshalb Ihr Code etwas schneller ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="de329-184">By using single quotes, PowerShell doesn't have to parse the contents contained within the quotes so your code runs a little faster.</span></span>

<span data-ttu-id="de329-185">Erstellen Sie ein benutzerdefiniertes Objekt, um die Pipelineeingabe als Eigenschaftsname für den Parameter **Name** von `Stop-Service` zu testen.</span><span class="sxs-lookup"><span data-stu-id="de329-185">Create a custom object to test pipeline input by property name for the **Name** parameter of `Stop-Service`.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
>> Name = 'w32time'
>> }
```

<span data-ttu-id="de329-186">Der Inhalt der Variablen **CustomObject** ist ein **PSCustomObject**-Objekttyp, der eine Eigenschaft namens **Name** enthält.</span><span class="sxs-lookup"><span data-stu-id="de329-186">The contents of the **CustomObject** variable is a **PSCustomObject** object type and it contains a property named **Name**.</span></span>

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

<span data-ttu-id="de329-187">Wenn Sie die Variable `$CustomObject` in Anführungszeichen setzen müssten, sollten Sie doppelte Anführungszeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="de329-187">If you were to surround the `$CustomObject` variable with quotes, you want to use double quotes.</span></span>
<span data-ttu-id="de329-188">Andernfalls wird bei Verwendung von einfachen Anführungszeichen die wörtliche (literale) Zeichenfolge `$CustomObject` anstelle des in der Variablen enthaltenen Werts per Pipeline an `Get-Member` weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="de329-188">Otherwise, using single quotes, the literal string `$CustomObject` is piped to `Get-Member` instead of the value contained by the variable.</span></span>

<span data-ttu-id="de329-189">Obwohl der Inhalt von `$CustomObject` durch seine Weiterleitung per Pipeline an das Cmdlet `Stop-Service` an den Parameter **Name** gebunden wird, wird er diesmal **als Eigenschaftsname** gebunden anstatt **als Wert**, da der Inhalt von `$CustomObject` ein Objekt mit einer Eigenschaft namens **Name** ist.</span><span class="sxs-lookup"><span data-stu-id="de329-189">Although piping the contents of `$CustomObject` to `Stop-Service` cmdlet binds to the **Name** parameter, this time it binds **by property name** instead of **by value** because the contents of `$CustomObject` is an object that has a property named **Name**.</span></span>

<span data-ttu-id="de329-190">In diesem Beispiel erstelle ich ein anderes benutzerdefiniertes Objekt mit einem anderen Eigenschaftsnamen, z. B. **Service**.</span><span class="sxs-lookup"><span data-stu-id="de329-190">In this example, I create another custom object using a different property name, such as **Service**.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

<span data-ttu-id="de329-191">Ein Fehler wird generiert, wenn versucht wird, `$CustomObject` per Pipeline an `Stop-Service` weiterzuleiten, da der Befehl kein **ServiceController**- oder **String**-Objekt erzeugt und keine Eigenschaft namens **Name** besitzt.</span><span class="sxs-lookup"><span data-stu-id="de329-191">An error is generated when trying to pipe `$CustomObject` to `Stop-Service` because it doesn't produce a **ServiceController** or **String** object, and it doesn't have a property named **Name**.</span></span>

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

<span data-ttu-id="de329-192">Wenn die Ausgabe eines Befehls nicht mit den Pipelineeingabeoptionen für einen anderen Befehl übereinstimmt, kann `Select-Object` verwendet werden, um die Eigenschaft so umzubenennen, dass die Eigenschaften ordnungsgemäß übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="de329-192">If the output of one command doesn't line up with the pipeline input options for another command, `Select-Object` can be used to rename the property so that the properties lineup correctly.</span></span>

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

<span data-ttu-id="de329-193">In diesem Beispiel wurde `Select-Object` verwendet, um die Eigenschaft **Service** in eine Eigenschaft namens **Name** umzubenennen.</span><span class="sxs-lookup"><span data-stu-id="de329-193">In this example, `Select-Object` was used to rename the **Service** property to a property named **Name**.</span></span>

<span data-ttu-id="de329-194">Die Syntax in diesem Beispiel mag zuerst etwas kompliziert erscheinen.</span><span class="sxs-lookup"><span data-stu-id="de329-194">The syntax this example may seem a little complicated at first.</span></span> <span data-ttu-id="de329-195">Ich habe allerdings die Erfahrung gemacht, dass Sie die Syntax niemals erlernen werden, indem Sie Code kopieren und einfügen.</span><span class="sxs-lookup"><span data-stu-id="de329-195">What I have learned is that you'll never learn the syntax by copy and pasting code.</span></span> <span data-ttu-id="de329-196">Nehmen Sie sich die Zeit, den Code einzugeben.</span><span class="sxs-lookup"><span data-stu-id="de329-196">Take the time to type the code in.</span></span> <span data-ttu-id="de329-197">Wenn Sie dies ein paar Mal gemacht haben, wird es Ihnen zur zweiten Natur.</span><span class="sxs-lookup"><span data-stu-id="de329-197">After a few times, it becomes second nature.</span></span> <span data-ttu-id="de329-198">Mehrere Monitore zu haben, ist ein großer Vorteil, da Sie den Beispielcode auf dem einem Bildschirm anzeigen und ihn auf einem anderen Bildschirm eingeben können.</span><span class="sxs-lookup"><span data-stu-id="de329-198">Having multiple monitors is a huge benefit because you can display the example code on one screen and type it in on another one.</span></span>

<span data-ttu-id="de329-199">Gelegentlich kann es vorkommen, dass Sie einen Parameter verwenden möchten, der keine Pipelineeingabe akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="de329-199">Occasionally, you may want to use a parameter that doesn't accept pipeline input.</span></span> <span data-ttu-id="de329-200">Das folgende Beispiel veranschaulicht die Verwendung der Ausgabe eines Befehls als Eingabe für einen anderen.</span><span class="sxs-lookup"><span data-stu-id="de329-200">The following example demonstrates using the output of one command as input for another.</span></span> <span data-ttu-id="de329-201">Speichern Sie zuerst die Anzeigenamen einiger Windows-Dienste in einer Textdatei.</span><span class="sxs-lookup"><span data-stu-id="de329-201">First save the display name for a couple of Windows services into a text file.</span></span>

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

<span data-ttu-id="de329-202">Sie können den Befehl ausführen, der die erforderliche Ausgabe in Klammern als Wert für den Parameter des Befehls bereitstellt, der die Eingabe erfordert.</span><span class="sxs-lookup"><span data-stu-id="de329-202">You can run the command that provides the needed output within parentheses as the value for the parameter of the command requiring the input.</span></span>

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

<span data-ttu-id="de329-203">Für diejenigen, die sich noch daran erinnern können, wie dies funktioniert: Dies entspricht letztendlich der Reihenfolge von Operationen in der Algebra.</span><span class="sxs-lookup"><span data-stu-id="de329-203">This is just like order of operations in Algebra for those of you who remember how it works.</span></span> <span data-ttu-id="de329-204">Der Befehl in Klammern wird immer vor dem äußeren Teil des Befehls ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="de329-204">The command within parentheses always runs prior to the outer portion of the command.</span></span>

## <a name="powershellget"></a><span data-ttu-id="de329-205">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="de329-205">PowerShellGet</span></span>

<span data-ttu-id="de329-206">„PowerShellGet“ ist ein PowerShell-Modul, das Befehle zum Ermitteln, Installieren, Veröffentlichen und Aktualisieren von PowerShell-Modulen (und anderen Artefakten) in bzw. aus einem NuGet-Repository enthält.</span><span class="sxs-lookup"><span data-stu-id="de329-206">PowerShellGet is a PowerShell module that contains commands for discovering, installing, publishing, and updating PowerShell modules (and other artifacts) to or from a NuGet repository.</span></span> <span data-ttu-id="de329-207">„PowerShellGet“ ist im Lieferumfang von PowerShell, Version 5.0 und höher, enthalten.</span><span class="sxs-lookup"><span data-stu-id="de329-207">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="de329-208">Es steht als getrennter Download für PowerShell, Version 3.0 und höher, zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="de329-208">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="de329-209">Microsoft hostet ein NuGet-Onlinerepository mit dem Namen "[PowerShell Gallery][].</span><span class="sxs-lookup"><span data-stu-id="de329-209">Microsoft hosts an online NuGet repository called the [PowerShell Gallery][].</span></span> <span data-ttu-id="de329-210">Obwohl dieses Repository von Microsoft gehostet wird, wurde der Großteil der im Repository enthaltenen Module nicht von Microsoft geschrieben.</span><span class="sxs-lookup"><span data-stu-id="de329-210">Although this repository is hosted by Microsoft, the majority of the modules contained within the repository aren't written by Microsoft.</span></span> <span data-ttu-id="de329-211">Jeder Code, der aus dem PowerShell-Katalog abgerufen wird, sollte in einer isolierten Testumgebung gründlich überprüft werden, bevor er als für die Verwendung in einer Produktionsumgebung geeignet erachtet wird.</span><span class="sxs-lookup"><span data-stu-id="de329-211">Any code obtain from the PowerShell Gallery should be thoroughly reviewed in an isolated test environment before being considered suitable for use in a production environment.</span></span>

<span data-ttu-id="de329-212">Die meisten Unternehmen wollen wahrscheinlich ihr eigenes, internes, privates NuGet-Repository hosten, in dem sie ihre für den internen Gebrauch gedachten Module sowie aus anderen Quellen heruntergeladene Module bereitstellen können, nachdem diese als nicht böswillig validiert wurden.</span><span class="sxs-lookup"><span data-stu-id="de329-212">Most companies will want to host their own internal private NuGet repository where they can post their internal use only modules as well as modules that they've downloaded from other sources once they've validated them as being non-malicious.</span></span>

<span data-ttu-id="de329-213">Verwenden Sie das Cmdlet `Find-Module`, das Bestandteil des PowerShellGet-Moduls ist, um ein von mir geschriebenes Modul namens „MrToolkit“ im PowerShell-Katalog zu suchen.</span><span class="sxs-lookup"><span data-stu-id="de329-213">Use the `Find-Module` cmdlet that's part of the PowerShellGet module to find a module in the PowerShell Gallery that I wrote named MrToolkit.</span></span>

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

<span data-ttu-id="de329-214">Wenn Sie zum ersten Mal einen der Befehle aus dem PowerShellGet-Modul verwenden, werden Sie aufgefordert, den NuGet-Anbieter zu installieren.</span><span class="sxs-lookup"><span data-stu-id="de329-214">The first time you use one of the commands from the PowerShellGet module, you'll be prompted to install the NuGet provider.</span></span>

<span data-ttu-id="de329-215">Um das MrToolkit-Modul zu installieren, leiten Sie den vorherigen Befehl per Pipeline an `Install-Module` weiter.</span><span class="sxs-lookup"><span data-stu-id="de329-215">To install the MrToolkit module, pipe the previous command to `Install-Module`.</span></span>

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

<span data-ttu-id="de329-216">Da es sich beim PowerShell-Katalog um ein nicht vertrauenswürdiges Repository handelt, werden Sie aufgefordert, die Installation des Moduls zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="de329-216">Since the PowerShell Gallery is an untrusted repository, it prompts you to approve the installation of the module.</span></span>

## <a name="finding-pipeline-input-the-easy-way"></a><span data-ttu-id="de329-217">Pipelineeingaben suchen leicht gemacht</span><span class="sxs-lookup"><span data-stu-id="de329-217">Finding pipeline input the easy way</span></span>

<span data-ttu-id="de329-218">Das MrToolkit-Modul enthält eine Funktion namens `Get-MrPipelineInput`.</span><span class="sxs-lookup"><span data-stu-id="de329-218">The MrToolkit module contains a function named `Get-MrPipelineInput`.</span></span> <span data-ttu-id="de329-219">Dieses Cmdlet kann verwendet werden, um auf einfache Weise festzustellen, welche Parameter eines Befehls Pipelineeingaben akzeptieren, welchen Objekttyp sie akzeptieren und ob sie Pipelineeingaben **als Wert** oder **als Eigenschaftsname** akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="de329-219">This cmdlet can be used to easily determine which parameters of a command accept pipeline input, what type of object they accept, and if they accept pipeline input **by value** or **by property name**.</span></span>

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

<span data-ttu-id="de329-220">Wie Sie sehen, lassen sich dieselben Informationen, die wir zuvor mittels Durchsehen der Hilfe ermittelt haben, mit dieser Funktion problemlos bestimmen.</span><span class="sxs-lookup"><span data-stu-id="de329-220">As you can see, the same information we previously determined by sifting through the help can easily be determined with this function.</span></span>

## <a name="summary"></a><span data-ttu-id="de329-221">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="de329-221">Summary</span></span>

<span data-ttu-id="de329-222">In diesem Kapitel haben Sie PowerShell-Einzeiler kennen gelernt.</span><span class="sxs-lookup"><span data-stu-id="de329-222">In this chapter, you've learned about PowerShell one-liners.</span></span> <span data-ttu-id="de329-223">Sie haben erfahren, dass die Anzahl physischer Zeilen, in denen ein Befehl steht, nicht ausschlaggebend dafür ist, ob es sich um einen PowerShell-Einzeiler handelt oder nicht.</span><span class="sxs-lookup"><span data-stu-id="de329-223">You've learned that the number of physical lines that a command is on has nothing to do with whether or not it's a PowerShell one-liner.</span></span> <span data-ttu-id="de329-224">Außerdem haben Sie „links Filtern“, die Pipeline und PowerShellGet kennen gelernt.</span><span class="sxs-lookup"><span data-stu-id="de329-224">You've also learned about filtering left, the pipeline, and PowerShellGet.</span></span>

## <a name="review"></a><span data-ttu-id="de329-225">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="de329-225">Review</span></span>

1. <span data-ttu-id="de329-226">Was ist ein PowerShell-Einzeiler?</span><span class="sxs-lookup"><span data-stu-id="de329-226">What is a PowerShell one-liner?</span></span>
1. <span data-ttu-id="de329-227">Nennen Sie ein paar Zeichen, bei denen ein natürlicher Zeilenumbruch in PowerShell auftreten kann.</span><span class="sxs-lookup"><span data-stu-id="de329-227">What are some of the characters where natural line breaks can occur in PowerShell?</span></span>
1. <span data-ttu-id="de329-228">Warum sollten Sie links filtern?</span><span class="sxs-lookup"><span data-stu-id="de329-228">Why should you filter left?</span></span>
1. <span data-ttu-id="de329-229">Was sind die zwei Arten, auf die ein PowerShell-Befehl Pipelineeingaben akzeptieren kann?</span><span class="sxs-lookup"><span data-stu-id="de329-229">What are the two ways that a PowerShell command can accept pipeline input?</span></span>
1. <span data-ttu-id="de329-230">Warum sollten Sie die im PowerShell-Katalog gefundenen Befehlen nicht als vertrauenswürdig einstufen?</span><span class="sxs-lookup"><span data-stu-id="de329-230">Why shouldn't you trust commands found in the PowerShell Gallery?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="de329-231">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="de329-231">Recommended Reading</span></span>

- <span data-ttu-id="de329-232">[about_Pipelines][]</span><span class="sxs-lookup"><span data-stu-id="de329-232">[about_Pipelines][]</span></span>
- <span data-ttu-id="de329-233">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="de329-233">[about_Command_Syntax][]</span></span>
- <span data-ttu-id="de329-234">[about_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="de329-234">[about_Parameters][]</span></span>
- <span data-ttu-id="de329-235">[PowerShellGet: Die SUPER EINFACHE Methode zum Ermitteln, Installieren und Aktualisieren von PowerShell-Modulen][psget]</span><span class="sxs-lookup"><span data-stu-id="de329-235">[PowerShellGet: The BIG EASY way to discover, install, and update PowerShell modules][psget]</span></span>

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell Gallery]: https://www.powershellgallery.com/
