---
title: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
description: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: f8e1e9af257037fc7bd74549e4197c9a1695e952
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587430"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Verwenden von Visual Studio Code für die Entwicklung mit PowerShell

Neben der [PowerShell ISE][ise] wird auch PowerShell in Visual Studio Code unterstützt.
Außerdem wird die PowerShell ISE zwar nicht mit PowerShell Core unterstützt, jedoch wird Visual Studio Code für PowerShell Core auf sämtlichen Plattformen (Windows, macOS und Linux) unterstützt.

Sie können Visual Studio Code unter Windows mit PowerShell Version 5 verwenden, wenn Sie Windows 10 verwenden oder für ältere Windows-Versionen (z.B. Windows 8.1) [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installieren.

Prüfen Sie, ob PowerShell auf Ihrem System vorhanden ist, bevor Sie das Programm starten.
Aktuelle Workloads unter Windows, macOS und Linux finden Sie unter:

- [Installieren von PowerShell Core unter Linux][install-pscore-linux]
- [Installieren von PowerShell Core unter macOS][install-pscore-macos]
- [Installing PowerShell Core on Windows (Installieren von PowerShell Core unter Windows)][install-pscore-windows]

Herkömmliche Windows PowerShell-Workloads finden Sie unter [Installieren von Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Bearbeiten von Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Installieren von Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on Linux (Ausführen von VS Code unter Linux)](https://code.visualstudio.com/docs/setup/linux) aus.

- **macOS:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on macOS (Ausführen von VS Code unter macOS)](https://code.visualstudio.com/docs/setup/mac) aus.

  > [!IMPORTANT]
  > Unter macOS müssen Sie OpenSSL für die PowerShell-Erweiterung installieren, damit diese einwandfrei funktionieren kann.
  > Dies funktioniert am besten, wenn Sie [Homebrew](http://brew.sh/) installieren und anschließend `brew install openssl` ausführen.
  > Visual Studio Code kann jetzt die Erweiterung PowerShell erfolgreich laden.

- **Windows:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on Windows (Ausführen von VS Code unter Windows)](https://code.visualstudio.com/docs/setup/windows) aus.

### <a name="2-installing-powershell-extension"></a>2. Installieren der PowerShell-Erweiterung

- Starten Sie die Visual Studio Code-App, indem Sie:
  - **Windows:** `code` in Ihre PowerShell-Sitzung eingeben.
  - **Linux:** `code` in Ihr Terminal eingeben.
  - **macOS:** `code` in Ihr Terminal eingeben.

- Starten Sie **Quick Open**, indem Sie **STRG+P** (**cmd+P** unter Mac) drücken.
- Geben Sie in Quick Open `ext install powershell` ein, und drücken Sie die **EINGABETASTE**.
- Dann öffnet sich die Ansicht **Erweiterungen** in der Seitenleiste. Wählen Sie die PowerShell-Erweiterung für Microsoft aus.
  Es sollte etwa Folgendes angezeigt werden:

  ![VSCode](../../images/vscode.png)

- Klicken Sie auf die Schaltfläche **Installieren** in der PowerShell-Erweiterung für Microsoft.
- Nach der Installation ändert sich die Schaltfläche **Installieren** in **Erneut laden**.
  Klicken Sie auf **Erneut laden**.
- Nachdem Visual Studio Code neu geladen wurde, können Sie Bearbeitungen vornehmen.

Klicken Sie z.B. auf **Datei > Neu**, um eine neue Datei zu erstellen.
Klicken Sie zum Speichern auf **Datei > Speichern**, und geben Sie anschließend einen Dateinamen ein, z.B. `HelloWorld.ps1`.
Klicken Sie auf das „x“ neben dem Dateinamen, um die Datei zu schließen.
Klicken Sie auf **Datei > Beenden**, um Visual Studio Code zu beenden.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Verwenden einer bestimmten installierten PowerShell-Version

Wenn Sie eine bestimmte PowerShell-Installation mit Visual Studio Code verwenden möchten, müssen Sie der Datei mit den Benutzereinstellungen eine neue Variable hinzufügen.

1. Klicken Sie auf **Datei > Voreinstellungen > Einstellungen**.
1. Anschließend werden zwei Editorbereiche angezeigt.
   Fügen Sie die nachfolgende Einstellung im Bereich rechts (`settings.json`) abhängig von Ihrem Betriebssystem zwischen den geschweiften Klammern (`{` und `}`) ein, und ersetzen Sie **\<version\>** durch die installierte PowerShell-Version:

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. Ersetzen Sie die Einstellung durch den Pfad zu der gewünschten ausführbaren PowerShell-Datei.
1. Speichern Sie die Datei mit den Einstellungen, und starten Sie Visual Studio Code neu.

#### <a name="configuration-settings-for-visual-studio-code"></a>Konfigurationseinstellungen für Visual Studio Code

Mithilfe der im vorherigen Absatz aufgeführten Schritte können Sie die Konfigurationseinstellungen zu `settings.json` hinzufügen.

Die folgenden Konfigurationseinstellungen werden für Visual Studio Code empfohlen:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Debuggen mit Visual Studio Code

### <a name="no-workspace-debugging"></a>Debuggen außerhalb des Arbeitsbereichs

Ab Visual Studio Code Version 1.9 können Sie PowerShell-Skripts debuggen, ohne den Ordner öffnen zu müssen, in dem das jeweilige Skript enthalten ist.
Öffnen Sie einfach die PowerShell-Skriptdatei über **Datei > Datei öffnen...**, legen Sie auf einer Zeile einen Breakpoint fest (indem Sie F9 drücken), und drücken Sie anschließend F5, um mit dem Debuggen zu beginnen.
Dann wird der Aktionsbereich „Debuggen“ angezeigt, über den Sie den Debugger anhalten und den Debugvorgang ausführen, fortsetzen oder abbrechen können.

### <a name="workspace-debugging"></a>Debuggen von Arbeitsbereichen

Wenn davon die Rede ist, Arbeitsbereiche zu debuggen, ist damit das Debuggen eines Ordners gemeint, den Sie in Visual Studio Code über **Ordner öffnen...** im Menü **Datei** öffnen.
In der Regel wird dafür der PowerShell-Projektordner und bzw. oder der Stamm des Git-Repositorys geöffnet.

Sie können sogar in diesem Modus damit beginnen, das zu diesem Zeitpunkt ausgewählte PowerShell-Skript zu debuggen, indem Sie F5 drücken.
Wenn Sie allerdings Arbeitsbereiche debuggen, kann nicht nur für die zu diesem Zeitpunkt geöffnete Datei ein Debugvorgang ausgeführt werden, sondern es können auch mehrere Debugkonfigurationen definiert werden.
Beispielsweise können Sie Konfigurationen zu folgenden Vorgängen hinzufügen:

- Starten von Pester-Tests im Debugger
- Starten einer bestimmten Datei mit Argumenten im Debugger
- Starten einer interaktiven Sitzung im Debugger
- Anfügen des Debuggers an einen PowerShell-Hostvorgang

  Führen Sie die folgenden Schritte aus, um eine Konfigurationsdatei für den Debugvorgang zu erstellen:

  1. Öffnen Sie die Ansicht **Debuggen**, indem Sie **STRG+UMSCHALT+D** drücken (oder **cmd+UMSCHALT+D** unter Mac).
  2. Klicken Sie in der Symbolleiste auf das Zahnradsymbol **Konfigurieren**.
  3. Visual Studio Code zeigt folgende Eingabeaufforderung an: **Umgebung auswählen**.
  Wählen Sie **PowerShell** aus.

  Nachdem Sie diesen Vorgang ausgeführt haben, erstellt Visual Studio Code im Stamm Ihres Arbeitsbereichordners ein Verzeichnis und eine Datei: „.vscode\launch.json“.
  An dieser Stelle wird Ihre Debugkonfiguration gespeichert. Wenn sich Ihre Dateien in einem Git-Repository befinden, sollten Sie einen Commit für die launch.json-Datei ausführen.
  In dieser Datei sind folgende Inhalte enthalten:

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  Dies ist ein Beispiel für häufig auftretende Debugszenarios.
  Wenn Sie diese Datei im Editor öffnen, wird Ihnen jedoch die Schaltfläche **Konfiguration hinzufügen...** angezeigt.
  Sie können auf diese Schaltfläche klicken, um weitere Debugkonfigurationen für PowerShell hinzuzufügen. Sie können zum Beispiel die Konfiguration **PowerShell: Launch Script** (PowerShell: Skript starten) hinzufügen.
  Mithilfe dieser Konfiguration können Sie optionale Argumente für eine bestimmte Datei angeben, die immer gestartet werden soll, wenn Sie F5 drücken. Dabei macht es keinen Unterschied, welche Datei zu diesem Zeitpunkt im Editor aktiv ist.

  Nachdem Sie die Debugkonfiguration eingerichtet haben, können Sie auswählen, welche Konfiguration Sie während der Debugsitzung verwenden möchten, indem Sie eine der Debugkonfigurationen aus der Dropdownliste in der Symbolleistenansicht **Debuggen** auswählen.

  Im Folgenden werden einige Blogbeiträge aufgeführt, die hilfreich für die ersten Schritte mit der PowerShell-Erweiterung für Visual Studio Code sein können:

Visual Studio Code:

- [PowerShell-Erweiterungen][ps-extension]
- [Write and debug PowerShell scripts in Visual Studio Code (Schreiben und Debuggen von PowerShell-Skripts in Visual Studio Code)][debug]
- [Debugging Visual Studio Code Guidance (Debuggen der Visual Studio Code-Anleitung)][vscode-guide]
- [Debugging PowerShell in Visual Studio Code (Debuggen von PowerShell in Visual Studio Code)][ps-vscode]
- [Get started with PowerShell development in Visual Studio Code (Erste Schritte für die PowerShell-Entwicklung in Visual Studio Code)][getting-started]
- [Visual Studio Code editing features for PowerShell development – Part 1 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 1)][editing-part1]
- [Visual Studio Code editing features for PowerShell development – Part 2 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 2)][editing-part2]
- [Debugging PowerShell script in Visual Studio Code – Part 1 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 1)][debugging-part1]
- [Debugging PowerShell script in Visual Studio Code – Part 2 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 2)][debugging-part2]

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>PowerShell-Erweiterung für Visual Studio Code

Sie finden den Quellcode der PowerShell-Erweiterung auf [GitHub](https://github.com/PowerShell/vscode-powershell).