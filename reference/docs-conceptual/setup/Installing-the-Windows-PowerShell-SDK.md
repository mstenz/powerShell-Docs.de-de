---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Installieren das Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893537"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installieren das Windows PowerShell SDK

Das folgende Thema beschreibt, wie das PowerShell SDK in verschiedenen Versionen von Windows installiert wird.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installieren des Windows PowerShell 3.0 SDK für Windows 8 und Windows Server 2012

Windows PowerShell 3.0 wird automatisch mit Windows 8 und Windows Server 2012 installiert.
Darüber hinaus können Sie die Verweisassemblys für Windows PowerShell 3.0 als Teil des Windows 8 SDKs herunterladen und installieren.
Diese Assemblys ermöglichen Ihnen das Schreiben von Cmdlets, Anbietern und Host-Programmen für Windows PowerShell 3.0.
Wenn Sie das Windows SDK für Windows 8 installieren, werden die Windows PowerShell-Assemblys automatisch im Referenzassemblyordner unter `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0` installiert.
Weitere Informationen finden Sie auf der [Windows 8 SDK-Downloadwebsite](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).
Codebeispiele für Windows PowerShell stehen ebenfalls im Dev Center zur Verfügung.
Weitere Informationen finden Sie auf der Seite mit Desktop-Codebeispielen auf der [Dev Center-Website](https://code.msdn.microsoft.com:443/windowsdesktop/).

Darüber hinaus ist Windows PowerShell 3.0 abwärtskompatibel mit dem Windows PowerShell 2.0 SDK, das eine Reihe von Codebeispielen enthält.
Weitere Informationen zum Herunterladen des Windows PowerShell 2.0 SDKs finden Sie nachstehend.
(Beachten Sie, dass, während die 2.0-Codebeispiele mit Windows 8 und Windows PowerShell 3.0 kompatibel sind, Sie Windows PowerShell 2.0 auf einer Windows 8-Plattform nicht installieren können.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installieren des Windows PowerShell 3.0 SDK für Windows 7 und Windows Server 2008 R2

Bei Windows 7 und Windows Server 2008 R2 wird PowerShell 2.0 automatisch installiert.
Darüber hinaus können Sie PowerShell 3.0 auf diesen Systemen installieren.
(Weitere Informationen finden Sie unter [Installieren von Windows PowerShell](Installing-Windows-PowerShell.md).)
Wie oben beschrieben, können Sie das Windows 8 SDK auch unter Windows 7 und Windows Server 2008 R2 installieren.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installieren des Windows PowerShell 2.0 SDK für Windows 7, Vista, XP, Server 2003 und Server 2008

Das Windows PowerShell 2.0 SDK stellt die Verweisassemblys bereit, die zum Schreiben von Cmdlets, Anbietern und Hostinganwendungen erforderlich sind, und bietet C#-Beispielcode, der als Ausgangspunkt dienen kann, wenn Sie mit dem Schreiben von Code beginnen.

Informationen zur Installation dieses SDK finden Sie unter [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).

## <a name="reference-assemblies"></a>Verweisassemblys

Verweisassemblys werden standardmäßig an folgendem Speicherort installiert: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE] 
> Code, der für die Windows PowerShell 2.0-Assemblys kompiliert wird, kann nicht in Windows PowerShell 1.0-Installationen geladen werden.
> Jedoch kann Code, der für die Windows PowerShell 1.0-Assemblys kompiliert wird, in Windows PowerShell 2.0-Installationen geladen werden.

## <a name="samples"></a>Beispiele

Codebeispiele werden standardmäßig an folgendem Speicherort installiert: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Die folgenden Abschnitte enthalten eine kurze Beschreibung der einzelnen Beispiele.

## <a name="cmdlet-samples"></a>Cmdlet-Beispiele

### <a name="getprocesssample01"></a>GetProcessSample01

Zeigt, wie Sie ein einfaches Cmdlet schreiben, das alle Prozesse auf dem lokalen Computer abruft.

### <a name="getprocesssample02"></a>GetProcessSample02

Zeigt, wie dem Cmdlet Parameter hinzugefügt werden.
Das Cmdlet akzeptiert einen oder mehrere Prozessnamen und gibt die entsprechenden Prozesse zurück.

### <a name="getprocesssample03"></a>GetProcessSample03

Zeigt, wie Sie Parameter hinzufügen, die Eingaben aus der Pipeline akzeptieren.

### <a name="getprocesssample04"></a>GetProcessSample04

Zeigt, wie Fehler ohne Abbruch behandelt werden.

### <a name="getprocesssample05"></a>GetProcessSample05

Zeigt, wie eine Liste der angegebenen Prozesse angezeigt wird.

### <a name="selectobject"></a>SelectObject

Zeigt das Schreiben eines Filters, um nur bestimmte Objekte auszuwählen.

### <a name="selectstring"></a>SelectString

Zeigt, wie Dateien nach angegebenen Mustern durchsucht werden.

### <a name="stopprocesssample01"></a>StopProcessSample01

Zeigt das Implementieren eines *PassThru*-Parameters und das Anfordern von Benutzerfeedback durch Aufrufe der Methoden [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) und [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).
Benutzer geben den Parameter *PassThru* an, wenn sie erzwingen möchten, dass das Cmdlet ein Objekt zurückgibt.

### <a name="stopprocesssample02"></a>StopProcessSample02

Zeigt, wie ein bestimmter Prozess beendet wird.

### <a name="stopprocesssample03"></a>StopProcessSample03

Zeigt, wie Aliase für Parameter deklariert und Platzhalter unterstützt werden.

### <a name="stopprocesssample04"></a>StopProcessSample04

Zeigt die Deklaration von Parametersätzen, das Objekt, das vom Cmdlet als Eingabe akzeptiert wird, und die Angabe des zu verwendenden Standardparametersatzes.

## <a name="remoting-samples"></a>Remotingbeispiele

### <a name="remoterunspace01"></a>RemoteRunspace01

Zeigt, wie Sie einen Remoterunspace erstellen, der zum Herstellen einer Remoteverbindung verwendet wird.

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

Zeigt, wie Sie einen Remoterunspace-Pool erstellen und anhand dieses Pools mehrere Befehle gleichzeitig ausführen.

### <a name="serialization01"></a>Serialization01

Zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Informationen von ausgewählten öffentlichen Eigenschaften dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden.

### <a name="serialization02"></a>Serialization02

Zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Informationen von Instanzen aus dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden, wenn die Informationen nicht in öffentlichen Eigenschaften dieser Klasse verfügbar sind.

### <a name="serialization03"></a>Serialization03

Zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Instanzen dieser Klasse und von abgeleiteten Klassen in aktive .NET-Objekte deserialisiert (aktiviert) werden.

## <a name="event-samples"></a>Ereignisbeispiele

### <a name="event01"></a>Event01

Zeigt, wie Sie ein Cmdlet für die Ereignisregistrierung durch Ableiten von ObjectEventRegistrationBase erstellen.

### <a name="event02"></a>Event02

Zeigt, wie Sie Benachrichtigungen von Windows PowerShell-Ereignissen empfangen, die auf Remotecomputern generiert werden.
Verwendet das über die [Runspace](/dotnet/api/system.management.automation.runspaces.runspace)-Klasse offen gelegte PSEventReceived-Ereignis.

## <a name="hosting-application-samples"></a>Hosten von Anwendungsbeispielen

### <a name="runspace01"></a>Runspace01

Zeigt, wie Sie die [PowerShell](/dotnet/api/system.management.automation.powershell)-Klasse zum synchronen Ausführen des Cmdlets [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) verwenden.
Das Cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) gibt [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx)-Objekte für jeden Prozess zurück, der auf dem lokalen Computer ausgeführt wird.

### <a name="runspace02"></a>Runspace02

Zeigt, wie Sie die [PowerShell](/dotnet/api/system.management.automation.powershell)-Klasse zum synchronen Ausführen der Cmdlets [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) und [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) verwenden.
Das Cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) gibt [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx)-Objekte für jeden Prozess zurück, der auf dem lokalen Computer ausgeführt wird, und das Cmdlet `Sort-Object` sortiert die Objekte basierend auf ihrer [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx)-Eigenschaft.
Die Ergebnisse dieser Befehle werden anhand des Steuerelements [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) angezeigt.

### <a name="runspace03"></a>Runspace03

Zeigt, wie Sie die [PowerShell](/dotnet/api/system.management.automation.powershell)-Klasse zum synchronen Ausführen eines Skripts verwenden und wie Sie Fehler ohne Abbruch behandeln.
Das Skript empfängt eine Liste von Prozessnamen und ruft diese Prozesse anschließend ab.
Die Ergebnisse des Skripts, einschließlich Fehler ohne Abbruch, die beim Ausführen des Skripts generiert wurden, werden in einem Konsolenfenster angezeigt.

### <a name="runspace04"></a>Runspace04

Zeigt, wie die [PowerShell](/dotnet/api/system.management.automation.powershell)-Klasse zum Ausführen von Befehlen verwendet wird und wie Fehler mit Abbruch abgefangen werden, die beim Ausführen der Befehle ausgelöst werden.
Zwei Befehle werden ausgeführt. An den letzten Befehl wird ein ungültiges Parameterargument übergeben.
Daher werden keine Objekte zurückgegeben, und ein Fehler mit Abbruch wird ausgelöst.

### <a name="runspace05"></a>Runspace05

Zeigt, wie Sie einem [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate)-Objekt ein Snap-In hinzufügen, sodass das Cmdlet des Snap-Ins bei Öffnen des Runspace verfügbar ist.
Das Snap-In stellt ein Get-Proc-Cmdlet bereit (definiert durch das [GetProcessSample01-Beispiel](https://technet.microsoft.com/library/ff602028.aspx)), das synchron mithilfe eines [PowerShell](/dotnet/api/system.management.automation.powershell)-Objekts ausgeführt wird.

### <a name="runspace06"></a>Runspace06

Zeigt, wie Sie einem [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate)-Objekt ein Modul hinzufügen, sodass das Modul beim Öffnen des Runspace geladen wird.
Das Modul stellt ein Get-Proc-Cmdlet bereit (definiert durch das [GetProcessSample02-Beispiel](https://technet.microsoft.com/library/ff602027.aspx)), das synchron mithilfe eines [PowerShell](/dotnet/api/system.management.automation.powershell)-Objekts ausgeführt wird.

### <a name="runspace07"></a>Runspace07

Zeigt, wie Sie einen Runspace erstellen und dann diesen Runspace zum synchronen Ausführen von zwei Cmdlets anhand eines [PowerShell](/dotnet/api/system.management.automation.powershell)-Objekts verwenden.

### <a name="runspace08"></a>Runspace08

Zeigt, wie Sie der Pipeline eines [PowerShell](/dotnet/api/system.management.automation.powershell)-Objekts Befehle und Argumente hinzufügen und die Befehle synchron ausführen.

### <a name="runspace09"></a>Runspace09

Zeigt, wie Sie der Pipeline eines [PowerShell](/dotnet/api/system.management.automation.powershell)-Objekts ein Skript hinzufügen und das Skript asynchron ausführen.
Ereignisse werden verwendet, um die Ausgabe des Skripts zu verarbeiten.

### <a name="runspace10"></a>Runspace10

Zeigt, wie Sie einen anfänglichen Standardsitzungsstatus erstellen, dem [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) ein Cmdlet hinzufügen, einen Runspace erstellen, der den anfänglichen Sitzungsstatus verwendet, und wie Sie den Befehl anhand eines [PowerShell](/dotnet/api/system.management.automation.powershell)-Objekts ausführen.

### <a name="runspace11"></a>Runspace11

Zeigt, wie Sie mithilfe der [ProxyCommand](/dotnet/api/system.management.automation.proxycommand)-Klasse einen Proxybefehl erstellen, der ein vorhandenes Cmdlet aufruft, aber den Satz der verfügbaren Parameter einschränkt.
Der Proxybefehl wird anschließend zu einem anfänglichen Sitzungsstatus hinzugefügt, der dazu verwendet wird, einen eingeschränkten Runspace zu erstellen.
Dies bedeutet, dass der Benutzer nur über den Proxybefehl auf die Funktionalität des Cmdlets zugreifen kann.

### <a name="powershell01"></a>PowerShell01

Zeigt, wie Sie über ein [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate)-Objekt einen eingeschränkten Runspace erstellen.

### <a name="powershell02"></a>PowerShell02

Zeigt, wie Sie einen Runspacepool verwenden, um mehrere Befehle gleichzeitig auszuführen.

## <a name="host-samples"></a>Hostbeispiele

### <a name="host01"></a>Host01

Zeigt, wie eine Hostanwendung implementiert wird, die einen benutzerdefinierten Host verwendet.
In diesem Beispiel wird ein Runspace erstellt, der den benutzerdefinierten Host verwendet. Anschließend wird die [PowerShell](/dotnet/api/system.management.automation.powershell)-API zum Ausführen eines Skripts verwendet, das „exit“ aufruft.
Die Hostanwendung untersucht anschließend die Ausgabe des Skripts und gibt die Ergebnisse aus.

### <a name="host02"></a>Host02

Zeigt, wie Sie eine Hostanwendung schreiben, die die Windows PowerShell-Laufzeit zusammen mit einer benutzerdefinierten Hostimplementierung verwendet.
Die Hostanwendung legt die Hostkultur auf Deutsch fest, führt das Cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) aus und zeigt die Ergebnisse so an, wie sie über „pwrsh.exe“ dargestellt würden, und gibt dann das aktuelle Datum und die Uhrzeit auf Deutsch aus.

### <a name="host03"></a>Host03

Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.

### <a name="host04"></a>Host04

Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.
Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.

### <a name="host05"></a>Host05

Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.
Diese Anwendung unterstützt auch Aufrufe von Remotecomputern mithilfe der Cmdlets [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) und [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession).

### <a name="host06"></a>Host06

Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.
Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.

## <a name="provider-samples"></a>Anbieterbeispiele

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Zeigt, wie Sie eine Anbieterklasse deklarieren, die direkt von der [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider)-Klasse abgeleitet wird.
Wird hier nur aus Gründen der Vollständigkeit aufgeführt.

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Zeigt, wie Sie die Methoden [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) und [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) überschreiben, um Aufrufe an die Cmdlets `New-PSDrive` und `Remove-PSDrive` zu unterstützen.
Die Anbieterklasse in diesem Beispiel wird von der [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider)-Klasse abgeleitet.

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Zeigt, wie Sie die Methoden [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) und [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) überschreiben, um Aufrufe an die Cmdlets `Get-Item` und `Set-Item` zu unterstützen.
Die Anbieterklasse in diesem Beispiel wird von der [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider)-Klasse abgeleitet.

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Zeigt, wie Sie Containermethoden überschreiben, um Aufrufe an die Cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item` und `Remove-Item` zu unterstützen.
Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind.
Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element.
Die Anbieterklasse in diesem Beispiel wird von der [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider)-Klasse abgeleitet.

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Zeigt, wie Sie Containermethoden überschreiben, um Aufrufe an die Cmdlets `Move-Item` und `Join-Path` zu unterstützen.
Diese Methoden sollten implementiert werden, wenn der Benutzer Elemente innerhalb eines Containers verschieben muss, und wenn der Datenspeicher geschachtelte Container enthält.
Die Anbieterklasse in diesem Beispiel wird von der [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider)-Klasse abgeleitet.

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Zeigt, wie Sie Inhaltsmethoden überschreiben, um Aufrufe an die Cmdlets `Clear-Content`, `Get-Content` und `Set-Content` zu unterstützen.
Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss.
Die Anbieterklasse in diesem Beispiel wird von der [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider)-Klasse abgeleitet und implementiert die [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider)-Schnittstelle.