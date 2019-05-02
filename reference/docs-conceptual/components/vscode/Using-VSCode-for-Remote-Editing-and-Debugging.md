---
title: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
description: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086669"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen

Wenn Sie mit der ISE vertraut waren, erinnern Sie sich vielleicht daran, dass Sie `psedit file.ps1` über die integrierte Konsole ausführen konnten, um Dateien – lokal oder remote – direkt in der ISE zu öffnen.

Dieses Feature ist auch in der PowerShell-Erweiterung für VSCode verfügbar. In diesem Handbuch erfahren Sie, Sie dabei vorgehen.

## <a name="prerequisites"></a>Voraussetzungen

Dieses Handbuch setzt Folgendes voraus:

- eine Remoteressource (z.B. eine VM, einen Container), auf die Sie Zugriff haben
- Ausführung von PowerShell auf dieser Ressource und dem Hostcomputer
- VSCode und PowerShell-Erweiterung für VSCode

Dieses Feature funktioniert unter Windows PowerShell und PowerShell Core.

Dieses Feature funktioniert auch beim Herstellen der Verbindung mit einem Remotecomputer über WinRM, PowerShell Direct oder SSH. Wenn Sie SSH verwenden möchten, aber Windows verwenden, informieren Sie sich über die [Win32-Version von SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Los geht's!

In diesem Abschnitt werden Remotebearbeitung und -debuggen von einem MacBook Pro aus auf einer in Azure ausgeführten Ubuntu-VM demonstriert. Obwohl nicht Windows verwendet wird, **ist der Prozess identisch**.

### <a name="local-file-editing-with-open-editorfile"></a>Lokale Dateibearbeitung mit Open-EditorFile

Nach Starten der PowerShell-Erweiterung für VSCode und Öffnen der integrierten PowerShell-Konsole können wir `Open-EditorFile foo.ps1` oder `psedit foo.ps1` eingeben, um die lokale Datei „foo.ps1“ direkt im Editor zu öffnen.

![Bearbeitung von „foo.ps1“ in Open-EditorFile funktioniert lokal](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> „foo.ps1“ muss bereits vorhanden sein.

Von dort aus können wir:

dem Bundsteg Haltepunkte hinzufügen ![Hinzufügen eines Haltepunkts zum Bundsteg](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

und F5 drücken, um das PowerShell-Skript zu debuggen.
![Debuggen des lokalen PowerShell-Skripts](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Sie können während des Debuggens mit der Debugging-Konsole interagieren, im Bereich auf der linken Seite die Variablen überprüfen und alle anderen standardmäßigen Debuggingtools verwenden.

### <a name="remote-file-editing-with-open-editorfile"></a>Remotedateibearbeitung mit Open-EditorFile

Jetzt wenden wir uns Remotedateibearbeitung und -debuggen zu. Die Schritte sind nahezu identisch, wir müssen nur zuerst eines tun – unsere PowerShell-Sitzung auf dem Remoteserver starten.

Hierfür gibt es ein Cmdlet. Es heißt `Enter-PSSession`.

Die vereinfachte Erläuterung des Cmdlets ist:

- `Enter-PSSession -ComputerName foo` startet eine-Sitzung über WinRM
- `Enter-PSSession -ContainerId foo` und `Enter-PSSession -VmId foo` starten eine Sitzung über PowerShell Direct
- `Enter-PSSession -HostName foo` startet eine-Sitzung über SSH

Weitere Informationen zu `Enter-PSSession` finden Sie [hier](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6) in der Dokumentation.

Ich verwende SSH für das Remoting, da ich von macOS aus auf eine Ubuntu-VM in Azure zugreife.

Zunächst führen wir in der integrierten Konsole Enter-PSSession aus. Sie wissen, dass Sie sich in der Sitzung befinden, weil `[something]` links von Ihrer Eingabeaufforderung angezeigt wird.

![Der Aufruf von Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Von dort aus können wir genau dieselben Schritte ausführen wie beim Bearbeiten eines lokalen Skripts.

1. Führen Sie `Open-EditorFile test.ps1` oder `psedit test.ps1` aus, um die Remotedatei `test.ps1` zu öffnen. ![Datei „test.ps1“ in Open-EditorFile](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Bearbeiten Sie die Datei / legen Sie Haltepunkte fest. ![Bearbeiten und Festlegen von Haltepunkten](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Beginnen Sie mit dem Debuggen (F5) der Remotedatei.

![Debuggen der Remotedatei](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Das ist schon alles! Wir hoffen, dass wir mit dieser Anleitung Ihre Fragen zu Remotedebuggen und -bearbeitung mit PowerShell in VSCode beantwortet haben.

Zur Lösung evtl. noch auftretender Probleme steht Ihnen das [GitHub-Repository](http://github.com/powershell/vscode-powershell) zur Verfügung.
