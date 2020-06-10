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
# <a name="chapter-8---powershell-remoting"></a>Kapitel 8: PowerShell-Remoting

PowerShell bietet viele verschiedene Möglichkeiten zum Ausführen von Befehlen auf Remotecomputern. Im letzten Kapitel haben Sie erfahren, wie Sie WMI mithilfe der CIM-Cmdlets remote Abfragen. PowerShell umfasst auch mehrere Cmdlets, die über einen integrierten Parameter **ComputerName** verfügen.

Wie im folgenden Beispiel gezeigt, kann `Get-Command` mit dem Parameter **ParameterName** verwendet werden, um zu bestimmen, welche Befehle einen Parameter **ComputerName-** aufweisen.

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

Befehle wie `Get-Process` und `Get-Hotfix` haben einen Parameter **ComputerName**. Dies ist nicht die langfristige Richtung, in die Microsoft sich bei der Ausführung von Befehlen auf Remotecomputern entwickeln wird. Auch wenn Sie einen Befehl finden, der über einen Parameter **ComputerName** verfügt, besteht die Wahrscheinlichkeit, dass Sie alternative Anmeldeinformationen angeben müssen, aber über keinen Parameter **Credential** verfügen. Und wenn Sie sich entschieden haben, PowerShell mit einem Konto mit erhöhten Rechten auszuführen, kann eine Firewall zwischen Ihnen und dem Remotecomputer die Anforderung blockieren.

Um die PowerShell-Remotingbefehle zu verwenden, die in diesem Kapitel demonstriert werden, muss auf dem Remotecomputer PowerShell-Remoting aktiviert sein. Verwenden Sie das Cmdlet `Enable-PSRemoting`, um PowerShell-Remoting zu aktivieren.

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

## <a name="one-to-one-remoting"></a>1:1-Remoting

Wenn Sie möchten, dass Ihre Remotesitzung interaktiv ist, sollten Sie 1:1-Remoting wählen.
Diese Art von Remoting wird über das Cmdlet `Enter-PSSession` bereitgestellt.

Im letzten Kapitel habe ich die Anmeldeinformationen meines Domänenadministrators in einer Variablen namens `$Cred` gespeichert. Wenn Sie dies noch nicht getan haben, speichern Sie jetzt die Anmeldeinformationen Ihres Domänenadministrators in der Variablen `$Cred`.

Dies ermöglicht es Ihnen, die Anmeldeinformationen einmalig einzugeben und sie dann pro Befehls zu verwenden, solange die aktuelle PowerShell-Sitzung aktiv ist.

```powershell
$Cred = Get-Credential
```

Erstellen Sie eine 1:1-PowerShell-Remotingsitzung mit dem Domänencontroller namens „dc01“.

```powershell
Enter-PSSession -ComputerName dc01 -Credential $Cred
```

```Output
[dc01]: PS C:\Users\Administrator\Documents>
```

Beachten Sie, dass im vorherigen Beispiel der PowerShell-Eingabeaufforderung `[dc01]` vorangestellt ist. Dies bedeutet, dass Sie sich in einer interaktiven PowerShell-Sitzung mit dem Remotecomputer namens „dc01“ befinden. Alle Befehle, die Sie ausführen, werden auf dc01 und nicht auf dem lokalen Computer ausgeführt. Denken Sie außerdem daran, dass Sie nur auf die PowerShell-Befehle zugreifen können, die auf dem Remotecomputer vorhanden sind, nicht auf die auf dem lokalen Computer vorhandenen. Anders ausgedrückt: Wenn Sie zusätzliche Module auf Ihrem Computer installiert haben, können Sie auf diese auf dem Remotecomputer nicht zugreifen.

Wenn Sie über eine interaktive 1:1-PowerShell-Remotingsitzung mit einem Remotecomputer verbunden sind, sitzen Sie tatsächlich an dem Remotecomputer. Die Objekte sind normale Objekte, genau wie diejenigen, mit denen Sie im gesamten vorliegenden Buch gearbeitet haben.

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

Wenn Sie mit der Arbeit am Remotecomputer fertig sind, beenden Sie die 1:1-Remotingsitzung, indem Sie das Cmdlet `Exit-PSSession` verwenden.

```powershell
[dc01]:  Exit-PSSession
```

## <a name="one-to-many-remoting"></a>1:n-Remoting

Manchmal müssen Sie möglicherweise eine Aufgabe interaktiv auf einem Remotecomputer ausführen. Remoting ist aber wesentlich leistungsfähiger, wenn Sie eine Aufgabe gleichzeitig auf mehreren Remotecomputern ausführen. Verwenden Sie das Cmdlet `Invoke-Command`, um einen Befehl auf einem oder mehreren Remotecomputern gleichzeitig auszuführen.

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

Im vorherigen Beispiel wurde bei drei Servern der Status des Windows-Zeitdiensts abgefragt. Das Cmdlet `Get-Service` wurde im Skriptblock von `Invoke-Command` platziert. `Get-Service` wird tatsächlich auf dem Remotecomputer ausgeführt, und die Ergebnisse werden als deserialisierte Objekte an Ihren lokalen Computer zurückgegeben.

Wenn Sie den vorherigen Befehl per Pipeline an `Get-Member` weiterleiten, zeigt sich, dass die Ergebnisse tatsächlich deserialisierte Objekte sind.

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

Beachten Sie, dass die Mehrzahl der Methoden bei deserialisierten Objekten fehlt. Dies bedeutet, dass Sie keine Liveobjekte sind, sie sind inaktiv. Sie können einen Dienst nicht mit einem deserialisierten Objekt starten oder beenden, weil es sich um eine Momentaufnahme des Zustands dieses Objekts zu dem Zeitpunkt handelt, an dem der Befehl auf dem Remotecomputer ausgeführt wurde.

Dies bedeutet nicht, dass Sie einen Dienst nicht mithilfe einer Methode mit `Invoke-Command` starten oder beenden können. Es bedeutet lediglich, dass die Methode in der Remotesitzung aufgerufen werden muss.

Ich beende den Windows-Zeitdienst auf allen drei Remoteservern mit der Methode **Stopp()** , um diesen Punkt zu beweisen.

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

Wie in einem vorherigen Kapitel bereits erwähnt, empfehle ich, wenn ein Cmdlet vorhanden ist, um diese Aufgabe zu erledigen, dieses anstelle einer Methode zu verwenden. Im vorherigen Szenario empfehle ich, anstelle der Stop-Methode das Cmdlet `Stop-Service` zu verwenden. Ich habe mich entschieden, die Methode **Stop()** zu verwenden, um einen Punkt zu beweisen, da viele Personen dem Missverständnis unterliegen, dass Methoden bei Verwendung von PowerShell-Remoting nicht aufgerufen werden können. Sie können nicht für das Objekt aufgerufen werden, das zurückgegeben wird, da es deserialisiert ist, aber sie können in der Remotesitzung selbst aufgerufen werden.

## <a name="powershell-sessions"></a>PowerShell-Sitzungen

Im letzten Beispiel im vorherigen Abschnitt habe ich zwei Befehle mithilfe des Cmdlets `Invoke-Command` ausgeführt.
Dies bedeutet, dass zwei gesonderte Sitzungen eingerichtet und abgebrochen werden mussten, um diese beiden Befehle auszuführen.

Ähnlich wie bei den in Kapitel 7 behandelten CIM-Sitzungen kann eine PowerShell-Sitzung auf einem Remotecomputer verwendet werden, um mehrere Befehle auf dem Remotecomputer auszuführen, ohne dass für jeden einzelnen Befehl eine neue Sitzung benötigt wird.

Erstellen Sie eine PowerShell-Sitzung für jeden der drei Computer, mit denen wir in diesem Kapitel gearbeitet haben: DC01, SQL02 und WEB01.

```powershell
$Session = New-PSSession -ComputerName dc01, sql02, web01 -Credential $Cred
```

Verwenden Sie nun die Variable namens `$Session`, um den Windows-Zeitdienst mithilfe einer Methode zu starten und den Status des Diensts zu überprüfen.

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

Nachdem die Sitzung mit alternativen Anmeldeinformationen erstellt wurde, ist es nicht mehr notwendig, die Anmeldeinformationen bei jeder Ausführung eines Befehl anzugeben.

Wenn Sie mit der Verwendung der Sitzungen fertig sind, müssen Sie diese entfernen.

```powershell
Get-PSSession | Remove-PSSession
```

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie mehr über PowerShell-Remoting erfahren, wie Sie Befehle in einer interaktiven Sitzung mit einem einzelnen Remotecomputer ausführen, und wie Sie Befehle auf mehreren Computern mithilfe von 1:n-Remoting ausführen. Sie haben ferner die Vorteile der Verwendung einer PowerShell-Sitzung kennengelernt, wenn Sie mehrere Befehle auf demselben Remotecomputer ausführen.

## <a name="review"></a>Überprüfung

1. Wie aktivieren Sie PowerShell-Remoting?
1. Wie lautet der PowerShell-Befehl für das Starten einer interaktiven Sitzung mit einem Remotecomputer?
1. Was ist ein Vorteil bei der Verwendung einer PowerShell-Remotingsitzung im Gegensatz zum bloßen Angeben des Computernamens mit jedem Befehl?
1. Kann eine PowerShell-Remotingsitzung mit einer 1:1-Remotingsitzung verwendet werden?
1. Worin besteht der Unterschied zwischen dem Typ der Objekte, die von Cmdlets zurückgegeben werden, und denen, die zurückgegeben werden, wenn dieselben Cmdlets auf Remotecomputern mit `Invoke-Command` ausgeführt werden?

## <a name="recommended-reading"></a>Empfohlene Lektüre

- [about_Remote][]
- [about_Remote_FAQ][]
- [about_Remote_Output][]
- [about_Remote_Requirements][]
- [about_Remote_Troubleshooting][]
- [about_Remote_Variables][]

<!-- link references -->
[about_Remote]: /powershell/module/microsoft.powershell.core/about/about_remote
[about_Remote_FAQ]: /powershell/module/microsoft.powershell.core/about/about_remote_faq
[about_Remote_Output]: /powershell/module/microsoft.powershell.core/about/about_remote_output
[about_Remote_Requirements]: /powershell/module/microsoft.powershell.core/about/about_remote_requirements
[about_Remote_Troubleshooting]: /powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting
[about_Remote_Variables]: /powershell/module/microsoft.powershell.core/about/about_remote_variables
[Breaking changes in PowerShell 6.0]: /powershell/scripting/whats-new/breaking-changes-ps6#remove--protocol-from--computer-cmdlets-5277
