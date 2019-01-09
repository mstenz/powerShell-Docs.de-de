---
title: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
description: Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655606"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Verwenden von Visual Studio Code für Remotebearbeitung und Remotedebuggen

Für diejenigen unter Ihnen, die mit der ISE vertraut waren, denken Sie daran, dass Sie ausführen könnten `psedit file.ps1` über die integrierte Konsole zum Öffnen von Dateien – lokal oder remote - rechten Maustaste in der ISE.

Wie sich herausstellt, ist dieses Feature auch in der PowerShell-Erweiterung für VSCode verfügbar. Diesem Leitfaden erfahren Sie, wie es geht.

## <a name="prerequisites"></a>Voraussetzungen

Dieses Handbuch setzt voraus, dass Sie haben:

- eine Remoteressource (z. B.: eine VM, einen Container), dass Sie Zugriff haben
- PowerShell, die darauf, und der Hostcomputer ausgeführt wird
- VSCode und der PowerShell-Erweiterung für VSCode

Dieses Feature funktioniert auf Windows PowerShell und PowerShell Core.

Dieses Feature funktioniert auch bei der Verbindung von eines Remotecomputer über WinRM, PowerShell Direct oder SSH. Wenn Sie SSH verwenden möchten, aber Windows verwenden, sehen Sie sich die [Win32-Version von SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Los geht's!

In diesem Abschnitt erläutere ich, wie remote bearbeiten und Debuggen, die aus meinem MacBook Pro, auf einer Ubuntu-VM in Azure ausgeführt werden. Ich kann keine werden mithilfe von Windows, aber **der Prozess ist identisch**.

### <a name="local-file-editing-with-open-editorfile"></a>Lokale Datei mit Open-EditorFile bearbeiten

Mit der PowerShell-Erweiterung für VSCode gestartet und die integrierte PowerShell-Konsole geöffnet, gebe `Open-EditorFile foo.ps1` oder `psedit foo.ps1` auf die lokalen foo. ps1-Datei direkt im Editor zu öffnen.

![Open-EditorFile foo. ps1 funktioniert lokal.](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo. ps1 muss bereits vorhanden sein.

Von dort aus können wir folgende Aktionen ausführen:

Haltepunkte hinzufügen, um den Bundsteg ![Breakpoint um Bundsteg hinzufügen](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

ein, und drücken Sie F5, um das PowerShell-Skript zu debuggen.
![Debuggen lokale PowerShell-Skript](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Sie können während des Debuggens die Debugging-Konsole interagieren, sehen Sie sich die Variablen im Bereich auf der linken Seite und alle anderen standardmäßigen debugging-Tools.

### <a name="remote-file-editing-with-open-editorfile"></a>Remote-Datei mit Open-EditorFile bearbeiten

Jetzt wenden wir uns in remote-Datei bearbeiten und Debuggen. Die Schritte sind nahezu identisch, gibt es nur einen Aspekt benötigten zuerst tun – geben unsere PowerShell-Sitzung mit dem Remoteserver.

Es ist ein Cmdlet für die zu diesem Zweck ein. Es heißt `Enter-PSSession`.

Die unten watered Erläuterung des-Cmdlets ist:

- `Enter-PSSession -ComputerName foo` Startet eine-Sitzung über WinRM
- `Enter-PSSession -ContainerId foo` und `Enter-PSSession -VmId foo` starten Sie eine Sitzung über PowerShell Direct
- `Enter-PSSession -HostName foo` Startet eine-Sitzung über SSH

Weitere Informationen zur `Enter-PSSession`, sehen Sie sich die Dokumentation [hier](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Ich verwende SSH für das Remoting, da ich auf einem Ubuntu-VM in Azure über MacOS werde.

Zunächst in der integrierten Konsole führen wir unsere Enter-PSSession. Wissen Sie, dass Sie in der Sitzung sind da `[something]` wird auf der linken Seite Ihre Eingabeaufforderung angezeigt.

![Der Aufruf von Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Von dort aus können wir die genauen Schritte tun, als ob es ein lokales Skript bearbeitet haben.

1. Führen Sie `Open-EditorFile test.ps1` oder `psedit test.ps1` , öffnen Sie die Remote `test.ps1` Datei ![Open-EditorFile die test.ps1-Datei](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Bearbeiten Sie die Datei/Set-Haltepunkte ![Bearbeiten, und legen Sie Haltepunkte fest](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Starten des Debuggens (F5) der remote-Datei

![Debuggen der remote-Datei](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Das ist alles schon! Wir hoffen, dass in der vorliegenden, bereinigen Sie Fragen geholfen zu remote Debuggen und Bearbeiten von PowerShell in Visual Studio Code.

Wenn Sie Probleme haben, können Sie Probleme öffnen [GitHub-Repository](http://github.com/powershell/vscode-powershell).
