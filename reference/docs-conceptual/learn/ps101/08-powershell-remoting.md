---
title: PowerShell-Remoting
description: Es gibt viele verschiedene Möglichkeiten, Befehle auf Remotecomputern in PowerShell auszuführen.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ee83af41b53b254dd3dd993931333edac2f44f5a
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438211"
---
# <a name="chapter-8---powershell-remoting"></a><span data-ttu-id="ba9a8-103">Kapitel 8: PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="ba9a8-103">Chapter 8 - PowerShell remoting</span></span>

<span data-ttu-id="ba9a8-104">PowerShell bietet viele verschiedene Möglichkeiten zum Ausführen von Befehlen auf Remotecomputern.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-104">PowerShell has many different ways to run commands against remote computers.</span></span> <span data-ttu-id="ba9a8-105">Im letzten Kapitel haben Sie erfahren, wie Sie WMI mithilfe der CIM-Cmdlets remote Abfragen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-105">In the last chapter, you saw how to remotely query WMI using the CIM cmdlets.</span></span> <span data-ttu-id="ba9a8-106">PowerShell umfasst auch mehrere Cmdlets, die über einen integrierten Parameter **ComputerName** verfügen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-106">PowerShell also includes several cmdlets that have a built-in **ComputerName** parameter.</span></span>

<span data-ttu-id="ba9a8-107">Wie im folgenden Beispiel gezeigt, kann `Get-Command` mit dem Parameter **ParameterName** verwendet werden, um zu bestimmen, welche Befehle einen Parameter **ComputerName-** aufweisen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-107">As shown in the following example, `Get-Command` can be used with the **ParameterName** parameter to determine what commands have a **ComputerName** parameter.</span></span>

```powershell
Get-Command -ParameterName ComputerName
```

```Output
CommandType Name                        Version Source
----------- ----                        ------- ------
Cmdlet      Connect-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Connect-WSMan               7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Disconnect-WSMan            7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Enter-PSSession             7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-CimAssociatedInstance   7.0.0.0 CimCmdlets
Cmdlet      Get-CimClass                7.0.0.0 CimCmdlets
Cmdlet      Get-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Get-CimSession              7.0.0.0 CimCmdlets
Cmdlet      Get-Counter                 7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-HotFix                  7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Get-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Get-WinEvent                7.0.0.0 Microsoft.PowerShell.Diagnostics
Cmdlet      Get-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Invoke-CimMethod            7.0.0.0 CimCmdlets
Cmdlet      Invoke-Command              7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Invoke-WSManAction          7.0.0.0 Microsoft.WSMan.Management
Cmdlet      New-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      New-CimSession              7.0.0.0 CimCmdlets
Cmdlet      New-PSSession               7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      New-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Receive-Job                 7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Receive-PSSession           7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Register-CimIndicationEvent 7.0.0.0 CimCmdlets
Cmdlet      Remove-CimInstance          7.0.0.0 CimCmdlets
Cmdlet      Remove-CimSession           7.0.0.0 CimCmdlets
Cmdlet      Remove-PSSession            7.0.1.0 Microsoft.PowerShell.Core
Cmdlet      Remove-WSManInstance        7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Rename-Computer             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Restart-Computer            7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Send-MailMessage            7.0.0.0 Microsoft.PowerShell.Utility
Cmdlet      Set-CimInstance             7.0.0.0 CimCmdlets
Cmdlet      Set-WSManInstance           7.0.0.0 Microsoft.WSMan.Management
Cmdlet      Stop-Computer               7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-Connection             7.0.0.0 Microsoft.PowerShell.Management
Cmdlet      Test-WSMan                  7.0.0.0 Microsoft.WSMan.Management
```

<span data-ttu-id="ba9a8-108">Befehle wie `Get-Process` und `Get-Hotfix` haben einen Parameter **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-108">Commands such as `Get-Process` and `Get-Hotfix` have a **ComputerName** parameter.</span></span> <span data-ttu-id="ba9a8-109">Dies ist nicht die langfristige Richtung, in die Microsoft sich bei der Ausführung von Befehlen auf Remotecomputern entwickeln wird.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-109">This isn't the long-term direction that Microsoft is heading for running commands against remote computers.</span></span> <span data-ttu-id="ba9a8-110">Auch wenn Sie einen Befehl finden, der über einen Parameter **ComputerName** verfügt, besteht die Wahrscheinlichkeit, dass Sie alternative Anmeldeinformationen angeben müssen, aber über keinen Parameter **Credential** verfügen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-110">Even if you find a command that has a **ComputerName** parameter, chances are that you'll need to specify alternate credentials and it won't have a **Credential** parameter.</span></span> <span data-ttu-id="ba9a8-111">Und wenn Sie sich entschieden haben, PowerShell mit einem Konto mit erhöhten Rechten auszuführen, kann eine Firewall zwischen Ihnen und dem Remotecomputer die Anforderung blockieren.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-111">And if you decided to run PowerShell from an elevated account, a firewall between you and the remote computer can block the request.</span></span>

<span data-ttu-id="ba9a8-112">Um die PowerShell-Remotingbefehle zu verwenden, die in diesem Kapitel demonstriert werden, muss auf dem Remotecomputer PowerShell-Remoting aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-112">To use the PowerShell remoting commands that are demonstrated in this chapter, PowerShell remoting must be enabled on the remote computer.</span></span> <span data-ttu-id="ba9a8-113">Verwenden Sie das Cmdlet `Enable-PSRemoting`, um PowerShell-Remoting zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-113">Use the `Enable-PSRemoting` cmdlet to enable PowerShell remoting.</span></span>

```powershell
Enable-PSRemoting
```

```Output
WinRM has been updated to receive requests.
WinRM service type changed successfully.
WinRM service started.

WinRM has been updated for remote management.
WinRM firewall exception enabled.
```

## <a name="one-to-one-remoting"></a><span data-ttu-id="ba9a8-114">1:1-Remoting</span><span class="sxs-lookup"><span data-stu-id="ba9a8-114">One-To-One Remoting</span></span>

<span data-ttu-id="ba9a8-115">Wenn Sie möchten, dass Ihre Remotesitzung interaktiv ist, sollten Sie 1:1-Remoting wählen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-115">If you want your remote session to be interactive, then one-to-one remoting is what you want.</span></span>
<span data-ttu-id="ba9a8-116">Diese Art von Remoting wird über das Cmdlet `Enter-PSSession` bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-116">This type of remoting is provided via the `Enter-PSSession` cmdlet.</span></span>

<span data-ttu-id="ba9a8-117">Im letzten Kapitel habe ich die Anmeldeinformationen meines Domänenadministrators in einer Variablen namens `$Cred` gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-117">In the last chapter, I stored my domain admin credentials in a variable named `$Cred`.</span></span> <span data-ttu-id="ba9a8-118">Wenn Sie dies noch nicht getan haben, speichern Sie jetzt die Anmeldeinformationen Ihres Domänenadministrators in der Variablen `$Cred`.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-118">If you haven't already done so, go ahead and store your domain admin credentials in the `$Cred` variable.</span></span>

<span data-ttu-id="ba9a8-119">Dies ermöglicht es Ihnen, die Anmeldeinformationen einmalig einzugeben und sie dann pro Befehls zu verwenden, solange die aktuelle PowerShell-Sitzung aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-119">This allows you to enter the credentials once and use them on a per command basis as long as your current PowerShell session is active.</span></span>

```powershell
$Cred = Get-Credential
```

<span data-ttu-id="ba9a8-120">Erstellen Sie eine 1:1-PowerShell-Remotingsitzung mit dem Domänencontroller namens „dc01“.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-120">Create a one-to-one PowerShell remoting session to the domain controller named dc01.</span></span>

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

<span data-ttu-id="ba9a8-121">Beachten Sie, dass im vorherigen Beispiel der PowerShell-Eingabeaufforderung `[dc01]` vorangestellt ist.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-121">Notice that in the previous example that the PowerShell prompt is preceded by `[dc01]`.</span></span> <span data-ttu-id="ba9a8-122">Dies bedeutet, dass Sie sich in einer interaktiven PowerShell-Sitzung mit dem Remotecomputer namens „dc01“ befinden.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-122">This means you're in an interactive PowerShell session to the remote computer named dc01.</span></span> <span data-ttu-id="ba9a8-123">Alle Befehle, die Sie ausführen, werden auf dc01 und nicht auf dem lokalen Computer ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-123">Any commands you execute run on dc01, not on your local computer.</span></span> <span data-ttu-id="ba9a8-124">Denken Sie außerdem daran, dass Sie nur auf die PowerShell-Befehle zugreifen können, die auf dem Remotecomputer vorhanden sind, nicht auf die auf dem lokalen Computer vorhandenen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-124">Also, keep in mind that you only have access to the PowerShell commands that exist on the remote computer and not the ones on your local computer.</span></span> <span data-ttu-id="ba9a8-125">Anders ausgedrückt: Wenn Sie zusätzliche Module auf Ihrem Computer installiert haben, können Sie auf diese auf dem Remotecomputer nicht zugreifen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-125">In other words, if you've installed additional modules on your computer, they aren't accessible on the remote computer.</span></span>

<span data-ttu-id="ba9a8-126">Wenn Sie über eine interaktive 1:1-PowerShell-Remotingsitzung mit einem Remotecomputer verbunden sind, sitzen Sie tatsächlich an dem Remotecomputer.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-126">When you're connected to a remote computer via a one-to-one interactive PowerShell remoting session, you're effectively sitting at the remote computer.</span></span> <span data-ttu-id="ba9a8-127">Die Objekte sind normale Objekte, genau wie diejenigen, mit denen Sie im gesamten vorliegenden Buch gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-127">The objects are normal objects just like the ones you've been working with throughout this entire book.</span></span>

```powershell
[dc01]:  Get-Process | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
[dc01]:
```

<span data-ttu-id="ba9a8-128">Wenn Sie mit der Arbeit am Remotecomputer fertig sind, beenden Sie die 1:1-Remotingsitzung, indem Sie das Cmdlet `Exit-PSSession` verwenden.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-128">When you're done working with the remote computer, exit the one-to-one remoting session by using the `Exit-PSSession` cmdlet.</span></span>

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a><span data-ttu-id="ba9a8-129">1:n-Remoting</span><span class="sxs-lookup"><span data-stu-id="ba9a8-129">One-To-Many Remoting</span></span>

<span data-ttu-id="ba9a8-130">Manchmal müssen Sie möglicherweise eine Aufgabe interaktiv auf einem Remotecomputer ausführen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-130">Sometimes you may need to perform a task interactively on a remote computer.</span></span> <span data-ttu-id="ba9a8-131">Remoting ist aber wesentlich leistungsfähiger, wenn Sie eine Aufgabe gleichzeitig auf mehreren Remotecomputern ausführen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-131">But remoting is much more powerful when performing a task on multiple remote computers at the same time.</span></span> <span data-ttu-id="ba9a8-132">Verwenden Sie das Cmdlet `Invoke-Command`, um einen Befehl auf einem oder mehreren Remotecomputern gleichzeitig auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-132">Use the `Invoke-Command` cmdlet to run a command against one or more remote computers at the same time.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="ba9a8-133">Im vorherigen Beispiel wurde bei drei Servern der Status des Windows-Zeitdiensts abgefragt.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-133">In the previous example, three servers were queried for the status of the Windows Time service.</span></span> <span data-ttu-id="ba9a8-134">Das Cmdlet `Get-Service` wurde im Skriptblock von `Invoke-Command` platziert.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-134">The `Get-Service` cmdlet was placed inside the script block of `Invoke-Command`.</span></span> <span data-ttu-id="ba9a8-135">`Get-Service` wird tatsächlich auf dem Remotecomputer ausgeführt, und die Ergebnisse werden als deserialisierte Objekte an Ihren lokalen Computer zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-135">`Get-Service` actually runs on the remote computer and the results are returned to your local computer as deserialized objects.</span></span>

<span data-ttu-id="ba9a8-136">Wenn Sie den vorherigen Befehl per Pipeline an `Get-Member` weiterleiten, zeigt sich, dass die Ergebnisse tatsächlich deserialisierte Objekte sind.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-136">Piping the previous command to `Get-Member` shows that the results are indeed deserialized objects.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred | Get-Member
```

```Output
   TypeName: Deserialized.System.ServiceProcess.ServiceController

Name                MemberType   Definition
----                ----------   ----------
GetType             Method       type GetType()
ToString            Method       string ToString(), string ToString(string format, Sys...
Name                NoteProperty string Name=W32time
PSComputerName      NoteProperty string PSComputerName=sql02
PSShowComputerName  NoteProperty bool PSShowComputerName=True
RequiredServices    NoteProperty Deserialized.System.ServiceProcess.ServiceController[...
RunspaceId          NoteProperty guid RunspaceId=570313c4-ac84-4109-bf67-c6b33236af0a
CanPauseAndContinue Property     System.Boolean {get;set;}
CanShutdown         Property     System.Boolean {get;set;}
CanStop             Property     System.Boolean {get;set;}
Container           Property      {get;set;}
DependentServices   Property     Deserialized.System.ServiceProcess.ServiceController[...
DisplayName         Property     System.String {get;set;}
MachineName         Property     System.String {get;set;}
ServiceHandle       Property     System.String {get;set;}
ServiceName         Property     System.String {get;set;}
ServicesDependedOn  Property     Deserialized.System.ServiceProcess.ServiceController[...
ServiceType         Property     System.String {get;set;}
Site                Property      {get;set;}
StartType           Property     System.String {get;set;}
Status              Property     System.String {get;set;}
```

<span data-ttu-id="ba9a8-137">Beachten Sie, dass die Mehrzahl der Methoden bei deserialisierten Objekten fehlt.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-137">Notice that the majority of the methods are missing on deserialized objects.</span></span> <span data-ttu-id="ba9a8-138">Dies bedeutet, dass Sie keine Liveobjekte sind, sie sind inaktiv.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-138">This means they're not live objects; they're inert.</span></span> <span data-ttu-id="ba9a8-139">Sie können einen Dienst nicht mit einem deserialisierten Objekt starten oder beenden, weil es sich um eine Momentaufnahme des Zustands dieses Objekts zu dem Zeitpunkt handelt, an dem der Befehl auf dem Remotecomputer ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-139">You can't start or stop a service using a deserialized object because it's a snapshot of the state of that object the point when the command ran on the remote computer.</span></span>

<span data-ttu-id="ba9a8-140">Dies bedeutet nicht, dass Sie einen Dienst nicht mithilfe einer Methode mit `Invoke-Command` starten oder beenden können.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-140">That doesn't mean you can't start or stop a service using a method with `Invoke-Command` though.</span></span> <span data-ttu-id="ba9a8-141">Es bedeutet lediglich, dass die Methode in der Remotesitzung aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-141">It just means that the method has to be called in the remote session.</span></span>

<span data-ttu-id="ba9a8-142">Ich beende den Windows-Zeitdienst auf allen drei Remoteservern mit der Methode **Stopp()** , um diesen Punkt zu beweisen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-142">I'll stop the Windows Time service on all three of those remote servers using the **Stop()** method to prove this point.</span></span>

```powershell
Invoke-Command -ComputerName dc01, sql02, web01 {(Get-Service -Name W32time).Stop()} -Credential $Cred
Invoke-Command -ComputerName dc01, sql02, web01 {Get-Service -Name W32time} -Credential $Cred
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="ba9a8-143">Wie in einem vorherigen Kapitel bereits erwähnt, empfehle ich, wenn ein Cmdlet vorhanden ist, um diese Aufgabe zu erledigen, dieses anstelle einer Methode zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-143">As mentioned in a previous chapter, if a cmdlet exists for accomplishing a task, I recommend using it instead of using a method.</span></span> <span data-ttu-id="ba9a8-144">Im vorherigen Szenario empfehle ich, anstelle der Stop-Methode das Cmdlet `Stop-Service` zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-144">In the previous scenario, I recommend using the `Stop-Service` cmdlet instead of the stop method.</span></span> <span data-ttu-id="ba9a8-145">Ich habe mich entschieden, die Methode **Stop()** zu verwenden, um einen Punkt zu beweisen, da viele Personen dem Missverständnis unterliegen, dass Methoden bei Verwendung von PowerShell-Remoting nicht aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-145">I chose to use the **Stop()** method to prove a point since many people are under the misconception that methods can't be called when using PowerShell remoting.</span></span> <span data-ttu-id="ba9a8-146">Sie können nicht für das Objekt aufgerufen werden, das zurückgegeben wird, da es deserialisiert ist, aber sie können in der Remotesitzung selbst aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-146">They can't be called on the object that's returned because it's deserialized, but they can be called in the remote session itself.</span></span>

## <a name="powershell-sessions"></a><span data-ttu-id="ba9a8-147">PowerShell-Sitzungen</span><span class="sxs-lookup"><span data-stu-id="ba9a8-147">PowerShell Sessions</span></span>

<span data-ttu-id="ba9a8-148">Im letzten Beispiel im vorherigen Abschnitt habe ich zwei Befehle mithilfe des Cmdlets `Invoke-Command` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-148">In the last example in the previous section, I ran two commands using the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="ba9a8-149">Dies bedeutet, dass zwei gesonderte Sitzungen eingerichtet und abgebrochen werden mussten, um diese beiden Befehle auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-149">That means two separate sessions had to be set up and torn down to run those two commands.</span></span>

<span data-ttu-id="ba9a8-150">Ähnlich wie bei den in Kapitel 7 behandelten CIM-Sitzungen kann eine PowerShell-Sitzung auf einem Remotecomputer verwendet werden, um mehrere Befehle auf dem Remotecomputer auszuführen, ohne dass für jeden einzelnen Befehl eine neue Sitzung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-150">Similar to the CIM sessions discussed in Chapter 7, a PowerShell session to a remote computer can be used to run multiple commands against the remote computer without the overhead of a new session for each individual command.</span></span>

<span data-ttu-id="ba9a8-151">Erstellen Sie eine PowerShell-Sitzung für jeden der drei Computer, mit denen wir in diesem Kapitel gearbeitet haben: DC01, SQL02 und WEB01.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-151">Create a PowerShell session to each of the three computers we've been working with in this chapter, DC01, SQL02, and WEB01.</span></span>

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

<span data-ttu-id="ba9a8-152">Verwenden Sie nun die Variable namens `$Session`, um den Windows-Zeitdienst mithilfe einer Methode zu starten und den Status des Diensts zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-152">Now use the variable named `$Session` to start the Windows Time service using a method and check the status of the service.</span></span>

```powershell
Invoke-Command -Session $Session {(Get-Service -Name W32time).Start()}
Invoke-Command -Session $Session {Get-Service -Name W32time}
```

```Output
Status   Name        DisplayName       PSComputerName
------   ----        -----------       --------------
Running  W32time     Windows Time      web01
Start... W32time     Windows Time      dc01
Running  W32time     Windows Time      sql02
```

<span data-ttu-id="ba9a8-153">Nachdem die Sitzung mit alternativen Anmeldeinformationen erstellt wurde, ist es nicht mehr notwendig, die Anmeldeinformationen bei jeder Ausführung eines Befehl anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-153">Once the session is created using alternate credentials, it's no longer necessary to specify the credentials each time a command is run.</span></span>

<span data-ttu-id="ba9a8-154">Wenn Sie mit der Verwendung der Sitzungen fertig sind, müssen Sie diese entfernen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-154">When you're finished using the sessions, be sure to remove them.</span></span>

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a><span data-ttu-id="ba9a8-155">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="ba9a8-155">Summary</span></span>

<span data-ttu-id="ba9a8-156">In diesem Kapitel haben Sie mehr über PowerShell-Remoting erfahren, wie Sie Befehle in einer interaktiven Sitzung mit einem einzelnen Remotecomputer ausführen, und wie Sie Befehle auf mehreren Computern mithilfe von 1:n-Remoting ausführen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-156">In this chapter you've learned about PowerShell remoting, how to run commands in an interactive session with one remote computer, and how to run commands against multiple computers using one-to-many remoting.</span></span> <span data-ttu-id="ba9a8-157">Sie haben ferner die Vorteile der Verwendung einer PowerShell-Sitzung kennengelernt, wenn Sie mehrere Befehle auf demselben Remotecomputer ausführen.</span><span class="sxs-lookup"><span data-stu-id="ba9a8-157">You've also learned the benefits of using a PowerShell session when running multiple commands against the same remote computer.</span></span>

## <a name="review"></a><span data-ttu-id="ba9a8-158">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="ba9a8-158">Review</span></span>

1. <span data-ttu-id="ba9a8-159">Wie aktivieren Sie PowerShell-Remoting?</span><span class="sxs-lookup"><span data-stu-id="ba9a8-159">How do you enable PowerShell remoting?</span></span>
1. <span data-ttu-id="ba9a8-160">Wie lautet der PowerShell-Befehl für das Starten einer interaktiven Sitzung mit einem Remotecomputer?</span><span class="sxs-lookup"><span data-stu-id="ba9a8-160">What is the PowerShell command for starting an interactive session with a remote computer?</span></span>
1. <span data-ttu-id="ba9a8-161">Was ist ein Vorteil bei der Verwendung einer PowerShell-Remotingsitzung im Gegensatz zum bloßen Angeben des Computernamens mit jedem Befehl?</span><span class="sxs-lookup"><span data-stu-id="ba9a8-161">What is a benefit of using a PowerShell remoting session versus just specifying the computer name with each command?</span></span>
1. <span data-ttu-id="ba9a8-162">Kann eine PowerShell-Remotingsitzung mit einer 1:1-Remotingsitzung verwendet werden?</span><span class="sxs-lookup"><span data-stu-id="ba9a8-162">Can a PowerShell remoting session be used with a one-to-one remoting session?</span></span>
1. <span data-ttu-id="ba9a8-163">Worin besteht der Unterschied zwischen dem Typ der Objekte, die von Cmdlets zurückgegeben werden, und denen, die zurückgegeben werden, wenn dieselben Cmdlets auf Remotecomputern mit `Invoke-Command` ausgeführt werden?</span><span class="sxs-lookup"><span data-stu-id="ba9a8-163">What is the difference in the type of objects that are returned by cmdlets versus those returned when running those same cmdlets against remote computers with `Invoke-Command`?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="ba9a8-164">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="ba9a8-164">Recommended Reading</span></span>

- <span data-ttu-id="ba9a8-165">[about_Remote][]</span><span class="sxs-lookup"><span data-stu-id="ba9a8-165">[about_Remote][]</span></span>
- <span data-ttu-id="ba9a8-166">[about_Remote_FAQ][]</span><span class="sxs-lookup"><span data-stu-id="ba9a8-166">[about_Remote_FAQ][]</span></span>
- <span data-ttu-id="ba9a8-167">[about_Remote_Output][]</span><span class="sxs-lookup"><span data-stu-id="ba9a8-167">[about_Remote_Output][]</span></span>
- <span data-ttu-id="ba9a8-168">[about_Remote_Requirements][]</span><span class="sxs-lookup"><span data-stu-id="ba9a8-168">[about_Remote_Requirements][]</span></span>
- <span data-ttu-id="ba9a8-169">[about_Remote_Troubleshooting][]</span><span class="sxs-lookup"><span data-stu-id="ba9a8-169">[about_Remote_Troubleshooting][]</span></span>
- <span data-ttu-id="ba9a8-170">[about_Remote_Variables][]</span><span class="sxs-lookup"><span data-stu-id="ba9a8-170">[about_Remote_Variables][]</span></span>

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
