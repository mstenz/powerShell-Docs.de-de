---
title: Entdecken von Objekten, Eigenschaften und Methoden
description: Sie müssen kein Entwickler sein, um Objekte, Eigenschaften und Methoden zu verstehen und zu verwenden.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 5ab972755afeba0d94bf6c2debaf84ec84cd9244
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438071"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a>Kapitel 3: Entdecken von Objekten, Eigenschaften und Methoden

Meine erste Begegnung mit Computern war ein Commodore 64, aber mein erster moderner Computer war ein 286 12-MHz-IBM-Klon mit 1 MB Arbeitsspeicher, einer 40 MB-Festplatte und einem 5-1/4-Zoll-Diskettenlaufwerk mit einem CGA-Monitor, der unter Microsoft DOS 3.3 lief.

Viele IT-Profis wie ich selbst kennen sich mit der Befehlszeile aus, doch sobald das Thema „Objekte, Eigenschaften und Methoden“ aufkommt, bekommen sie schreckgeweitete, große Augen und sagen: „Ich bin kein Entwickler.“. Aber wissen Sie was? Sie müssen kein Entwickler sein, um erfolgreich mit PowerShell zu arbeiten. Verzetteln Sie sich nicht bei der Terminologie. Nicht alles mag anfänglich Sinn ergeben, aber nach ein wenig praktischer Erfahrung werden Sie immer öfter diese „Mir geht ein Licht auf“-Momente erleben. „Aha! Also das war im Buch gemeint.“

Stellen Sie sicher, dass Sie die Beispiele auf Ihrem Computer ausprobieren, um praktische Erfahrung zu sammeln.

## <a name="requirements"></a>Requirements (Anforderungen)

Das Active Directory PowerShell-Modul ist für einige der in diesem Kapitel gezeigten Beispiele erforderlich.
Das Modul ist Bestandteil der Remoteserver-Verwaltungstools (Remote Server Administration Tools, RSAT) für Windows. Für den Build 1809 (oder höher) von Windows werden die RSAT-Tools als Windows-Funktion installiert.

- Informationen zum Installieren der RSAT-Tools finden Sie unter [Windows-Verwaltungsmodule][].
- Informationen zu älteren Versionen von Windows finden Sie unter [RSAT für Windows][].

## <a name="get-member"></a>Get-Member

`Get-Member` hilft Ihnen herauszufinden, welche Objekte, Eigenschaften und Methoden für Befehle verfügbar sind.
Jeder Befehl, der eine objektbasierte Ausgabe erzeugt, kann per Pipeline an `Get-Member` weitergeleitet werden. Eine Eigenschaft ist ein Merkmal eines Elements. Ihr Führerschein besitzt eine Eigenschaft namens „Augenfarbe“, und die häufigsten Werte für diese Eigenschaft sind „Blau“ und „Braun“. Eine Methode ist eine Aktion, die an einem Objekt vorgenommen werden kann. Um im Führerscheinbeispiel zu bleiben: Eine der Methoden ist „Entziehen“ (Revoke), weil das Straßenverkehrsamt Ihren Führerschein einziehen kann.

### <a name="properties"></a>Eigenschaften

Im folgenden Beispiel rufe ich Informationen zum Windows-Zeitdienst ab, der auf meinem Computer ausgeführt wird.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

**Status**, **Name**und **DisplayName** (Anzeigename) sind Beispiele für Eigenschaften, wie im vorherigen Resultset gezeigt. Der Wert der Eigenschaft **Status** ist `Running`, der Wert der Eigenschaft **Name** ist `w32time`, und der Wert von **DisplayName** ist `Windows Time`.

Nun leite ich denselben Befehl per Pipeline an `Get-Member` weiter:

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

Die erste Zeile der Ergebnisse im vorherigen Beispiel enthält eine sehr wichtige Information. **TypeName** gibt an, welcher Objekttyp zurückgegeben wurde. In diesem Beispiel wurde ein **System.ServiceProcess.ServiceController**-Objekt zurückgegeben. Dies wird häufig als der Teil von **TypeName** direkt hinter dem letzten Punkt abgekürzt, in diesem Beispiel also **ServiceController**.

Sobald Sie wissen, welcher Objekttyp von einem Befehl erzeugt wird, können Sie diese Information verwenden, um Befehle zu identifizieren, die diesen Objekttyp als Eingabe akzeptieren.

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

Alle diese Befehle verfügen über einen Parameter, der einen **ServiceController**-Objekttyp per Pipeline, Parametereingabe oder über beides akzeptiert.

Beachten Sie, dass es mehr Eigenschaften gibt, als standardmäßig angezeigt werden. Obwohl diese zusätzlichen Eigenschaften standardmäßig nicht angezeigt werden, können Sie in der Pipeline ausgewählt werden, indem Sie den Befehl per Pipeline an das Cmdlet `Select-Object` weiterleiten und den Parameter **Property** verwenden. Im folgenden Beispiel werden alle Eigenschaften ausgewählt, indem die Ergebnisse von `Get-Service` per Pipeline an `Select-Object` weitergeleitet werden und das Platzhalterzeichen `*` als Wert für den Parameter **Property** angegeben wird.

```powershell
Get-Service -Name w32time | Select-Object -Property *
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

Bestimmte Eigenschaften lassen sich auch auswählen, indem an den Parameter **Property** eine durch Trennzeichen getrennte Liste als Wert übergeben wird.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

Standardmäßig werden vier Eigenschaften in einer Tabelle zurückgegeben und fünf oder mehr in einer Liste. Einige Befehle verwenden benutzerdefinierte Formatierung, um außer Kraft zu setzen, wie viele Eigenschaften standardmäßig in einer Tabelle angezeigt werden.
Es gibt mehrere `Format-*`-Cmdlets, die verwendet werden können, um diese Standardeinstellungen manuell zu überschreiben. Die gängigsten sind `Format-Table` und `Format-List`, die beide in einem zukünftigen Kapitel behandelt werden.

Platzhalterzeichen können beim Angeben der Eigenschaftsnamen mit `Select-Object` verwendet werden.

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

Im vorherigen Beispiel wurde `Can*` als einer der Werte für den Parameter **Property** verwendet, um alle Eigenschaften zurückzugeben, die mit `Can` beginnen. Hierzu gehören **CanPauseAndContinue**, **CanShutdown** und **CanStop**.

### <a name="methods"></a>Methoden

Methoden sind Aktionen, die ausgeführt werden können. Verwenden Sie den Parameter **MemberType**, um die Ergebnisse von `Get-Member` so einzugrenzen, dass nur die Methoden für `Get-Service` angezeigt werden.

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

Wie sie sehen können, gibt es zahlreiche Methoden. Mithilfe der **Stop**-Methode können Sie einen Windows-Dienst beenden.

```powershell
(Get-Service -Name w32time).Stop()
```

Nun überprüfen wir, ob der Windows-Zeitdienst tatsächlich beendet wurde.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

Ich selbst verwende diese Methoden selten, aber Sie sollten sie dennoch kennen. Es kann vorkommen, dass Ihnen ein `Get-*`-Befehl begegnet, ohne dass ein entsprechender Befehl zum Ändern des Elements vorhanden wäre.
Häufig kann dann eine Methode verwendet werden, um eine Aktion auszuführen, mit der das Element geändert wird. Das Cmdlet `Get-SqlAgentJob` im SqlServer PowerShell-Modul ist ein gutes Beispiel dafür. Das Modul wird als Bestandteil von [SQL Server Management Studio (SSMS)][SMSS] installiert. Es gibt kein entsprechendes `Set-*`-Cmdlet, aber dieselbe Aufgabe kann mit einer Methode erledigt werden.

Ein weiterer Grund, Methoden zu kennen, besteht darin, dass viele Einsteiger davon ausgehen, dass mit `Get-*`-Befehlen keine destruktiven Änderungen möglich sind. Allerdings können sie schwerwiegende Probleme verursachen, wenn Sie nicht ordnungsgemäß verwendet werden.

Eine bessere Option ist es, ein Cmdlet zu verwenden, um die Aktion auszuführen, wenn eins vorhanden ist. Fahren Sie fort, und starten Sie den Windows-Zeitdienst, nur diesmal mit dem Unterschied, dass Sie das Cmdlet zum Starten von Diensten verwenden.

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Standardmäßig gibt `Start-Service` keine Ergebnisse zurück, genau wie die Start-Methode von `Get-Service`.
Einer der Vorteile bei der Verwendung eines Cmdlets ist jedoch, dass das Cmdlet oft zusätzliche Funktionen bietet, die mit einer Methode nicht verfügbar sind. Im vorherigen Beispiel wurde der Parameter **PassThru** verwendet. Dieser bewirkt, dass ein Cmdlet, das normalerweise keine Ausgabe erzeugt, Ausgaben erzeugt.

Seien Sie immer vorsichtig mit Annahmen zur Ausgabe eines Cmdlets. Wir alle wissen, was passiert, wenn man etwas voraussetzt. Ich rufe nun Informationen über den PowerShell-Prozess, der auf meinem Computer in der Windows 10-Laborumgebung ausgeführt wird, ab.

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

Nun leite ich denselben Befehl per Pipeline an „Get-Member“ weiter:

```powershell
Get-Process -Name PowerShell | Get-Member
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
```

Beachten Sie, dass mehr Eigenschaften aufgelistet werden, als standardmäßig angezeigt würden. Eine Reihe der angezeigten Standardeigenschaften wird nicht als Eigenschaften angezeigt, wenn die Ergebnisse von `Get-Member` angezeigt werden. Dies liegt daran, dass viele der angezeigten Werte, z. B. `NPM(K)`, `PM(K)`, `WS(K)` und `CPU(s)` berechnete Eigenschaften sind. Um die tatsächlichen Eigenschaftsnamen zu bestimmen, muss der Befehl per Pipeline an `Get-Member` weitergeleitet werden.

Wenn ein Befehl keine Ausgabe erzeugt, kann er nicht per Pipeline an `Get-Member` weitergeleitet werden. Da `Start-Service` standardmäßig keine Ausgabe erzeugt, wird ein Fehler generiert, wenn Sie versuchen, ihn per Pipeline an `Get-Member` weiterzuleiten.

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

Der Parameter **PassThru** kann mit dem Cmdlet `Start-Service` angegeben werden, damit eine Ausgabe erzeugt wird, die dann ohne einen Fehler per Pipeline an `Get-Member` weitergeleitet wird.

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

Damit ein Befehl per Pipeline an `Get-Member` weitergeleitet werden kann, muss er eine objektbasierte Ausgabe erzeugen.

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

`Out-Host` schreibt direkt in den PowerShell-Host, aber es erzeugt keine objektbasierte Ausgabe für die Pipeline. Somit kann es nicht per Pipeline an `Get-Member` weitergeleitet werden.

## <a name="active-directory"></a>Active Directory

> [!NOTE]
> Die im Abschnitt „Anforderungen“ dieses Kapitels aufgeführten Remoteserver-Verwaltungstools, sind erforderlich, um diesen Abschnitt abzuschließen. Außerdem, wie in der Einführung dieses Buchs erwähnt, muss Ihr Computer in der Windows 10-Laborumgebung Mitglied der Domäne der Laborumgebung sein.

Verwenden Sie `Get-Command` mit dem Parameter **Module**, um zu bestimmen, welche Befehle als Teil des ActiveDirectory PowerShell-Moduls bei der Installation der Remoteserver-Verwaltungstools hinzugefügt wurden.

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

Insgesamt wurden 147 Befehle als Teil des ActiveDirectory PowerShell-Moduls hinzugefügt. Einige von diesen Befehlen geben standardmäßig nur einen Teil der verfügbaren Eigenschaften zurück.

Haben Sie einen Unterschied bei den Namen der Befehle in diesem Modul bemerkt? Der Nomen-Teil der Befehle besitzt ein AD-Präfix. Dies finden Sie häufig bei den Befehlen der meisten Module. Das Präfix dient der Vermeidung von Benennungskonflikten.

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

Selbst wenn Sie nur entfernt mit Active Directory vertraut sind, wissen Sie wahrscheinlich, dass ein Benutzerkonto über mehr Eigenschaften verfügt, als in diesem Beispiel gezeigt werden.

Das Cmdlet `Get-ADUser` verfügt über einen Parameter **Properties**, der verwendet wird, um die zusätzlichen (nicht standardmäßigen) Eigenschaften anzugeben, die Sie zurückgegeben haben möchten. Wenn Sie das Platzhalterzeichen `*` angeben, werden alle zurückgegeben.

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

Jetzt sieht es schon eher so aus.

Können Sie sich einen Grund vorstellen, warum die Eigenschaften eines Active Directory-Benutzerkontos standardmäßig so eingeschränkt sein sollten? Stellen Sie sich vor, wenn Sie jede Eigenschaft für jedes Benutzerkonto in Ihrer Active Directory-Produktionsumgebung zurückgäben. Stellen Sie sich die Leistungsbeeinträchtigung vor, die Sie verursachen könnten, nicht nur bei den Domänencontrollern selbst, sondern auch in Ihrem Netzwerk. Es ist außerdem zweifelhaft, ob Sie tatsächlich jede Eigenschaft benötigen. Das Zurückgeben aller Eigenschaften für ein einzelnes Benutzerkonto ist absolut akzeptabel, wenn Sie feststellen möchten, welche Eigenschaften vorhanden sind.

Es ist nicht ungewöhnlich, einen Befehl bei der Prototypenerstellung mehrmals auszuführen. Wenn Sie eine sehr große Abfrage ausführen möchten, fragen Sie sie einmal ab, und speichern Sie die Ergebnisse in einer Variablen. Arbeiten Sie dann mit dem Inhalt der Variablen, anstatt wiederholt eine aufwändige Abfrage zu verwenden.

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

Verwenden Sie den Inhalt der Variablen `$Users`, anstatt den vorherigen Befehl mehrmals auszuführen.
Denken Sie daran, dass der Inhalt der Variablen nicht aktualisiert wird, wenn Änderungen an diesem Benutzer in Active Directory vorgenommen werden.

Sie könnten die Variable `$Users` per Pipeline an `Get-Member` weiterleiten, um die verfügbaren Eigenschaften zu ermitteln.

```powershell
$Users | Get-Member
```

Wählen Sie dann die einzelnen Eigenschaften aus, indem Sie `$Users` per Pipeline an `Select-Object` weiterleiten, ohne dabei Active Directory jemals mehr als einmal abfragen zu müssen.

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

Wenn Sie Active Directory mehr als einmal Abfragen möchten, verwenden Sie den Parameter **Properties**, um alle nicht standardmäßigen Eigenschaften anzugeben, die Sie verwenden möchten.

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie erfahren, wie Sie bestimmen, welchen Objekttyp ein Befehl erzeugt, wie Sie bestimmen, welche Eigenschaften und Methoden für einen Befehl verfügbar sind, und wie Sie mit Befehlen arbeiten, die die Eigenschaften begrenzen, die standardmäßig zurückgegeben werden.

## <a name="review"></a>Überprüfung

1. Welchen Objekttyp erzeugt das Cmdlet `Get-Process`?
1. Wie bestimmen Sie die für einen Befehl verfügbaren Eigenschaften?
1. Wenn es einen Befehl für das Abrufen, nicht aber für das Festlegen derselben Sache gibt, auf was sollten Sie überprüfen?
1. Wie können Sie dafür sorgen, dass bestimmte Befehle, die standardmäßig keine Ausgabe erzeugen, eine Ausgabe erzeugen?
1. Wenn Sie mit den Ergebnissen eines Befehls arbeiten möchten, der eine sehr große Menge an Ausgaben erzeugt, welche Aktion sollten Sie in Erwägung ziehen?

## <a name="recommended-reading"></a>Empfohlene Lektüre

- [Get-Member][]
- [Anzeigen einer Objektstruktur (Get-Member)][]
- [about_Objects][]
- [about_Properties][]
- [about_Methods][]
- [Kein PowerShell-Cmdlet zum Starten oder Beenden einer Aktion? Vergessen Sie nicht, auf Methoden des „Get-Cmdlets“ zu überprüfen][use-methods].

<!-- link references -->
[RSAT für Windows]: https://support.microsoft.com/help/2693643
[Windows-Verwaltungsmodule]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[Anzeigen einer Objektstruktur (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
