---
title: Installieren das Windows PowerShell SDK
ms.date: 03/30/2020
ms.topic: article
ms.openlocfilehash: b47dddaf167024d30a7a31596f96569f976109d7
ms.sourcegitcommit: bf71c8c5e2a4fc7d5c3a67a537db1285089d03a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80394987"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installieren das Windows PowerShell SDK

Gilt für: Windows PowerShell 2,0, Windows PowerShell 3,0

Das folgende Thema beschreibt, wie das PowerShell SDK in verschiedenen Versionen von Windows installiert wird.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installieren des Windows PowerShell 3.0 SDK für Windows 8 und Windows Server 2012

Windows PowerShell 3.0 wird automatisch mit Windows 8 und Windows Server 2012 installiert. Darüber hinaus können Sie die Verweisassemblys für Windows PowerShell 3.0 als Teil des Windows 8 SDKs herunterladen und installieren. Diese Assemblys ermöglichen Ihnen das Schreiben von Cmdlets, Anbietern und Host-Programmen für Windows PowerShell 3.0. Wenn Sie das Windows SDK für Windows 8 installieren, werden die Windows PowerShell-Assemblys automatisch im Referenzassemblyordner unter `\Program Files
(x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0` installiert. Weitere Informationen finden Sie auf der Windows 8 SDK-Download Website. Windows PowerShell-Codebeispiele sind auch im Repository " [PowerShell-SDK-Samples](https://github.com/MicrosoftDocs/powershell-sdk-samples/tree/master/SDK-3.0) " verfügbar.

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installieren des Windows PowerShell 3.0 SDK für Windows 7 und Windows Server 2008 R2

Bei Windows 7 und Windows Server 2008 R2 wird PowerShell 2.0 automatisch installiert. Darüber hinaus können Sie PowerShell 3.0 auf diesen Systemen installieren. Sie können das Windows 8 SDK auch unter Windows 7 und Windows Server 2008 R2 installieren, wie oben beschrieben.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installieren des Windows PowerShell 2.0 SDK für Windows 7, Vista, XP, Server 2003 und Server 2008

Das Windows PowerShell 2.0 SDK stellt die Verweisassemblys bereit, die zum Schreiben von Cmdlets, Anbietern und Hostinganwendungen erforderlich sind, und bietet C#-Beispielcode, der als Ausgangspunkt dienen kann, wenn Sie mit dem Schreiben von Code beginnen. Sie können die Codebeispiele aus [https://www.microsoft.com/download/details.aspx?id=2560](https://www.microsoft.com/download/details.aspx?id=2560)herunterladen.

### <a name="reference-assemblies"></a>Verweisassemblys

Verweisassemblys werden standardmäßig an folgendem Speicherort installiert: `c:\Program Files\Reference
Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE]
> Code, der für die Windows PowerShell 2.0-Assemblys kompiliert wird, kann nicht in Windows PowerShell 1.0-Installationen geladen werden. Jedoch kann Code, der für die Windows PowerShell 1.0-Assemblys kompiliert wird, in Windows PowerShell 2.0-Installationen geladen werden.

### <a name="samples"></a>Beispiele

Codebeispiele werden standardmäßig an folgendem Speicherort installiert: `C:\Program Files\Microsoft
SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`. Die folgenden Abschnitte enthalten eine kurze Beschreibung der einzelnen Beispiele.

#### <a name="cmdlet-samples"></a>Cmdlet-Beispiele

- GetProcessSample01: zeigt, wie ein einfaches Cmdlet geschrieben wird, das alle Prozesse auf dem lokalen Computer abruft.
- GetProcessSample02-zeigt, wie Parameter zum Cmdlet hinzugefügt werden. Das Cmdlet akzeptiert einen oder mehrere Prozessnamen und gibt die entsprechenden Prozesse zurück.
- GetProcessSample03: zeigt, wie Parameter hinzugefügt werden, die Eingaben aus der Pipeline akzeptieren.
- GetProcessSample04: zeigt, wie Fehler ohne Abbruch behandelt werden.
- GetProcessSample05-zeigt, wie eine Liste der angegebenen Prozesse angezeigt wird.
- SelectObject: zeigt, wie ein Filter geschrieben wird, um nur bestimmte Objekte auszuwählen.
- SelectString: zeigt, wie Dateien nach angegebenen Mustern durchsucht werden.
- StopProcessSample01: zeigt, wie ein PassThru-Parameter implementiert wird und wie Benutzer Feedback durch Aufrufe der Methode "tiondprocess" und "tiondcontinue" angefordert wird. Benutzer geben den passthru-Parameter an, wenn Sie erzwingen möchten, dass das Cmdlet ein Objekt zurückgibt.
- StopProcessSample02: zeigt, wie ein bestimmter Prozess beendet wird.
- StopProcessSample03-zeigt, wie Aliase für Parameter deklariert und Platzhalter unterstützt werden.
- StopProcessSample04-zeigt, wie Parametersätze, das-Objekt, das vom Cmdlet als Eingabe verwendet wird, deklariert werden und wie der zu verwendende Standardparameter Satz angegeben wird.

#### <a name="remoting-samples"></a>Remotingbeispiele

- RemoteRunspace01: zeigt, wie Sie einen Remoterunspace erstellen, der zum Herstellen einer Remote Verbindung verwendet wird.
- RemoteRunspacePool01: zeigt, wie Sie einen Remote-Runspace-Pool erstellen und mehrere Befehle gleichzeitig mit diesem Pool ausführen.
- Serialization01: zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Informationen aus ausgewählten öffentlichen Eigenschaften dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden.
- Serialization02: zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Informationen aus der Instanz dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden, wenn die Informationen in öffentlichen Eigenschaften der-Klasse nicht verfügbar sind.
- Serialization03: zeigt, wie Sie eine vorhandene .NET-Klasse anzeigen und sicherstellen, dass Instanzen dieser Klasse und abgeleiteter Klassen in aktive .NET-Objekte deserialisiert (aktiviert) werden.

#### <a name="event-samples"></a>Ereignisbeispiele

- Event01-zeigt, wie Sie ein Cmdlet für die Ereignis Registrierung durch Ableiten von objecteventregistrationbase erstellen.
- Event02: zeigt, wie Sie Benachrichtigungen von Windows PowerShell-Ereignissen erhalten, die auf Remote Computern generiert werden. Er verwendet das pereigempfangene Ereignis, das durch die Runspace-Klasse verfügbar gemacht wird.

#### <a name="hosting-application-samples"></a>Hosten von Anwendungsbeispielen

- Runspace01: zeigt, wie die PowerShell-Klasse verwendet wird, um das `Get-Process`-Cmdlet synchron auszuführen.
  Das `Get-Process`-Cmdlet gibt Prozess Objekte für jeden Prozess zurück, der auf dem lokalen Computer ausgeführt wird.
- Runspace02: zeigt, wie die PowerShell-Klasse zum synchronen Ausführen der `Get-Process` und `Sort-Object` Cmdlets verwendet wird. Das `Get-Process`-Cmdlet gibt Prozess Objekte für jeden Prozess zurück, der auf dem lokalen Computer ausgeführt wird, und der `Sort-Object` sortiert die Objekte basierend auf Ihrer ID-Eigenschaft. Die Ergebnisse dieser Befehle werden mithilfe eines DataGridView-Steuer Elements angezeigt.
- Runspace03: zeigt, wie die PowerShell-Klasse zum synchronen Ausführen eines Skripts verwendet wird und wie Fehler ohne Abbruch behandelt werden. Das Skript empfängt eine Liste von Prozessnamen und ruft diese Prozesse anschließend ab. Die Ergebnisse des Skripts, einschließlich Fehler ohne Abbruch, die beim Ausführen des Skripts generiert wurden, werden in einem Konsolenfenster angezeigt.
- Runspace04: zeigt, wie die PowerShell-Klasse zum Ausführen von Befehlen verwendet wird, und wie abschließende Fehler abgefangen werden, die beim Ausführen der Befehle ausgelöst werden. Zwei Befehle werden ausgeführt. An den letzten Befehl wird ein ungültiges Parameterargument übergeben. Daher werden keine Objekte zurückgegeben, und ein Fehler mit Abbruch wird ausgelöst.
- Runspace05: zeigt, wie einem initialsessionstate-Objekt ein Snap-in hinzugefügt wird, sodass das Cmdlet des Snap-Ins verfügbar ist, wenn der Runspace geöffnet wird. Das Snap-in stellt ein Get-proc-Cmdlet bereit (definiert durch das GetProcessSample01-Beispiel), das synchron mithilfe eines PowerShell-Objekts ausgeführt wird.
- Runspace06: zeigt, wie ein Modul einem initialsessionstate-Objekt hinzugefügt wird, damit das Modul geladen wird, wenn der Runspace geöffnet wird. Das Modul stellt ein Get-proc-Cmdlet bereit (definiert durch das GetProcessSample02-Beispiel), das synchron mithilfe eines PowerShell-Objekts ausgeführt wird.
- Runspace07: zeigt, wie ein Runspace erstellt wird, und verwendet dann diesen Runspace, um zwei Cmdlets mithilfe eines PowerShell-Objekts synchron auszuführen.
- Runspace08: zeigt, wie Sie der Pipeline eines PowerShell-Objekts Befehle und Argumente hinzufügen und wie die Befehle synchron ausgeführt werden.
- Runspace09: zeigt, wie ein Skript zur Pipeline eines PowerShell-Objekts hinzugefügt wird und wie das Skript asynchron ausgeführt wird. Ereignisse werden verwendet, um die Ausgabe des Skripts zu verarbeiten.
- Runspace10: zeigt, wie ein ursprünglicher Standard Sitzungszustand erstellt wird, wie ein Cmdlet zu initialsessionstate hinzugefügt wird, wie ein Runspace erstellt wird, der den anfänglichen Sitzungs Status verwendet, und wie der Befehl mithilfe eines PowerShell-Objekts ausgeführt wird.
- Runspace11-zeigt, wie Sie mit der ProxyCommand-Klasse einen Proxy Befehl erstellen, der ein vorhandenes Cmdlet aufruft, aber den Satz verfügbarer Parameter einschränkt. Der Proxybefehl wird anschließend zu einem anfänglichen Sitzungsstatus hinzugefügt, der dazu verwendet wird, einen eingeschränkten Runspace zu erstellen. Dies bedeutet, dass der Benutzer nur über den Proxybefehl auf die Funktionalität des Cmdlets zugreifen kann.
- PowerShell01-zeigt, wie ein eingeschränkter Runspace mit einem initialsessionstate-Objekt erstellt wird.
- PowerShell02: zeigt, wie ein Runspace-Pool verwendet wird, um mehrere Befehle gleichzeitig auszuführen.

#### <a name="host-samples"></a>Hostbeispiele

- Host01: zeigt, wie eine Host Anwendung implementiert wird, die einen benutzerdefinierten Host verwendet. In diesem Beispiel wird ein Runspace erstellt, der den benutzerdefinierten Host verwendet, und dann wird die PowerShell-API zum Ausführen eines Skripts verwendet, das `exit`aufruft. Die Hostanwendung untersucht anschließend die Ausgabe des Skripts und gibt die Ergebnisse aus.
- Host02: zeigt, wie eine Host Anwendung geschrieben wird, die die Windows PowerShell-Laufzeit zusammen mit einer benutzerdefinierten Host Implementierung verwendet. Die Host Anwendung legt die Host Kultur auf Deutsch fest, führt das `Get-Process`-Cmdlet aus und zeigt die Ergebnisse an, wie Sie Sie mithilfe von "pwrsh. exe" sehen würden. Anschließend werden die aktuellen Daten und die aktuelle Zeit in Deutsch ausgegeben.
- Host03: zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.
- Host04: zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.
- Host05: zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Diese Host Anwendung unterstützt auch Aufrufe von Remote Computern mithilfe der Cmdlets `Enter-PsSession` und `Exit-PsSession`.
- Host06: zeigt, wie eine interaktive konsolenbasierte Host Anwendung erstellt wird, die Befehle in der Befehlszeile liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.

#### <a name="provider-samples"></a>Anbieterbeispiele

- AccessDBProviderSample01-zeigt, wie Sie eine Anbieter Klasse deklarieren, die direkt von der cmdletprovider-Klasse abgeleitet wird. Wird hier nur aus Gründen der Vollständigkeit aufgeführt.

- AccessDBProviderSample02: zeigt, wie die newdrive-Methode und die removedrive-Methode überschrieben werden, um Aufrufe des `New-PSDrive` und `Remove-PSDrive`-Cmdlets zu unterstützen. Die Anbieter Klasse in diesem Beispiel wird von der drivecmdletprovider-Klasse abgeleitet.

- AccessDBProviderSample03: zeigt, wie Sie die GetItem-Methode und die-Methode für das Festlegen von Methoden überschreiben, um Aufrufe der Cmdlets `Get-Item` und `Set-Item` zu unterstützen Die Anbieter Klasse in diesem Beispiel wird von der itemcmdletprovider-Klasse abgeleitet.

- AccessDBProviderSample04-zeigt, wie Sie Container Methoden überschreiben, um Aufrufe der Cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item`und `Remove-Item` zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Die Anbieter Klasse in diesem Beispiel wird von der itemcmdletprovider-Klasse abgeleitet.

- AccessDBProviderSample05: zeigt, wie Sie Container Methoden überschreiben, um Aufrufe an die `Move-Item`-und `Join-Path`-Cmdlets zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Benutzer Elemente innerhalb eines Containers verschieben muss, und wenn der Datenspeicher geschachtelte Container enthält. Die Anbieter Klasse in diesem Beispiel wird von der navigationcmdletprovider-Klasse abgeleitet.

- AccessDBProviderSample06: zeigt, wie Inhalts Methoden überschrieben werden, um Aufrufe an die `Clear-Content`-, `Get-Content`-und `Set-Content`-Cmdlets zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss. Die Anbieter Klasse in diesem Beispiel wird von der navigationcmdletprovider-Klasse abgeleitet und implementiert die icontentcmdletprovider-Schnittstelle.
