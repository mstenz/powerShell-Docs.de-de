---
title: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
description: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325228"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Verwenden von Visual Studio Code für die Entwicklung mit PowerShell

Neben der [PowerShell ISE][ise] wird auch PowerShell in Visual Studio Code (VS Code) unterstützt. Außerdem wird die PowerShell ISE zwar nicht mit PowerShell Core unterstützt, jedoch wird VS Code für PowerShell Core auf sämtlichen Plattformen (Windows, macOS und Linux) unterstützt.

Sie können VS Code unter Windows mit PowerShell Version 5 verwenden, wenn Sie Windows 10 verwenden oder für ältere Windows-Versionen (z.B. Windows 8.1) [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) installieren.

Prüfen Sie, ob PowerShell auf Ihrem System vorhanden ist, bevor Sie das Programm starten. Aktuelle Workloads unter Windows, macOS und Linux finden Sie unter:

- [Installieren von PowerShell Core unter Linux][install-pscore-linux]
- [Installieren von PowerShell Core unter macOS][install-pscore-macos]
- [Installing PowerShell Core on Windows (Installieren von PowerShell Core unter Windows)][install-pscore-windows]

Herkömmliche Windows PowerShell-Workloads finden Sie unter [Installieren von Windows PowerShell][install-winps].

## <a name="editing-with-vscode"></a>Bearbeiten mit VS Code

1. [Installieren von VS Code](https://code.visualstudio.com/Docs/setup/setup-overview)

   - **Linux:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on Linux (Ausführen von VS Code unter Linux)](https://code.visualstudio.com/docs/setup/linux) aus.
   - **macOS:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on macOS (Ausführen von VS Code unter macOS)](https://code.visualstudio.com/docs/setup/mac) aus.

     > [!IMPORTANT]
     > Unter macOS müssen Sie OpenSSL für die PowerShell-Erweiterung installieren, damit diese einwandfrei funktionieren kann. Dies funktioniert am besten, wenn Sie [Homebrew](https://brew.sh/) installieren und anschließend `brew install openssl` ausführen. VS Code kann jetzt die PowerShell-Erweiterung erfolgreich laden.

   - **Windows:** Führen Sie die Installationsanweisungen auf der Seite [Running VS Code on Windows (Ausführen von VS Code unter Windows)](https://code.visualstudio.com/docs/setup/windows) aus.

2. Installieren der PowerShell-Erweiterung

   - Starten Sie VS Code, indem Sie:
     - **Windows:** `code` in Ihre PowerShell-Sitzung eingeben.
     - **Linux:** `code` in Ihr Terminal eingeben.
     - **macOS:** `code` in Ihr Terminal eingeben.
   - Starten Sie **Quick Open**, indem Sie <kbd>STRG</kbd>+<kbd>P</kbd> (<kbd>cmd</kbd>+<kbd>P</kbd> unter Mac) drücken.
   - Geben Sie in Quick Open `ext install powershell` ein, und drücken Sie die **EINGABETASTE**.
   - Dann öffnet sich die Ansicht **Erweiterungen** in der Seitenleiste. Wählen Sie die PowerShell-Erweiterung für Microsoft aus.
     Es sollte etwa Folgendes angezeigt werden:

     ![VSCode](../../images/using-vscode/vscode.png)

   - Klicken Sie auf die Schaltfläche **Installieren** in der PowerShell-Erweiterung für Microsoft.
   - Nach der Installation ändert sich die Schaltfläche **Installieren** in **Erneut laden**. Klicken Sie auf **Erneut laden**.
   - Nachdem VS Code neu geladen wurde, können Sie Bearbeitungen vornehmen.

Klicken Sie z.B. auf **Datei > Neu**, um eine neue Datei zu erstellen. Klicken Sie zum Speichern auf **Datei > Speichern**, und geben Sie anschließend einen Dateinamen ein, z.B. `HelloWorld.ps1`. Klicken Sie auf das „x“ neben dem Dateinamen, um die Datei zu schließen. Wählen Sie zum Beenden von VS Code **Datei > Beenden** aus.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installieren der PowerShell-Erweiterung auf eingeschränkten Systemen

Einige Systeme sind so eingerichtet, dass alle Codesignaturen überprüft werden müssen und die Editor-Dienste von PowerShell daher manuell für die Ausführung auf dem System genehmigt werden müssen. Ein Gruppenrichtlinienupdate, das die Ausführungsrichtlinie ändert, ist eine wahrscheinliche Ursache, wenn Sie die PowerShell-Erweiterung installiert haben, aber einen Fehler wie diesen erhalten:

```
Language server startup failed.
```

Öffnen Sie zur manuellen Genehmigung der Editor-Dienste von PowerShell und somit der PowerShell-Erweiterung für VSCode eine PowerShell-Eingabeaufforderung, und führen Sie Folgendes aus:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Sie werden gefragt: „Do you want to run software from this untrusted publisher?“ (Möchten Sie Software von diesem nicht vertrauenswürdigen Herausgeber ausführen?). Geben Sie `R` ein, um die Datei auszuführen. Öffnen Sie dann VS Code, und überprüfen Sie, ob die PowerShell-Erweiterung ordnungsgemäß funktioniert. Wenn Sie noch immer Probleme haben, lassen Sie uns dies auf [GitHub](https://github.com/PowerShell/vscode-powershell/issues) wissen.

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Auswählen einer Version von PowerShell für die Verwendung mit der Erweiterung

Mit einer parallelen Installation von PowerShell Core und Windows PowerShell ist es jetzt möglich, eine bestimmte Version von PowerShell mit der PowerShell-Erweiterung zu verwenden. Verwenden Sie die folgenden Schritte, um die Version auszuwählen:

1. Öffnen Sie die Befehlspalette (<kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> auf Windows und Linux, <kbd>BEFEHL</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> unter MacOS).
1. Suchen Sie nach „Sitzung“.
1. Klicken Sie auf „PowerShell“: Zeigen Sie das Menü „Sitzung“ an.
1. Wählen Sie die Version von PowerShell aus der Liste aus, die Sie verwenden möchten, z. B. „PowerShell Core“.

> [!IMPORTANT]
> Dieses Feature sucht in ein paar bekannten Pfaden unter verschiedenen Betriebssystemen, um die Installationsspeicherorte von PowerShell zu ermitteln. Wenn Sie PowerShell an einem untypischen Speicherort installiert haben, wird es möglicherweise anfangs nicht im Menü „Sitzung“ angezeigt. Sie können das Menü „Sitzung“ erweitern, indem Sie [Ihre eigenen benutzerdefinierten Pfade hinzufügen](#adding-your-own-powershell-paths-to-the-session-menu), wie unten beschrieben.

>[!NOTE]
> Es gibt eine weitere Möglichkeit, um zum Menü „Sitzung“ zu gelangen. Wenn Sie eine PowerShell-Datei im Editor geöffnet haben, wird unten rechts eine grüne Versionsnummer angezeigt. Wenn Sie auf diese Versionsnummer klicken, gelangen Sie zum Menü „Sitzung“.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Hinzufügen Ihres eigenen PowerShell-Pfads zum Menü „Sitzung“

Sie können dem Menü „Sitzung“ mithilfe einer VS Code-Einstellung andere PowerShell-Pfade für ausführbare Dateien hinzufügen.

Fügen Sie der Liste `powershell.powerShellAdditionalExePaths` eine Element hinzu, oder erstellen Sie die Liste, wenn sie in Ihrer `settings.json` nicht vorhanden ist:

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

Jedes Element benötigt:

* `exePath`: Der Pfad zu `pwsh` oder zur ausführbaren `powershell`-Datei.
* `versionName`: Der Text, der im Menü „Sitzung“ angezeigt wird.

Sie können die PowerShell-Standardversion so festlegen, dass die Einstellung `powershell.powerShellDefaultVersion` verwendet wird, indem Sie diese auf den Text festlegen, der im Menü „Sitzung“ angezeigt wird (auch bekannt als `versionName` in der letzten Einstellung):

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

Wenn Sie diese Einstellung festgelegt haben, starten Sie VS Code neu, oder verwenden Sie die Befehlspalettenaktion „Developer: Fenster erneut laden“, um das aktuelle Fenster neu zu laden.

Wenn Sie das Menü „Sitzung“ öffnen, werden jetzt Ihre zusätzlichen PowerShell-Versionen angezeigt.

> [!NOTE]
> Wenn Sie PowerShell aus der Quelle erstellen, ist dies eine hervorragende Möglichkeit zum Testen Ihres lokalen Builds von PowerShell.

#### <a name="configuration-settings-for-vscode"></a>Konfigurationseinstellungen für VS Code

Mithilfe der im vorherigen Absatz aufgeführten Schritte können Sie die Konfigurationseinstellungen zu `settings.json` hinzufügen.

Die folgenden Konfigurationseinstellungen werden für VS Code empfohlen:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Wenn Sie nicht möchten, dass diese Einstellungen für alle Dateitypen gelten, können Sie in VS Code auch sprachspezifische Konfigurationen vornehmen. Sie können sprachspezifische Einstellungen erstellen, indem Sie Einstellungen in ein `[<language-name>]`-Feld einfügen. Beispiel:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Weitere Informationen zur Dateicodierung in VS Code finden Sie unter [Informationen zur Dateicodierung](understanding-file-encoding.md).

## <a name="debugging-with-vscode"></a>Debuggen mit VS Code

### <a name="no-workspace-debugging"></a>Debuggen außerhalb des Arbeitsbereichs

Ab VS Code Version 1.9 können Sie PowerShell-Skripts debuggen, ohne den Ordner öffnen zu müssen, in dem das jeweilige PowerShell-Skript enthalten ist. Öffnen Sie die PowerShell-Skriptdatei über **Datei > Datei öffnen**, legen Sie einen Breakpoint für eine Zeile fest (indem Sie <kbd>F9</kbd> drücken), und drücken Sie dann <kbd>F5</kbd>, um mit dem Debuggen zu beginnen. Dann wird der Aktionsbereich „Debuggen“ angezeigt, über den Sie den Debugger anhalten und den Debugvorgang ausführen, fortsetzen oder abbrechen können.

### <a name="workspace-debugging"></a>Debuggen von Arbeitsbereichen

Wenn davon die Rede ist, Arbeitsbereiche zu debuggen, ist damit das Debuggen eines Ordners gemeint, den Sie in Visual Studio Code über **Ordner öffnen...** im Menü **Datei** öffnen. In der Regel wird dafür der PowerShell-Projektordner und bzw. oder der Stamm des Git-Repositorys geöffnet.

Sie können sogar in diesem Modus damit beginnen, das aktuell ausgewählte PowerShell-Skript zu debuggen, indem Sie <kbd>F5</kbd> drücken. Wenn Sie allerdings Arbeitsbereiche debuggen, kann nicht nur für die zu diesem Zeitpunkt geöffnete Datei ein Debugvorgang ausgeführt werden, sondern es können auch mehrere Debugkonfigurationen definiert werden. Beispielsweise können Sie Konfigurationen zu folgenden Vorgängen hinzufügen:

- Starten von Pester-Tests im Debugger
- Starten einer bestimmten Datei mit Argumenten im Debugger
- Starten einer interaktiven Sitzung im Debugger
- Anfügen des Debuggers an einen PowerShell-Hostvorgang

Führen Sie die folgenden Schritte aus, um eine Konfigurationsdatei für den Debugvorgang zu erstellen:

  1. Öffnen Sie die Ansicht **Debuggen**, indem Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd> drücken (oder <kbd>cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd> unter Mac).
  2. Klicken Sie in der Symbolleiste auf das Zahnradsymbol **Konfigurieren**.
  3. VS Code zeigt folgende Eingabeaufforderung an: **Umgebung auswählen**. Wählen Sie **PowerShell** aus.

  Nachdem Sie diesen Vorgang ausgeführt haben, erstellt VS Code im Stamm Ihres Arbeitsbereichordners ein Verzeichnis und eine Datei: „.vscode\launch.json“. An dieser Stelle wird Ihre Debugkonfiguration gespeichert. Wenn sich Ihre Dateien in einem Git-Repository befinden, sollten Sie einen Commit für die launch.json-Datei ausführen. In dieser Datei sind folgende Inhalte enthalten:

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

  Dies ist ein Beispiel für häufig auftretende Debugszenarios. Wenn Sie diese Datei im Editor öffnen, wird Ihnen jedoch die Schaltfläche **Konfiguration hinzufügen...** angezeigt. Sie können auf diese Schaltfläche klicken, um weitere Debugkonfigurationen für PowerShell hinzuzufügen. Sie können zum Beispiel die Konfiguration **PowerShell: Launch Script** (PowerShell: Skript starten) hinzufügen. Mithilfe dieser Konfiguration können Sie optionale Argumente für eine bestimmte Datei angeben, die immer gestartet werden soll, wenn Sie <kbd>F5</kbd> drücken. Dabei macht es keinen Unterschied, welche Datei zu diesem Zeitpunkt im Editor aktiv ist.

  Nachdem Sie die Debugkonfiguration eingerichtet haben, können Sie auswählen, welche Konfiguration Sie während der Debugsitzung verwenden möchten, indem Sie eine der Debugkonfigurationen aus der Dropdownliste in der Symbolleistenansicht **Debuggen** auswählen.

Im Folgenden werden einige Blogbeiträge aufgeführt, die bei den ersten Schritten mit der PowerShell-Erweiterung für Visual Studio Code hilfreich sein können:

- [PowerShell-Erweiterung][ps-extension]
- [Write and debug PowerShell scripts in Visual Studio Code (Schreiben und Debuggen von PowerShell-Skripts in Visual Studio Code)][debug]
- [Debugging Visual Studio Code Guidance (Anleitung zum Debuggen in Visual Studio Code)][vscode-guide]
- [Debugging PowerShell in Visual Studio Code (Debuggen von PowerShell in Visual Studio Code)][ps-vscode]
- [Get started with PowerShell development in Visual Studio Code (Erste Schritte für die PowerShell-Entwicklung in Visual Studio Code)][getting-started]
- [Visual Studio Code editing features for PowerShell development – Part 1 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 1)][editing-part1]
- [Visual Studio Code editing features for PowerShell development – Part 2 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 2)][editing-part2]
- [Debugging PowerShell script in Visual Studio Code – Part 1 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 1)][debugging-part1]
- [Debugging PowerShell script in Visual Studio Code – Part 2 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 2)][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
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

## <a name="powershell-extension-for-vscode"></a>PowerShell-Erweiterung für VS Code

Sie finden den Quellcode der PowerShell-Erweiterung auf [GitHub](https://github.com/PowerShell/vscode-powershell).
