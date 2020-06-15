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
# <a name="chapter-4---one-liners-and-the-pipeline"></a>Kapitel 4: Einzeiler und die Pipeline

Als ich mich zum ersten Mal mit PowerShell beschäftigt habe, habe ich, wenn ich eine Aufgabe nicht mit einem PowerShell-Einzeiler ausführen konnte, auf die grafische Benutzeroberfläche (GUI) zurückgegriffen. Im Laufe der Zeit habe ich meine Kenntnisse auf das Schreiben von Skripts, Funktionen und Modulen erweitert. Lassen Sie sich von einigen der umfangreicheren Beispiele, die Sie möglicherweise im Internet sehen, nicht abschrecken. Niemand kommt als PowerShell-Experte auf die Welt. Jeder von uns hat einmal angefangen.

Ich möchten denjenigen, die immer noch die grafische Benutzeroberfläche (GUI) für Verwaltungszwecke verwenden, ein paar Ratschläge anbieten: Installieren Sie die Verwaltungstools auf ihrer Administrator-Arbeitsstation, und verwalten Sie Ihre Server remote. Auf diese Weise ist es unerheblich, ob auf dem Server eine GUI- oder Server Core-Installation des Betriebssystems ausgeführt wird.
Dies wird Ihnen dabei helfen, sich auf die Remoteverwaltung von Servern mit PowerShell vorzubereiten.

Stellen Sie wie in vorherigen Kapiteln sicher, dass Sie die Abläufe auf Ihrem Windows 10-Laborumgebungscomputer durchlaufen und nachvollziehen.

## <a name="one-liners"></a>Einzeiler

Ein PowerShell-Einzeiler ist eine kontinuierliche Pipeline, nicht notwendigerweise ein Befehl, der in einer physischen Zeile steht. Nicht alle Befehle, die in einer physischen Zeile stehen, sind Einzeiler.

Obwohl sich der folgende Befehl auf mehrere physische Zeilen verteilt, handelt es sich um einen PowerShell-Einzeiler, weil er eine kontinuierliche Pipeline ist. Er könnte in einer physischen Zeile geschrieben werden, aber ich habe mich entschieden, die Zeilen am Pipe-Symbol zu umbrechen. Das Pipe-Symbol ist eins der Zeichen, bei denen ein natürlicher Zeilenumbruch in PowerShell zulässig ist.

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

Natürliche Zeilenumbrüche können bei häufig verwendeten Zeichen auftreten, einschließlich Komma (`,`) sowie öffnenden eckigen (`[`), geschweiften (`{`) und runden Klammern (`(`). Andere Zeichen, die nicht so häufig vorkommen, umfassen das Semikolon (`;`), das Gleichheitszeichen (`=`) sowie öffnende einfache als auch doppelte Anführungszeichen (`'`, `"`).

Die Verwendung des Graviszeichens (`` ` ``) als Zeilenfortsetzungszeichen ist ein umstrittenes Thema. Ich empfehle Ihnen, die Verwendung dieses Zeichens vollständig zu vermeiden, falls möglich. Ich sehe häufig PowerShell-Befehle, die ein Graviszeichen direkt hinter einem natürlichen Zeilenumbruchzeichen verwenden.
Dafür gibt es keinen Grund.

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

Die in den vorherigen zwei Beispielen gezeigten Befehle funktionieren in der PowerShell-Konsole einwandfrei. Wenn Sie aber versuchen, sie im Konsolenbereich der PowerShell ISE auszuführen, wird ein Fehler generiert. Der Konsolenbereich der PowerShell ISE wartet nicht, bis der restliche Befehl in der nächsten Zeile eingegeben wird, wie es die PowerShell-Konsole macht. Um dieses Problem im Konsolenbereich der PowerShell ISE zu vermeiden, verwenden Sie <kbd>Umschalt</kbd>+<kbd>EINGABE</kbd>, anstatt nur die <kbd>EINGABETASTE</kbd> zu drücken, wenn Sie einen Befehl in einer anderen Zeile fortsetzen möchten.

Das nächste Beispiel ist kein PowerShell-Einzeiler, weil es sich nicht um eine kontinuierliche Pipeline handelt. Es handelt sich um zwei getrennte Befehle in einer Zeile, die durch ein Semikolon getrennt sind.

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Viele Programmier- und Skriptsprachen erfordern am Ende jeder Zeile ein Semikolon. Zwar können Sie dies so auch in PowerShell handhaben, doch wird dies nicht empfohlen, da es unnötig ist.

## <a name="filtering-left"></a>Links filtern

Die Ergebnisse der in diesem Kapitel gezeigten Befehle wurden zu einer Teilmenge gefiltert. Beispielsweise wurde `Get-Service` mit dem Parameter **Name** verwendet, um die Liste der zurückgegebenen Dienste auf nur den Windows-Zeitdienst zu filtern.

In der Pipeline sollten Sie die Ergebnisse immer so früh wie möglich auf das Gesuchte filtern. Dies erfolgt mithilfe von Parametern beim ersten Befehl oder dem am weitesten links stehenden.
Dies wird manchmal auch als _Links filtern_ bezeichnet.

Im folgenden Beispiel wird der Parameter **Name** von `Get-Service` verwendet, um die Ergebnisse sofort nur auf den Windows-Zeitdienst zu filtern.

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

Es ist nicht ungewöhnlich, dass in Beispielen der Befehl per Pipeline an `Where-Object` weitergeleitet wird, um die Filterung durchzuführen.

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

Im ersten Beispiel wird an der Quelle gefiltert, und es werden nur die Ergebnisse für den Windows-Zeitdienst zurückgegeben.
Im zweiten Beispiel werden alle Dienste zurückgegeben, die dann per Pipeline an einen anderen Befehl weitergeleitet werden, um die Filterung durchzuführen. Dies mag in diesem Beispiel nicht wie ein großer Unterschied aussehen, doch stellen Sie sich vor, dass Sie eine Liste von Active Directory-Benutzern abfragen. Möchten Sie wirklich die Informationen für viele Tausende von Benutzerkonten aus Active Directory zurückgeben, nur um diese per Pipeline an einen anderen Befehl weiterzuleiten, der sie dann zu einer kleinen Teilmenge filtert? Meine Empfehlung ist, immer links zu filtern, auch wenn dies bedeutungslos zu sein scheint. Sie gewöhnen sich dies so an, dass Sie später automatisch links filtern, wenn es wirklich darauf ankommt.

Mit hat mal jemand gesagt, dass die Reihenfolge, in der Sie die Befehle angeben, keine Rolle spielt. Das entspricht jedoch in keiner Weise den Tatsachen. Die Reihenfolge, in der die Befehle angegeben werden, ist allerdings von Bedeutung, nämlich beim Filtern. Nehmen Sie beispielsweise ein Szenario an, in dem Sie `Select-Object` verwenden, um nur ein paar Eigenschaften auszuwählen, und `Where-Object` verwenden, um nach Eigenschaften zu filtern, die nicht in der Auswahl sein sollen. In diesem Szenario muss die Filterung zuerst erfolgen, da die Eigenschaft andernfalls nicht in der Pipeline vorhanden sein wird, wenn Sie versuchen, die Filterung durchzuführen.

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

Der Befehl im vorherigen Beispiel gibt keine Ergebnisse zurück, weil die Eigenschaft **CanStopAndContinue-** nicht vorhanden ist, wenn die Ergebnisse von `Select-Object` per Pipeline an `Where-Object` weitergeleitet werden. Diese spezifische Eigenschaft wurde nicht „ausgewählt“. Im Wesentlichen wurde sie herausgefiltert. Wenn Sie die Reihenfolge von `Select-Object` und `Where-Object` umkehren, erzeugt dies die gewünschten Ergebnisse.

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

## <a name="the-pipeline"></a>Die Pipeline

Wie Sie in vielen der bisher gezeigten Beispiele in diesem Buch gesehen haben, kann die Ausgabe eines Befehls oft als Eingabe für einen anderen Befehl verwendet werden. In Kapitel 3 wurde `Get-Member` verwendet, um zu bestimmen, welcher Objekttyp von einem Befehl erzeugt wird. In Kapitel 3 wird auch die Verwendung des Parameters **ParameterType** von `Get-Command` gezeigt, um zu bestimmen, welche Befehle diesen Typ von Eingabe akzeptieren, obwohl dies nicht notwendigerweise durch eine Pipelineeingabe erfolgt sein muss.

Abhängig davon, wie gründlich die Hilfe eines Befehls ist, kann sie einen Abschnitt **INPUTS** (Eingaben) und **OUTPUTS** (Ausgaben) enthalten.

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

In den vorherigen Ergebnissen wird nur der relevante Abschnitt angezeigt. Wie Sie sehen können, wird im Abschnitt **INPUTS** angegeben, dass ein **ServiceController**- oder ein **String**-Objekt per Pipeline an das Cmdlet `Stop-Service` weitergeleitet werden kann. Sie erfahren nicht, welche Parameter diese Art von Eingabe akzeptieren. Eine der einfachsten Methoden, um diese Information zu ermitteln, besteht darin, die verschiedenen Parameter in der vollständigen Version der Hilfe für das Cmdlet `Stop-Service` durchzusehen.

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

Noch einmal: Ich habe hier nur den relevanten Teil der Hilfe im vorherigen Resultset angezeigt. Beachten Sie Folgendes: Der Parameter **DisplayName** akzeptiert keine Pipelineeingabe, der Parameter **InputObject** akzeptiert Pipelineeingaben **als Wert** für **ServiceController**-Objekte, und der Parameter **Name** akzeptiert Pipelineeingaben **als Wert** für **String**-Objekte. Er akzeptiert auch Pipelineeingaben **als Eigenschaftsname**.

Wenn ein Parameter Pipelineeingaben sowohl als Eigenschaftsnamen als auch als Wert akzeptiert, wird immer zuerst **als Wert** ausprobiert. Schlägt **als Wert** fehl, wird **als Eigenschaftsname** versucht. **Als Wert** ist ein wenig irreführend. Ich ziehe es vor, hier von **als Typ** zu sprechen. Dies bedeutet, dass, wenn Sie die Ergebnisse eines Befehls, der einen **ServiceController**-Objekttyp erzeugt, per Pipeline an `Stop-Service` weiterleiten, diese Eingabe an den Parameter **InputObject** gebunden wird. Wenn Sie aber die Ergebnisse eines Befehls, der eine **String**-Ausgabe erzeugt, per Pipeline an `Stop-Service` weiterleiten, werden diese an den Parameter **Name** gebunden. Wenn Sie die Ergebnisse eines Befehls, der weder ein **ServiceController**- noch ein **String**-Objekt erzeugt, per Pipeline an `Stop-Service` weiterleiten, dieser aber eine Ausgabe erzeugt, die eine Eigenschaft namens **Name** enthält, wird die Eigenschaft **Name** der Ausgabe an den Parameter **Name** von `Stop-Service` gebunden.

Bestimmen Sie, welchen Typ von Ausgabe der Befehl `Get-Service` erzeugt.

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

`Get-Service` erzeugt einen ServiceController-Objekttyp.

Wie zuvor in der Hilfe gesehen, akzeptiert der Parameter **InputObject** von `Stop-Service` **ServiceController**-Objekte über die Pipeline **als Wert** (als Typ). Dies bedeutet Folgendes: Wenn die Ergebnisse des Cmdlets`Get-Service` per Pipeline an `Stop-Service` weitergeleitet werden, werden sie an den Parameter **InputObject** von `Stop-Service` gebunden.

```powershell
Get-Service -Name w32time | Stop-Service
```

Nun probieren wir String-Eingaben aus. Leiten Sie `w32time` per Pipeline an `Get-Member` weiter, lediglich um zu bestätigen, dass es eine Zeichenfolge (string) ist.

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

Wie zuvor in der Hilfe gezeigt, wird eine Zeichenfolge durch ihre Weiterleitung per Pipeline an `Stop-Service` **als Wert** an den Parameter **Name** von `Stop-Service` gebunden. Testen Sie dies, indem Sie `w32time` per Pipeline an `Stop-Service` weiterleiten.

```powershell
'w32time' | Stop-Service
```

Beachten Sie, dass ich im vorherigen Beispiel einfache Anführungszeichen um die Zeichenfolge `w32time` verwendet habe. In PowerShell sollten Sie immer einfache Anführungszeichen anstelle von doppelten Anführungszeichen verwenden, es sei denn, der Inhalt der Zeichenfolge in Anführungszeichen enthält eine Variable, die auf ihren tatsächlichen Wert erweitert werden muss. Wenn Sie einfache Anführungszeichen verwenden, muss PowerShell den in den Anführungszeichen stehenden Inhalt nicht analysieren, weshalb Ihr Code etwas schneller ausgeführt wird.

Erstellen Sie ein benutzerdefiniertes Objekt, um die Pipelineeingabe als Eigenschaftsname für den Parameter **Name** von `Stop-Service` zu testen.

```powershell
$CustomObject = [pscustomobject]@{
>> Name = 'w32time'
>> }
```

Der Inhalt der Variablen **CustomObject** ist ein **PSCustomObject**-Objekttyp, der eine Eigenschaft namens **Name** enthält.

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

Wenn Sie die Variable `$CustomObject` in Anführungszeichen setzen müssten, sollten Sie doppelte Anführungszeichen verwenden.
Andernfalls wird bei Verwendung von einfachen Anführungszeichen die wörtliche (literale) Zeichenfolge `$CustomObject` anstelle des in der Variablen enthaltenen Werts per Pipeline an `Get-Member` weitergeleitet.

Obwohl der Inhalt von `$CustomObject` durch seine Weiterleitung per Pipeline an das Cmdlet `Stop-Service` an den Parameter **Name** gebunden wird, wird er diesmal **als Eigenschaftsname** gebunden anstatt **als Wert**, da der Inhalt von `$CustomObject` ein Objekt mit einer Eigenschaft namens **Name** ist.

In diesem Beispiel erstelle ich ein anderes benutzerdefiniertes Objekt mit einem anderen Eigenschaftsnamen, z. B. **Service**.

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

Ein Fehler wird generiert, wenn versucht wird, `$CustomObject` per Pipeline an `Stop-Service` weiterzuleiten, da der Befehl kein **ServiceController**- oder **String**-Objekt erzeugt und keine Eigenschaft namens **Name** besitzt.

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

Wenn die Ausgabe eines Befehls nicht mit den Pipelineeingabeoptionen für einen anderen Befehl übereinstimmt, kann `Select-Object` verwendet werden, um die Eigenschaft so umzubenennen, dass die Eigenschaften ordnungsgemäß übereinstimmen.

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

In diesem Beispiel wurde `Select-Object` verwendet, um die Eigenschaft **Service** in eine Eigenschaft namens **Name** umzubenennen.

Die Syntax in diesem Beispiel mag zuerst etwas kompliziert erscheinen. Ich habe allerdings die Erfahrung gemacht, dass Sie die Syntax niemals erlernen werden, indem Sie Code kopieren und einfügen. Nehmen Sie sich die Zeit, den Code einzugeben. Wenn Sie dies ein paar Mal gemacht haben, wird es Ihnen zur zweiten Natur. Mehrere Monitore zu haben, ist ein großer Vorteil, da Sie den Beispielcode auf dem einem Bildschirm anzeigen und ihn auf einem anderen Bildschirm eingeben können.

Gelegentlich kann es vorkommen, dass Sie einen Parameter verwenden möchten, der keine Pipelineeingabe akzeptiert. Das folgende Beispiel veranschaulicht die Verwendung der Ausgabe eines Befehls als Eingabe für einen anderen. Speichern Sie zuerst die Anzeigenamen einiger Windows-Dienste in einer Textdatei.

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

Sie können den Befehl ausführen, der die erforderliche Ausgabe in Klammern als Wert für den Parameter des Befehls bereitstellt, der die Eingabe erfordert.

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

Für diejenigen, die sich noch daran erinnern können, wie dies funktioniert: Dies entspricht letztendlich der Reihenfolge von Operationen in der Algebra. Der Befehl in Klammern wird immer vor dem äußeren Teil des Befehls ausgeführt.

## <a name="powershellget"></a>PowerShellGet

„PowerShellGet“ ist ein PowerShell-Modul, das Befehle zum Ermitteln, Installieren, Veröffentlichen und Aktualisieren von PowerShell-Modulen (und anderen Artefakten) in bzw. aus einem NuGet-Repository enthält. „PowerShellGet“ ist im Lieferumfang von PowerShell, Version 5.0 und höher, enthalten. Es steht als getrennter Download für PowerShell, Version 3.0 und höher, zur Verfügung.

Microsoft hostet ein NuGet-Onlinerepository mit dem Namen "[PowerShell Gallery][]. Obwohl dieses Repository von Microsoft gehostet wird, wurde der Großteil der im Repository enthaltenen Module nicht von Microsoft geschrieben. Jeder Code, der aus dem PowerShell-Katalog abgerufen wird, sollte in einer isolierten Testumgebung gründlich überprüft werden, bevor er als für die Verwendung in einer Produktionsumgebung geeignet erachtet wird.

Die meisten Unternehmen wollen wahrscheinlich ihr eigenes, internes, privates NuGet-Repository hosten, in dem sie ihre für den internen Gebrauch gedachten Module sowie aus anderen Quellen heruntergeladene Module bereitstellen können, nachdem diese als nicht böswillig validiert wurden.

Verwenden Sie das Cmdlet `Find-Module`, das Bestandteil des PowerShellGet-Moduls ist, um ein von mir geschriebenes Modul namens „MrToolkit“ im PowerShell-Katalog zu suchen.

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

Wenn Sie zum ersten Mal einen der Befehle aus dem PowerShellGet-Modul verwenden, werden Sie aufgefordert, den NuGet-Anbieter zu installieren.

Um das MrToolkit-Modul zu installieren, leiten Sie den vorherigen Befehl per Pipeline an `Install-Module` weiter.

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

Da es sich beim PowerShell-Katalog um ein nicht vertrauenswürdiges Repository handelt, werden Sie aufgefordert, die Installation des Moduls zu genehmigen.

## <a name="finding-pipeline-input-the-easy-way"></a>Pipelineeingaben suchen leicht gemacht

Das MrToolkit-Modul enthält eine Funktion namens `Get-MrPipelineInput`. Dieses Cmdlet kann verwendet werden, um auf einfache Weise festzustellen, welche Parameter eines Befehls Pipelineeingaben akzeptieren, welchen Objekttyp sie akzeptieren und ob sie Pipelineeingaben **als Wert** oder **als Eigenschaftsname** akzeptieren.

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

Wie Sie sehen, lassen sich dieselben Informationen, die wir zuvor mittels Durchsehen der Hilfe ermittelt haben, mit dieser Funktion problemlos bestimmen.

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie PowerShell-Einzeiler kennen gelernt. Sie haben erfahren, dass die Anzahl physischer Zeilen, in denen ein Befehl steht, nicht ausschlaggebend dafür ist, ob es sich um einen PowerShell-Einzeiler handelt oder nicht. Außerdem haben Sie „links Filtern“, die Pipeline und PowerShellGet kennen gelernt.

## <a name="review"></a>Überprüfung

1. Was ist ein PowerShell-Einzeiler?
1. Nennen Sie ein paar Zeichen, bei denen ein natürlicher Zeilenumbruch in PowerShell auftreten kann.
1. Warum sollten Sie links filtern?
1. Was sind die zwei Arten, auf die ein PowerShell-Befehl Pipelineeingaben akzeptieren kann?
1. Warum sollten Sie die im PowerShell-Katalog gefundenen Befehlen nicht als vertrauenswürdig einstufen?

## <a name="recommended-reading"></a>Empfohlene Lektüre

- [about_Pipelines][]
- [about_Command_Syntax][]
- [about_Parameters][]
- [PowerShellGet: Die SUPER EINFACHE Methode zum Ermitteln, Installieren und Aktualisieren von PowerShell-Modulen][psget]

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell Gallery]: https://www.powershellgallery.com/
