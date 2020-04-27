---
title: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
description: Verwenden von Visual Studio Code für die Entwicklung mit PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 5251094388f6abc7da7f2cc706537eade78df7c9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978694"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Verwenden von Visual Studio Code für die Entwicklung mit PowerShell

[Visual Studio Code][vscode] ist ein plattformübergreifender Skript-Editor von Microsoft. In Verbindung mit der [PowerShell-Erweiterung][psext] bietet er eine umfassende und interaktive Oberfläche zur Skriptbearbeitung, die das Schreiben zuverlässiger PowerShell-Skripts vereinfacht. Visual Studio Code mit PowerShell-Erweiterung ist der empfohlene Editor zum Schreiben von PowerShell-Skripts.

Die folgenden PowerShell-Versionen werden unterstützt:

- PowerShell 7 und höher (Windows, macOS und Linux)
- PowerShell Core 6 (Windows, macOS und Linux)
- Windows PowerShell 5.1 (nur Windows)

> [!NOTE]
> Visual Studio Code ist nicht identisch mit [Visual Studio][].

## <a name="getting-started"></a>Erste Schritte

Prüfen Sie, ob PowerShell auf Ihrem System vorhanden ist, bevor Sie starten. Aktuelle Workloads unter Windows, macOS und Linux finden Sie unter den folgenden Links:

- [Installieren von PowerShell unter Linux][install-pscore-linux]
- [Installieren von PowerShell unter macOS][install-pscore-macos]
- [Installieren von PowerShell unter Windows][install-pscore-windows]

Herkömmliche Windows PowerShell-Workloads finden Sie unter [Installieren von Windows PowerShell][install-winps].

> [!IMPORTANT]
> Die [Windows PowerShell ISE][ise] ist für Windows weiterhin verfügbar. Sie befindet sich jedoch nicht mehr in der aktiven Featureentwicklung. Die ISE funktioniert nicht mit PowerShell 6 und höher. Als Windows-Komponente wird sie weiterhin offiziell mit Sicherheits- und Wartungsfixes hoher Priorität unterstützt.
> Es ist nicht geplant, die ISE aus Windows zu entfernen.

## <a name="editing-with-visual-studio-code"></a>Bearbeiten von Visual Studio Code

1. Installieren Sie Visual Studio Code. Weitere Informationen finden Sie in der Übersicht [Einrichten von Visual Studio Code][vsc-setup].

   Dort finden Sie Installationsanweisungen für jede Plattform:

   - **Windows**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter Windows][vsc-setup-win] aus.
   - **macOS**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter macOS][vsc-setup-macOS] aus.
   - **Linux**: Führen Sie die Installationsanweisungen auf der Seite [Ausführen von Visual Studio Code unter Linux][vsc-setup-linux] aus.

1. Installieren Sie die PowerShell-Erweiterung.

   1. Starten Sie die Visual Studio Code-App, indem Sie `code` in einer Konsole eingeben bzw. `code-insiders`, falls Sie Visual Studio Code für Insider installiert haben.
   1. Starten Sie **Quick Open** unter Windows oder Linux, indem Sie <kbd>STRG</kbd>+<kbd>P</kbd> drücken. Drücken Sie unter macOS <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Geben Sie in Quick Open `ext install powershell` ein, und drücken Sie die **EINGABETASTE**.
   1. Dann öffnet sich die Ansicht **Erweiterungen** in der Seitenleiste. Wählen Sie die PowerShell-Erweiterung für Microsoft aus.
      Ihnen wird in etwa folgender Visual Studio Code-Bildschirm angezeigt:

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. Klicken Sie auf die Schaltfläche **Installieren** in der PowerShell-Erweiterung für Microsoft.
   1. Nach der Installation ändert sich die Schaltfläche **Installieren** in **Erneut laden**. Klicken Sie auf **Erneut laden**.
   1. Nachdem Visual Studio Code neu geladen wurde, können Sie Bearbeitungen vornehmen.

Klicken Sie z. B. auf **Datei > Neu**, um eine neue Datei zu erstellen. Klicken Sie zum Speichern auf **Datei > Speichern**, und geben Sie anschließend einen Dateinamen ein, z. B. `HelloWorld.ps1`. Klicken Sie auf `X` neben dem Dateinamen, um die Datei zu schließen. Klicken Sie auf **Datei > Beenden**, um Visual Studio Code zu beenden.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installieren der PowerShell-Erweiterung auf eingeschränkten Systemen

Einige Systeme sind so eingerichtet, dass alle Codesignaturen überprüft werden müssen. Unter Umständen wird der folgende Fehler angezeigt:

```
Language server startup failed.
```

Dieses Problem kann auftreten, wenn die PowerShell-Ausführungsrichtlinie von Windows-Gruppenrichtlinie festgelegt ist. Öffnen Sie eine PowerShell-Eingabeaufforderung, um die Editor-Dienste von PowerShell und die PowerShell-Erweiterung für Visual Studio Code manuell zu genehmigen, und führen Sie den folgenden Befehl aus:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Sie werden gefragt: **Möchten Sie Software von diesem nicht vertrauenswürdigen Herausgeber ausführen?** . Geben Sie `A` ein, um die Datei auszuführen. Öffnen Sie dann Visual Studio Code, und überprüfen Sie, ob die PowerShell-Erweiterung ordnungsgemäß funktioniert. Wenn weiterhin Probleme auftreten, lassen Sie uns dies auf [GitHub-Probleme][] wissen.

> [!NOTE]
> Die PowerShell-Erweiterung für Visual Studio Code unterstützt nicht die Ausführung im eingeschränkten Sprachmodus. Weitere Informationen finden Sie unter dem [GitHub-Problem #606][i606].

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Auswählen einer Version von PowerShell für die Verwendung mit der Erweiterung

Mit einer parallelen Installation von PowerShell Core und Windows PowerShell ist es jetzt möglich, eine bestimmte Version von PowerShell mit der PowerShell-Erweiterung zu verwenden. Dieses Feature sucht in ein paar bekannten Pfaden unter verschiedenen Betriebssystemen, um PowerShell-Installationen zu ermitteln.

Verwenden Sie die folgenden Schritte, um die Version auszuwählen:

1. Öffnen Sie die **Befehlspalette** unter Windows oder Linux mit <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>. Verwenden Sie unter macOS <kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>.
1. Suchen Sie nach **Sitzung**.
1. Klicken Sie auf **PowerShell: Menü „Sitzung“ anzeigen**.
1. Wählen Sie die Version von PowerShell aus der Liste aus, die Sie verwenden möchten, z. B. **PowerShell Core**.

Wenn Sie PowerShell an einem untypischen Speicherort installiert haben, wird es möglicherweise anfangs nicht im Menü „Sitzung“ angezeigt. Sie können das Menü „Sitzung“ erweitern, indem Sie [Ihre eigenen benutzerdefinierten Pfade hinzufügen](#adding-your-own-powershell-paths-to-the-session-menu), wie unten beschrieben.

> [!NOTE]
> Der Zugriff auf das PowerShell-Sitzungsmenü ist auch über die grüne Versionsnummer unten rechts auf der Statusleiste möglich. Wenn Sie auf diese Versionsnummer klicken, wird das Menü „Sitzung“ geöffnet.

## <a name="configuration-settings-for-visual-studio-code"></a>Konfigurationseinstellungen für Visual Studio Code

Wenn Sie mit dem Ändern von Einstellungen in Visual Studio Code nicht vertraut sind, sollten Sie die [Dokumentation zu den Visual Studio Code-Einstellungen][vsc-settings] lesen.

Anschließend können Sie Konfigurationseinstellungen in `settings.json` hinzufügen.

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Wenn Sie nicht möchten, dass diese Einstellungen für alle Dateitypen gelten, können Sie in Visual Studio Code auch sprachspezifische Konfigurationen vornehmen. Sie können sprachspezifische Einstellungen erstellen, indem Sie Einstellungen in ein `[<language-name>]` einfügen. Beispiel:

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> Weitere Informationen zur Dateicodierung in Visual Studio Code finden Sie unter [Informationen zur Dateicodierung][file-encoding].
>
> Weitere Tipps zum Konfigurieren von Visual Studio Code für die PowerShell-Bearbeitung finden Sie unter [Replizieren der ISE-Benutzeroberfläche in Visual Studio Code][vsc-ise].

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Hinzufügen Ihres eigenen PowerShell-Pfads zum Menü „Sitzung“

Sie können dem Sitzungsmenü über die folgende [Visual Studio Code-Einstellung](https://code.visualstudio.com/docs/getstarted/settings) andere PowerShell-Pfade für ausführbare Dateien hinzufügen: `powershell.powerShellAdditionalExePaths`.

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

- `exePath`: Der Pfad zu `pwsh` oder zur ausführbaren `powershell`-Datei.
- `versionName`: Der Text, der im Menü „Sitzung“ angezeigt wird.

Zum Festlegen der PowerShell-Standardversion legen Sie den Wert `powershell.powerShellDefaultVersion` auf den im Sitzungsmenü angezeigten Text fest (auch als `versionName` bezeichnet):

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

Nachdem Sie diese Einstellung konfiguriert haben, starten Sie Visual Studio Code neu, oder laden Sie das aktuelle Visual Studio Code-Fenster über die **Befehlspalette**, und geben Sie **Entwickler: Fenster neu laden** ein.

Wenn Sie das Menü „Sitzung“ öffnen, werden jetzt Ihre zusätzlichen PowerShell-Versionen angezeigt.

> [!NOTE]
> Wenn Sie PowerShell aus der Quelle erstellen, ist dies eine hervorragende Möglichkeit zum Testen Ihres lokalen Builds von PowerShell.

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>Verwenden einer älteren Version der PowerShell-Erweiterung für Windows PowerShell v3 und v4

Die aktuelle PowerShell-Erweiterung bietet keine Unterstützung für [PowerShell v3 und v4][i1310]. Sie können jedoch die letzte Version der Erweiterung verwenden, die PowerShell v3 und v4 unterstützt.

> [!CAUTION]
> Für diese ältere Version der Erweiterung werden keine weiteren Fixes bereitgestellt. Sie wird in der vorgelegten Form („AS IS“) bereitgestellt, ist aber für Sie verfügbar, wenn Sie noch Windows PowerShell v3 und Windows PowerShell v4 verwenden.

Öffnen Sie zunächst den Erweiterungsbereich, und suchen Sie nach `PowerShell`. Klicken Sie dann auf das Zahnrad, und wählen Sie **Andere Version installieren** aus.

![Andere Version installieren...](media/using-vscode/install-another-version.png)

Wählen Sie anschließend die Version **2020.1.0** aus. Diese Version der Erweiterung ist die letzte Version, die v3 und v4 unterstützt. Fügen Sie außerdem die folgende Einstellung hinzu, damit Ihre Erweiterungsversion nicht automatisch aktualisiert wird:

```json
{
    "extensions.autoUpdate": false
}
```

Die Version **2020.1.0** wird auf absehbare Zeit funktionieren. Dennoch könnte Visual Studio Code eine Änderung implementieren, die bei dieser Version der Erweiterung einen Fehler verursacht. Aus diesem Grund und aufgrund der fehlenden Unterstützung wird eine der beiden folgenden Aktionen empfohlen:

- Upgrade auf Windows PowerShell 5.1
- Installieren von PowerShell 7 (dies ist eine parallele Installation zu Windows PowerShell, die mit der PowerShell-Erweiterung am besten funktioniert)

## <a name="debugging-with-visual-studio-code"></a>Debuggen mit Visual Studio Code

### <a name="no-workspace-debugging"></a>Debuggen außerhalb des Arbeitsbereichs

In Visual Studio Code Version 1.9 (oder höher) können Sie PowerShell-Skripts debuggen, ohne den Ordner öffnen zu müssen, in dem das PowerShell-Skript enthalten ist.

1. Öffnen Sie die PowerShell-Skriptdatei über **Datei > Datei öffnen...**
1. Legen Sie einen Breakpoint fest (wählen Sie eine Zeile aus, und drücken Sie dann <kbd>F9</kbd>)
1. Drücken Sie <kbd>F5</kbd>, um das Debuggen zu starten

Dann wird der Aktionsbereich „Debuggen“ angezeigt, über den Sie den Debugger anhalten und den Debugvorgang ausführen, fortsetzen oder abbrechen können.

### <a name="workspace-debugging"></a>Debuggen von Arbeitsbereichen

Wenn davon die Rede ist, Arbeitsbereiche zu debuggen, ist damit das Debuggen eines Ordners gemeint, den Sie über **Ordner öffnen...** im Menü **Datei** geöffnet haben. In der Regel ist dies der PowerShell-Projektordner oder der Stamm des Git-Repositorys. Beim Debuggen von Arbeitsbereichen kann nicht nur für die aktuell geöffnete Datei ein Debugvorgang ausgeführt werden, sondern es können auch mehrere Debugkonfigurationen definiert werden.

Führen Sie die folgenden Schritte aus, um eine Konfigurationsdatei für den Debugvorgang zu erstellen:

1. Öffnen Sie die Ansicht **Debuggen** in Windows oder Linux, indem Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd> drücken. Drücken Sie unter macOS <kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd>.
1. Klicken Sie auf den **Link zum Erstellen einer Datei „launch.json“** .
1. Wählen Sie in der Eingabeaufforderung **Umgebung auswählen** die Option **PowerShell** aus.
1. Wählen Sie den gewünschten Debugtyp aus:

   - **Aktuelle Datei starten**: Starten und Debuggen der Datei im aktuell aktiven Editor-Fenster
   - **Skript starten**: Starten und Debuggen der angegebenen Datei oder des angegebenen Befehls
   - **Interaktive Sitzung**: Debuggen von Befehlen, die über die integrierte Konsole ausgeführt werden
   - **Anfügen**: Anfügen des Debuggers an einen ausgeführten PowerShell-Hostvorgang

Visual Studio Code erstellt im Stamm Ihres Arbeitsbereichsordners ein Verzeichnis und eine Datei `.vscode\launch.json` zum Speichern der Debugkonfiguration. Wenn sich Ihre Dateien in einem Git-Repository befinden, sollten Sie einen Commit für die `launch.json`-Datei ausführen. Die `launch.json`-Datei beinhaltet:

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

Diese Datei ist ein Beispiel für häufig auftretende Debugszenarios. Wenn Sie diese Datei im Editor öffnen, wird die Schaltfläche **Konfiguration hinzufügen...** angezeigt. Sie können auf diese Schaltfläche klicken, um weitere Debugkonfigurationen für PowerShell hinzuzufügen. Sie können zum Beispiel die Konfiguration **PowerShell: Launch Script** (PowerShell: Skript starten) hinzufügen. Mithilfe dieser Konfiguration können Sie eine Datei mit optionalen Argumenten angeben, die immer dann verwendet werden sollen, wenn Sie <kbd>F5</kbd> drücken. Dabei macht es keinen Unterschied, welche Datei aktuell im Editor aktiv ist.

Nachdem die Debugkonfiguration eingerichtet wurde, können Sie auswählen, welche Konfiguration Sie während einer Debugsitzung verwenden möchten. Wählen Sie eine Konfiguration aus der Dropdownliste „Debugkonfiguration“ in der Symbolleiste der Ansicht **Debuggen**.

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>Problembehandlung der PowerShell-Erweiterung für Visual Studio Code

Wenn bei der Verwendung von Visual Studio Code für die PowerShell-Skriptentwicklung Probleme auftreten, sehen Sie sich den [Leitfaden zur Problembehandlung][troubleshooting] auf GitHub an.

## <a name="useful-resources"></a>Nützliche Ressourcen

Im Folgenden sind einige Videos und Blogbeiträge aufgeführt, die bei den ersten Schritten mit der PowerShell-Erweiterung für Visual Studio Code hilfreich sein können:

### <a name="videos"></a>Videos

- [Using Visual Studio Code as Your Default PowerShell Editor](https://youtu.be/bGn45vIeAMM) (Verwenden von Visual Studio Code als PowerShell-Standard-Editor)
- [Visual Studio Code: deep dive into debugging your PowerShell scripts](https://youtu.be/cSbIXmlkr8o) (Visual Studio Code: Ausführliche Einführung in das Debuggen von PowerShell-Skripts)

### <a name="blog-posts"></a>Blogbeiträge

- [PowerShell-Erweiterung][pscdn]
- [Write and debug PowerShell scripts in Visual Studio Code (Schreiben und Debuggen von PowerShell-Skripts in Visual Studio Code)][debug]
- [Debugging Visual Studio Code Guidance (Anleitung zum Debuggen in Visual Studio Code)][psdbgblog]
- [Debugging PowerShell in Visual Studio Code (Debuggen von PowerShell in Visual Studio Code)][psdbg-gh]
- [Get started with PowerShell development in Visual Studio Code (Erste Schritte für die PowerShell-Entwicklung in Visual Studio Code)][getting-started]
- [Visual Studio Code editing features for PowerShell development – Part 1 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 1)][editing-part1]
- [Visual Studio Code editing features for PowerShell development – Part 2 (Bearbeitungsfeatures für die PowerShell-Entwicklung mit Visual Studio Code: Teil 2)][editing-part2]
- [Debugging PowerShell script in Visual Studio Code – Part 1 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 1)][debugging-part1]
- [Debugging PowerShell script in Visual Studio Code – Part 2 (Debuggen von PowerShell-Skripts in Visual Studio Code: Teil 2)][debugging-part2]

## <a name="powershell-extension-project-source-code"></a>Quellcode des PowerShell-Erweiterungsprojekts

Sie finden den Quellcode der PowerShell-Erweiterung auf [GitHub][psext-src].

Wenn Sie an diesen Inhalten mitwirken möchten, sind Pull Requests sehr willkommen. Befolgen Sie die Schritte in der [Entwicklerdokumentation auf GitHub][dev-docs], um loszulegen.

<!-- related articles -->
[ise]:                    ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[GitHub-Probleme]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
