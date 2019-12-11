---
title: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
description: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117488"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Replizieren der ISE-Benutzeroberfläche in Visual Studio Code

Obwohl die PowerShell-Erweiterung für VSCode keine vollständige Funktionsparität mit der PowerShell ISE anstrebt, gibt es Funktionen, die die VSCode-Benutzeroberfläche für Benutzer der ISE natürlicher gestalten.

Dieses Dokument versucht, Einstellungen aufzulisten, die Sie in VSCode konfigurieren können, um die Benutzerfreundlichkeit im Vergleich zur ISE etwas vertrauter zu gestalten.

## <a name="key-bindings"></a>Schlüsselbindungen

| Funktion                              | ISE-Bindung                  | VSCode-Bindung                              |
| ----------------                      | -----------                  | --------------                              |
| Unterbrechen und Pausieren des Debuggers          | <kbd>STRG</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Ausführen der aktuellen Zeile/des hervorgehobenen Texts | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Auflisten verfügbarer Codeausschnitte               | <kbd>STRG</kbd>+<kbd>J</kbd> | <kbd>STRG</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Benutzerdefinierte Schlüsselbindungen

Sie können in Visual Studio Code auch [Ihre eigenen Schlüsselbindungen konfigurieren](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings).

## <a name="simplified-ise-like-ui"></a>Vereinfachte, ISE-ähnliche Benutzeroberfläche

Wenn Sie nach einer Möglichkeit zur Vereinfachung der Visual Studio Code-Benutzeroberfläche suchen, damit diese der ISE-Benutzeroberfläche ähnelt, wenden Sie diese zwei Einstellungen an:

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

Dies führt zum Ausblenden der Aktivitätsleiste und der Seitenleiste zum Debuggen innerhalb des roten Kastens:

![Hervorgehobener Abschnitt mit Aktivitätsleiste und der Seitenleiste zum Debuggen](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

Das Endergebnis sieht so aus:

![Vereinfachte Ansicht von VS Code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Registerkartenvervollständigung

Fügen Sie die folgende Einstellung hinzu, um Vervollständigung mit der TAB-TASTE zu erzielen, die der ISE ähnlicher ist:

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Diese Einstellung wurde VSCode direkt (anstatt in der Erweiterung) hinzugefügt. Das Verhalten wird direkt von VSCode bestimmt und kann durch die Erweiterung nicht geändert werden.

## <a name="no-focus-on-console-when-executing"></a>Kein Fokus auf der Konsole bei der Ausführung

So bleibt der Fokus bei der Ausführung mit <kbd>F8</kbd> im Editor:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Der Standardwert ist aus Gründen der Barrierefreiheit `true`.

## <a name="dont-start-integrated-console-on-startup"></a>Integrierte Konsole beim Start nicht starten

Legen Sie Folgendes fest, um die integrierte Konsole beim Start zu beenden:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Der PowerShell-Hintergrundprozess wird trotzdem gestartet, da er IntelliSense, Skriptanalyse, Symbolnavigation usw. bereitstellt. Die Konsole wird aber nicht angezeigt.

## <a name="assume-files-are-powershell-by-default"></a>Standardmäßige Annahme, dass es sich um PowerShell-Dateien handelt

Um neue/unbenannte Dateien zu erstellen, registrieren Sie sie standardmäßig als PowerShell:

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a>Farbschema

Für VSCode stehen eine Reihe von ISE-Designs zur Verfügung, damit der Editor der ISE wesentlich ähnlicher sieht.

Geben Sie `theme` in der [Befehlspalette] ein, um `Preferences: Color Theme` abzurufen, und drücken Sie die <kbd>EINGABETASTE</kbd>.
Wählen Sie in der Dropdownliste `PowerShell ISE` aus.

Sie können dieses Design in den Einstellungen wie folgt festlegen:

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a>PowerShell-Befehls-Explorer

Dank der Arbeit von [@corbob](https://github.com/corbob) weist die PowerShell-Erweiterung Anfänge eines eigenen Befehls-Explorers auf.

Geben Sie `PowerShell Command Explorer` in der [Befehlspalette] ein, und drücken Sie die <kbd>EINGABETASTE</kbd>.

## <a name="open-in-the-ise"></a>Öffnen in der ISE

Wenn Sie letztendlich trotzdem eine Datei in der ISE öffnen möchten, können Sie <kbd>UMSCHALT</kbd>+<kbd>ALT</kbd>+<kbd>P</kbd> verwenden.

## <a name="other-resources"></a>Weitere Ressourcen

- 4sysops bietet [einen großartigen Artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) zur Konfiguration von VSCode, um der ISE ähnlicher zu sein.
- Mike F. Robbins hat [einen hervorragenden Beitrag](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) zum Einrichten von VSCode verfasst.
- Learn PowerShell bietet [eine ausgezeichnete Zusammenfassung](https://www.learnpwsh.com/setup-vs-code-for-powershell/) zur Einrichtung von VSCode für PowerShell.

## <a name="more-settings"></a>Weitere Einstellungen

Wenn Sie weitere Möglichkeiten kennen, wie Sie VSCode für ISE-Anwender vertrauter gestalten können, tragen Sie zu diesem Dokument bei. Wenn Sie nach einer Kompatibilitätskonfiguration suchen, aber keine Möglichkeit finden, diese zu aktivieren, [legen Sie ein Issue an](https://github.com/PowerShell/vscode-powershell/issues/new/choose), und fragen Sie nach einer Lösung!

Wir freuen uns immer über PRs und Beiträge!

## <a name="vscode-tips"></a>VSCode-Tipps

### <a name="command-palette"></a>Befehlspalette

<kbd>F1</kbd> ODER <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> unter MacOS)

Eine praktische Möglichkeit zur Ausführung von Befehlen in Visual Studio Code.
Weitere Informationen finden Sie in der [VSCode-Dokumentation](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Befehlspalette]: #command-palette
