---
title: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
description: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78279136"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen

Wenn Sie mit der ISE vertraut sind, wissen Sie sicher, dass Sie `psedit file.ps1` über die integrierte Konsole ausführen konnten, um Dateien – lokal oder remote – direkt in der ISE zu öffnen.

Dieses Feature ist auch in der PowerShell-Erweiterung für VSCode verfügbar. In diesem Leitfaden erfahren Sie, wie Sie dabei vorgehen.

## <a name="prerequisites"></a>Voraussetzungen

Dieses Handbuch setzt Folgendes voraus:

- Eine Remoteressource (z.B. eine VM oder einen Container), auf die Sie Zugriff haben
- Ausführung von PowerShell auf dieser Ressource und dem Hostcomputer
- VSCode und PowerShell-Erweiterung für VSCode

Dieses Feature funktioniert unter Windows PowerShell und PowerShell Core.

Dieses Feature funktioniert auch beim Herstellen der Verbindung mit einem Remotecomputer über WinRM, PowerShell Direct oder SSH. Wenn Sie SSH verwenden möchten, aber Windows verwenden, informieren Sie sich über die [Win32-Version von SSH](https://github.com/PowerShell/Win32-OpenSSH)!

> [!IMPORTANT]
> Die Befehle `Open-EditorFile` und `psedit` funktionieren nur in der **integrierten PowerShell-Konsole**, die von der PowerShell-Erweiterung für VSCode erstellt wird.

## <a name="usage-examples"></a>Anwendungsbeispiele

Diese Beispiele veranschaulichen das Remotebearbeiten und -debuggen von einem MacBook Pro aus auf einer in Azure ausgeführten Ubuntu-VM. Der Prozess läuft unter Windows identisch ab.

### <a name="local-file-editing-with-open-editorfile"></a>Lokale Dateibearbeitung mit Open-EditorFile

Nach Starten der PowerShell-Erweiterung für VSCode und Öffnen der integrierten PowerShell-Konsole können wir `Open-EditorFile foo.ps1` oder `psedit foo.ps1` eingeben, um die lokale Datei „foo.ps1“ direkt im Editor zu öffnen.

![Bearbeitung von „foo.ps1“ in Open-EditorFile funktioniert lokal](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> Die Datei `foo.ps1` muss bereits vorhanden sein.

Von dort aus können wir:

- Fügen Sie Haltepunkte zum Bundsteg hinzu.

  ![Hinzufügen von Haltepunkten zum Bundsteg](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Drücken Sie F5, um das PowerShell-Skript zu debuggen.

  ![Debuggen des lokalen PowerShell-Skripts](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Sie können während des Debuggens mit der Debugging-Konsole interagieren, im Bereich auf der linken Seite die Variablen überprüfen und alle anderen standardmäßigen Debuggingtools verwenden.

### <a name="remote-file-editing-with-open-editorfile"></a>Remotedateibearbeitung mit Open-EditorFile

Jetzt wenden wir uns Remotedateibearbeitung und -debuggen zu. Die Schritte sind nahezu identisch, wir müssen nur zuerst eines tun: unsere PowerShell-Sitzung auf dem Remoteserver starten.

Hierfür gibt es ein Cmdlet. Es heißt `Enter-PSSession`.

Die vereinfachte Erläuterung des Cmdlets ist:

- `Enter-PSSession -ComputerName foo` startet eine-Sitzung über WinRM
- `Enter-PSSession -ContainerId foo` und `Enter-PSSession -VmId foo` starten eine Sitzung über PowerShell Direct
- `Enter-PSSession -HostName foo` startet eine-Sitzung über SSH

Weitere Informationen finden Sie in der Dokumentation zu [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Da wir von macOS aus auf eine Ubuntu-VM in Azure zugreifen, verwenden wir SSH für das Remoting.

Führen Sie zunächst in der integrierten Konsole `Enter-PSSession` aus. Sie sind mit der Remotesitzung verbunden, wenn links neben Ihrer Eingabeaufforderung `[<hostname>]` angezeigt wird.

![Der Aufruf von Enter-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Jetzt können wir dieselben Schritte ausführen wie beim Bearbeiten eines lokalen Skripts.

1. Führen Sie `Open-EditorFile test.ps1` oder `psedit test.ps1` aus, um die Remotedatei `test.ps1` zu öffnen.

  ![Datei „Open-EditorFile the test.ps1“](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Bearbeiten Sie die Datei bzw. / legen Sie Haltepunkte fest.

   ![Bearbeiten und Festlegen von Haltepunkten](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Beginnen Sie mit dem Debuggen (F5) der Remotedatei.

   ![Debuggen der Remotedatei](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Zur Lösung eventuell noch auftretender Probleme steht Ihnen das [GitHub-Repository](https://github.com/powershell/vscode-powershell) zur Verfügung.
