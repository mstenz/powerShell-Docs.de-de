---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: keithb
title: "Installieren und Konfigurieren von WMF 5.1"
ms.openlocfilehash: f58676de6f7a5c51ba586a8c607097af8e60d0c9
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2018
---
# <a name="install-and-configure-wmf-51"></a>Installieren und Konfigurieren von WMF 5.1 #


## <a name="download-and-install-the-wmf-51-package"></a>Herunterladen und Installieren des WMF 5.1-Pakets

Laden Sie das WMF 5.1-Paket für das Betriebssystem und die Architektur herunter, in der es installiert werden soll:

| Betriebssystem       | Voraussetzungen           | Paketlinks                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Installieren von WMF 5.1 für Windows Server 2008 R2 und Windows 7

> **Hinweis:** Die Installationsanweisungen für Windows Server 2008 R2 und Windows 7 wurden geändert und unterscheiden sich von den Anweisungen für die anderen Pakete. Die Installationsanweisungen für Windows Server 2012 R2, Windows Server 2012 und Windows 8.1 sind unten aufgeführt.

**Installieren von WMF 5.1 unter Windows Server 2008 R2 und Windows 7**

1. Wechseln Sie zum Ordner, in den Sie die ZIP-Datei heruntergeladen haben.

2. Klicken Sie mit der rechten Maustaste auf die ZIP-Datei, und wählen Sie „Alle extrahieren“ aus. Die ZIP-Datei enthält 2 Dateien: eine MSU und die Skriptdatei „Install-WMF5.1.PS1“.
Nachdem Sie die ZIP-Datei entpackt haben, können Sie den Inhalt auf einen beliebigen Computer unter Windows 7 oder Windows Server 2008 R2 kopieren.

3. Nachdem Sie den Inhalt der ZIP-Datei extrahiert haben, öffnen Sie PowerShell als Administrator, und navigieren Sie zu dem Ordner, der den Inhalt der ZIP-Datei enthält.

4. Führen Sie das Skript „Install-Wmf5.1.ps1“ in diesem Ordner aus, und folgen Sie den Anweisungen. Dieses Skript überprüft, ob der lokale Computer die Voraussetzungen erfüllt, und installiert dann WMF 5.1. Die Voraussetzungen sind unten aufgeführt.

„Install-WMF5.1.ps1“ verfügt über die folgenden Parameter, die das Automatisieren der Installation unter Windows Server 2008 R2 und Windows 7 erleichtern:

- „AcceptEula“: Wenn dieser Parameter verwendet wird, wird der Endbenutzer-Lizenzvertrag automatisch akzeptiert und nicht angezeigt.
- „AllowRestart“: Dieser Parameter kann nur verwendet werden, wenn „AcceptEula“ ebenfalls angegeben wird. Wird dieser Parameter angegeben und ist nach der Installation von WMF 5.1 ein Neustart erforderlich, erfolgt dieser Neustart nach Abschluss der Installation sofort und ohne Nachfrage.

**WMF 5.1-Voraussetzungen für Windows Server 2008 R2 SP1 und Windows 7 SP1**

Für die Installation von WMF 5.1 unter Windows Server 2008 R2 SP1 oder Windows 7 SP1 müssen folgende Voraussetzungen erfüllt sein:
- Das neueste Service Pack installiert sein.
- WMF 3.0 **darf nicht** installiert sein. Wird WMF 5.1 über WMF 3.0 installiert, führt dies zum Verlust des PSModulePath, wodurch es zu Fehlern in anderen Anwendungen kommen kann. Vor der Installation von WMF 5.1 müssen Sie WMF 3.0 entweder deinstallieren oder den PSModulePath speichern und nach Abschluss der Installation von WMF 5.1 manuell wiederherstellen.
- WMF 5.1 erfordert mindestens [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).
Befolgen Sie die Anweisungen auf der Downloadseite, um Microsoft .NET Framework 4.5.2 zu installieren.

**WinRM-Abhängigkeit**

Windows PowerShell DSC (Desired State Configuration) hängt von WinRM ab.
Unter Windows Server 2008 R2 und Windows 7 ist WinRM nicht standardmäßig aktiviert.
Führen Sie zum Aktivieren von WinRM in einer Windows PowerShell-Sitzung mit erhöhten Benutzerrechten `Set-WSManQuickConfig` aus.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Installieren von WMF 5.1 für Windows Server 2012 R2, Windows Server 2012 und Windows 8.1
**Installation über den Windows-Explorer (bzw. Datei-Explorer in Windows Server 2012 R2 oder Windows 8.1)**

1. Wechseln Sie zum Ordner, in den Sie die MSU-Datei heruntergeladen haben.
2. Doppelklicken Sie auf die MSU-Datei, um sie auszuführen.

**Installation über die Eingabeaufforderung**

1. Öffnen Sie nach dem Herunterladen des richtigen Pakets für die Architektur Ihres Computers ein Eingabeaufforderungsfenster mit erhöhten Benutzerrechten (Als Administrator ausführen). Bei den Server Core-Installationsoptionen von Windows Server 2012 R2, Windows Server 2012 oder Windows Server 2008 R2 SP1 wird das Eingabeaufforderungsfenster standardmäßig mit erhöhten Benutzerrechten geöffnet.
2. Wechseln Sie zum Ordner, in den Sie das Installationspaket für WMF 5.1 heruntergeladen oder kopiert haben.
3. Führen Sie einen der folgenden Befehle aus:
   - Führen Sie auf Computern mit Windows Server 2012 R2 oder Windows 8.1 x64 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet` aus.
   - Führen Sie auf Computern mit Windows Server 2012 `W2K12-KB3191565-x64.msu /quiet` aus.
   - Führen Sie auf Computern mit Windows Server 8.1 x86 `Win8.1-KB3191564-x86.msu /quiet` aus.

> [!NOTE]
> Für die Installation von WMF 5.1 ist ein Neustart erforderlich. Wenn Sie die Option `/quiet` verwenden, wird das System ohne vorherige Ankündigung neu gestartet.
> Wählen Sie die Option `/norestart` aus, wenn kein Neustart ausgeführt werden soll. WMF 5.1 wird jedoch erst installiert, wenn Sie einen Neustart durchgeführt haben.