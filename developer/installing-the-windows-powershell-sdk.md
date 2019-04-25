---
title: Installieren das Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082480"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installieren das Windows PowerShell SDK

Gilt für: Windows PowerShell 2.0, Windows PowerShell 3.0

Das folgende Thema beschreibt, wie das PowerShell SDK in verschiedenen Versionen von Windows installiert wird.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installieren des Windows PowerShell 3.0 SDK für Windows 8 und Windows Server 2012

Windows PowerShell 3.0 wird automatisch mit Windows 8 und Windows Server 2012 installiert. Darüber hinaus können Sie die Verweisassemblys für Windows PowerShell 3.0 als Teil des Windows 8 SDKs herunterladen und installieren. Diese Assemblys ermöglichen Ihnen das Schreiben von Cmdlets, Anbietern und Host-Programmen für Windows PowerShell 3.0. Wenn Sie das Windows SDK für Windows 8 installieren, werden die Windows PowerShell-Assemblys im Ordner „Verweisassembly“ unter „\Programme (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0“ automatisch installiert. Weitere Informationen finden Sie in das Windows 8 SDK-Website herunterladen. Codebeispiele für Windows PowerShell stehen ebenfalls im Dev Center zur Verfügung.
Weitere Informationen finden Sie unter der Beispielseite Desktop-Codebeispielen auf der Dev Center-Website.

Darüber hinaus ist Windows PowerShell 3.0 abwärtskompatibel mit dem Windows PowerShell 2.0 SDK, das eine Reihe von Codebeispielen enthält. Weitere Informationen zum Herunterladen des Windows PowerShell 2.0 SDKs finden Sie nachstehend. (Beachten Sie, dass, während die 2.0-Codebeispiele mit Windows 8 und Windows PowerShell 3.0 kompatibel sind, Sie Windows PowerShell 2.0 auf einer Windows 8-Plattform nicht installieren können.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installieren des Windows PowerShell 3.0 SDK für Windows 7 und Windows Server 2008 R2

Bei Windows 7 und Windows Server 2008 R2 wird PowerShell 2.0 automatisch installiert. Darüber hinaus können Sie PowerShell 3.0 auf diesen Systemen installieren. (Weitere Informationen finden Sie unter Installieren von Windows PowerShell.). Wie oben beschrieben, können Sie das Windows 8 SDK auch unter Windows 7 und Windows Server 2008 R2 installieren.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installieren des Windows PowerShell 2.0 SDK für Windows 7, Vista, XP, Server 2003 und Server 2008

Das Windows PowerShell 2.0 SDK stellt die Verweisassemblys bereit, die zum Schreiben von Cmdlets, Anbietern und Hostinganwendungen erforderlich sind, und bietet C#-Beispielcode, der als Ausgangspunkt dienen kann, wenn Sie mit dem Schreiben von Code beginnen.

Um dieses SDK zu installieren, finden Sie in Windows PowerShell 2.0 SDK.

### <a name="reference-assemblies"></a>Verweisassemblys

Verweisassemblys werden standardmäßig an folgendem Speicherort installiert: c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> Code, der für die Windows PowerShell 2.0-Assemblys kompiliert wird, kann nicht in Windows PowerShell 1.0-Installationen geladen werden. Jedoch kann Code, der für die Windows PowerShell 1.0-Assemblys kompiliert wird, in Windows PowerShell 2.0-Installationen geladen werden.


### <a name="samples"></a>Beispiele

Codebeispiele werden standardmäßig an folgendem Speicherort installiert: C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. Die folgenden Abschnitte enthalten eine kurze Beschreibung der einzelnen Beispiele.

#### <a name="cmdlet-samples"></a>Cmdlet-Beispiele

- GetProcessSample01 - veranschaulicht, wie ein einfaches Cmdlet schreiben, das alle Prozesse auf dem lokalen Computer abruft.
- GetProcessSample02 - zeigt, wie das Cmdlet Parameter hinzugefügt wird. Das Cmdlet akzeptiert einen oder mehrere Prozessnamen und gibt die entsprechenden Prozesse zurück.
- GetProcessSample03 - zeigt, wie Sie Parameter hinzufügen, die Eingaben aus der Pipeline akzeptieren.
- GetProcessSample04 - wird gezeigt, wie Fehler ohne Abbruch behandelt werden.
- GetProcessSample05 - zeigt, wie Sie eine Liste aller angegebenen Prozesse anzuzeigen.
- SelectObject - veranschaulicht, wie schreiben Sie einen Filter, um nur bestimmte Objekte auszuwählen.
- SelectString - zeigt, wie Dateien nach angegebenen Mustern gesucht wird.
- StopProcessSample01 - wird zum Implementieren eines PassThru-Parameters, und das Anfordern von Benutzerfeedback durch Aufrufe der ShouldProcess- und "shouldcontinue"-Methode gezeigt. Benutzer geben den PassThru-Parameter, erzwingen das Cmdlet ein Objekt zurückgegeben werden soll,
- StopProcessSample02 - veranschaulicht, wie ein bestimmter Prozess beendet wird.
- StopProcessSample03 - zeigt, wie Sie Aliase für Parameter deklariert und Platzhalter unterstützt.
- StopProcessSample04 - zeigt die Deklaration der Parametersätze, die das Objekt, das als Eingabe, und geben Sie den Standard-Parametersatz verwenden wie das Cmdlet verwendet.

#### <a name="remoting-samples"></a>Remotingbeispiele

- RemoteRunspace01 - zeigt, wie Sie einen Remoterunspace erstellen, der zum Herstellen einer Remoteverbindung verwendet wird.
- RemoteRunspacePool01 - zeigt, wie Sie einen Remoterunspace-Pool zu erstellen und wie Sie mehrere Befehle gleichzeitig ausgeführt werden, mithilfe von diesem Pool.
- Serialization01 - zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und stellen Sie sicher, dass Informationen von ausgewählten öffentlichen Eigenschaften dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden.
- Serialization02 - zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und stellen Sie sicher, dass Informationen von Instanz dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden, wenn die Informationen nicht in öffentlichen Eigenschaften der Klasse verfügbar ist.
- Serialization03 - zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und stellen Sie sicher, dass Instanzen dieser Klasse und von abgeleiteten Klassen (aktiviert), in aktive .NET-Objekte deserialisiert werden.

#### <a name="event-samples"></a>Ereignisbeispiele

- Event01 - veranschaulicht, wie ein Cmdlet für die ereignisregistrierung durch Ableiten von ObjectEventRegistrationBase erstellen.
- Event02 - zeigt, wie zum wird gezeigt, wie zum Empfangen von Benachrichtigungen von Windows PowerShell-Ereignissen, die auf Remotecomputern generiert werden. Er verwendet das offen gelegte PSEventReceived-Ereignis, das über die Runspace-Klasse verfügbar gemacht werden.

#### <a name="hosting-application-samples"></a>Hosten von Anwendungsbeispielen

- Runspace01 - zeigt, wie Sie die PowerShell-Klasse verwenden, führen Sie die `Get-Process` Cmdlet synchron.
Die `Get-Process` Cmdlet gibt zurück, Verarbeiten von Objekten für jeden Prozess auf dem lokalen Computer ausgeführt wird.
- Runspace02 - zeigt, wie Sie die PowerShell-Klasse verwenden, führen Sie die `Get-Process` und `Sort-Object` Cmdlets synchron. Die `Get-Process` Cmdlet gibt zurück, Verarbeiten von Objekten für jeden Prozess auf dem lokalen Computer ausgeführt wird und die `Sort-Object` sortiert die Objekte basierend auf ihrer Id-Eigenschaft. Die Ergebnisse dieser Befehle wird angezeigt, mit einem DataGridView-Steuerelement.
- Runspace03 - zeigt, wie Sie die PowerShell-Klasse, um ein Skript synchron auszuführen, und wie Fehler ohne Abbruch behandelt. Das Skript empfängt eine Liste von Prozessnamen und ruft diese Prozesse anschließend ab. Die Ergebnisse des Skripts, einschließlich Fehler ohne Abbruch, die beim Ausführen des Skripts generiert wurden, werden in einem Konsolenfenster angezeigt.
- Runspace04 – zu erfahren, wie Sie die PowerShell-Klasse, die zum Ausführen von Befehlen verwenden, und zum Abfangen von Fehlern, die beim Ausführen der Befehle ausgelöst werden beendet. Zwei Befehle werden ausgeführt. An den letzten Befehl wird ein ungültiges Parameterargument übergeben. Daher werden keine Objekte zurückgegeben, und ein Fehler mit Abbruch wird ausgelöst.
- Runspace05 - veranschaulicht, wie ein Snap-in ein InitialSessionState Objekt hinzufügen, damit das Cmdlet aus, der das Snap-in verfügbar ist, wenn der Runspace geöffnet wird. Das Snap-in bietet eine Get-Proc-Cmdlet (definiert durch die GetProcessSample01-Beispiel), das synchron mithilfe eines PowerShell-Objekts ausgeführt wird.
- Runspace06 - veranschaulicht, wie ein Modul ein InitialSessionState Objekt hinzufügen, damit das Modul geladen wird, wenn der Runspace geöffnet wird. Das Modul bietet eine Get-Proc-Cmdlet (definiert durch die GetProcessSample02-Beispiel), das synchron mithilfe eines PowerShell-Objekts ausgeführt wird.
- Runspace07 - veranschaulicht einen Runspace erstellen und verwenden Sie dann diesen Runspace zum synchronen zwei Cmdlets ausführen, unter Verwendung eines PowerShell-Objekts.
- Runspace08 - zeigt, wie Sie Befehle und Argumente an die Pipeline eine PowerShell-Objekts hinzufügen und wie Sie die Befehle synchron ausführen.
- Runspace09 - zeigt, wie Sie die Pipeline eine PowerShell-Objekts ein Skript hinzufügen und wie Sie das Skript asynchron ausführen. Ereignisse werden verwendet, um die Ausgabe des Skripts zu verarbeiten.
- Runspace10 - zeigt, wie Sie einen anfänglichen Standardsitzungsstatus erstellen, wie die InitialSessionState ein Cmdlet hinzugefügt, wie Sie einen Runspace erstellen, der den anfänglichen Sitzungsstatus verwendet und wie den Befehl ausgeführt wird, wird mithilfe eines PowerShell-Objekts.
- Runspace11 - veranschaulicht, wie die ProxyCommand-Klasse verwenden, um einen Proxybefehl zu erstellen, der ein vorhandenes Cmdlet aufruft, aber der Satz der verfügbaren Parameter einschränkt. Der Proxybefehl wird anschließend zu einem anfänglichen Sitzungsstatus hinzugefügt, der dazu verwendet wird, einen eingeschränkten Runspace zu erstellen. Dies bedeutet, dass der Benutzer nur über den Proxybefehl auf die Funktionalität des Cmdlets zugreifen kann.
- PowerShell01 - veranschaulicht, wie einen eingeschränkten Runspace mithilfe eines InitialSessionState-Objekts zu erstellen.
- PowerShell02 - zeigt, wie Sie einen runspacepool verwenden, um mehrere Befehle gleichzeitig auszuführen.

#### <a name="host-samples"></a>Hostbeispiele

- Host01 - veranschaulicht, wie eine hostanwendung implementiert wird, die einen benutzerdefinierten Host verwendet, wird. In diesem Beispiel, wenn ein Runspace erstellt wird, die den benutzerdefinierten Host verwendet, und klicken Sie dann wird der PowerShell-API verwendet, um ein Skript ausführen, die Aufrufe von "exit". Die Hostanwendung untersucht anschließend die Ausgabe des Skripts und gibt die Ergebnisse aus.
- Host02 - zeigt, wie eine hostanwendung zu schreiben, die Windows PowerShell-Laufzeit, zusammen mit einer benutzerdefinierten hostimplementierung verwendet, wird. Die hostanwendung legt die auf Deutsch fest, führt die `Get-Process` -Cmdlet und zeigt die Ergebnisse wie sehen sie mit pwrsh.exe, und klicken Sie dann druckt das aktuelle Datum und Uhrzeit auf Deutsch.
- Host03 - zeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle aus und klicken Sie dann die Ergebnisse in der Konsole angezeigt wird.
- Host04 - zeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle aus und klicken Sie dann die Ergebnisse in der Konsole angezeigt wird. Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.
- Host05 - zeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle aus und klicken Sie dann die Ergebnisse in der Konsole angezeigt wird. Diese hostanwendung unterstützt auch Aufrufe an Remotecomputern mithilfe der `Enter-PsSession` und `Exit-PsSession` Cmdlets.
- Host06 - zeigt, wie Sie eine interaktive, konsolenbasierte hostanwendung zu erstellen, die Befehle von der Befehlszeile aus liest, führt die Befehle aus und klicken Sie dann die Ergebnisse in der Konsole angezeigt wird. Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.

#### <a name="provider-samples"></a>Anbieterbeispiele

- AccessDBProviderSample01 - veranschaulicht, wie eine Anbieterklasse deklarieren, die direkt von der CmdletProvider-Klasse abgeleitet ist. Wird hier nur aus Gründen der Vollständigkeit aufgeführt.

- AccessDBProviderSample02 - zeigt, wie die NewDrive und RemoveDrive-Methoden, um Aufrufe unterstützen die `New-PSDrive` und `Remove-PSDrive` Cmdlets. Die Anbieterklasse in diesem Beispiel wird von der DriveCmdletProvider-Klasse abgeleitet.

- AccessDBProviderSample03 - zeigt, wie die GetItem und SetItem-Methoden, um Aufrufe unterstützen die `Get-Item` und `Set-Item` Cmdlets. Die Anbieterklasse in diesem Beispiel wird von der ItemCmdletProvider-Klasse abgeleitet.

- AccessDBProviderSample04 - zeigt, wie containermethoden um Aufrufe unterstützen die `Copy-Item`, `Get-ChildItem`, `New-Item`, und `Remove-Item` Cmdlets. Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Die Anbieterklasse in diesem Beispiel wird von der ItemCmdletProvider-Klasse abgeleitet.

- AccessDBProviderSample05 - zeigt, wie containermethoden um Aufrufe unterstützen die `Move-Item` und `Join-Path` Cmdlets. Diese Methoden sollten implementiert werden, wenn der Benutzer Elemente innerhalb eines Containers verschieben muss, und wenn der Datenspeicher geschachtelte Container enthält. Die Anbieterklasse in diesem Beispiel wird von der NavigationCmdletProvider-Klasse abgeleitet.

- AccessDBProviderSample06 - zeigt, wie inhaltsmethoden um Aufrufe unterstützen die `Clear-Content`, `Get-Content`, und `Set-Content` Cmdlets. Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss. Die Anbieterklasse in diesem Beispiel wird von der NavigationCmdletProvider-Klasse abgeleitet, und die IContentCmdletProvider-Schnittstelle implementiert.
