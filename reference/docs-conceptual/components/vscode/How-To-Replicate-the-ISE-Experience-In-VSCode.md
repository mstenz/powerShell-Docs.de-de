---
title: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
description: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012482"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Replizieren der ISE-Benutzeroberfläche in Visual Studio Code

Während die PowerShell-Erweiterung für VSCode vollständige Funktionsparität mit der PowerShell ISE seek nicht, gibt es Features direkt auf die VSCode-Erfahrung für Benutzer von ISE natürlicher zu machen.

Dieses Dokument versucht, listeneinstellungen, die Sie in Visual Studio Code, um die benutzerfreundlichkeit ein wenig mehr vertraut, die im Vergleich zu der ISE machen konfigurieren können.

## <a name="key-bindings"></a>Tastenzuordnungen

| Funktion                              | ISE-Bindung                  | VSCode-Bindung                              |
| ----------------                      | -----------                  | --------------                              |
| Unterbrechen und das Unterbrechen des Debuggers          | <kbd>STRG</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Führen Sie die aktuelle Zeile/hervorgehobener text | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Liste verfügbaren Ausschnitte               | <kbd>STRG</kbd>+<kbd>J</kbd> | <kbd>STRG</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Benutzerdefinierte Schlüssel-Bindungen

Sie können [konfigurieren Sie Ihre eigenen tastenzuordnungen](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in Visual Studio Code auch.

## <a name="tab-completion"></a>Registerkartenvervollständigung

Um mehr ISE-ähnliche befehlszeilenergänzung zu aktivieren, fügen Sie diese Einstellung aus:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Diese Einstellung wurde direkt in VSCode (statt in der Erweiterung) hinzugefügt. Das Verhalten wird direkt von VSCode bestimmt und kann nicht geändert werden, von der Erweiterung.

## <a name="no-focus-on-console-when-executing"></a>Ohne Fokus auf die Konsole beim Ausführen

Zu den Fokus im Editor, beim Ausführen von mit <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Der Standardwert ist `true` aus Gründen der Barrierefreiheit.

## <a name="dont-start-integrated-console-on-startup"></a>Integrierte Konsole kann beim Start nicht gestartet

Um die integrierte Konsole beim Start zu beenden, legen Sie Folgendes fest:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Hintergrund PowerShell-Prozess startet immer noch da, IntelliSense, Skript-Analyse, symbolnavigation usw. bereitstellt. Aber die Konsole wird nicht angezeigt werden.

## <a name="assume-files-are-powershell-by-default"></a>Wird davon ausgegangen Sie, dass Dateien mit PowerShell in der Standardeinstellung sind

Um neue/unbenannte Dateien zu machen, registrieren Sie standardmäßig als PowerShell:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Farbschema

Eine Anzahl von ISE Designs stehen zur Verfügung, für VSCode, um den Editor, suchen Sie die ISE eher zu machen.

In der [Befehlspalette] Typ `theme` abzurufenden `Preferences: Color Theme` , und drücken Sie <kbd>EINGABETASTE</kbd>.
Wählen Sie in der Dropdown-Liste `PowerShell ISE`.

Sie können dieses Design in den Einstellungen mit festlegen:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>PowerShell-Befehl-Explorer

Dank der Arbeit der [ @corbob ](https://github.com/corbob), die PowerShell-Erweiterung verfügt über die Anfänge von eigenen Befehl-Explorer.

In der [Befehlspalette], geben Sie `PowerShell Command Explorer` , und drücken Sie <kbd>EINGABETASTE</kbd>.

## <a name="open-in-the-ise"></a>In der ISE öffnen

Wenn Sie am Ende eine Datei trotzdem in der ISE öffnen möchten, können Sie <kbd>UMSCHALT</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Weitere Ressourcen

- 4sysops hat [ein großartiger Artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) zum Konfigurieren von VSCode genauer wie der ISE.
- Mike F Robbins hat [einen hervorragenden Beitrag](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) zum Einrichten von VSCode.
- Erfahren Sie mehr PowerShell verfügt über [eine ausgezeichnete schreiben Sie](https://www.learnpwsh.com/setup-vs-code-for-powershell/) richten Sie zum Abrufen von VSCode für PowerShell.

## <a name="more-settings"></a>Weitere Einstellungen

Wenn Sie weitere Informationen zum Stellen von VSCode für ISE Benutzer mehr vertraut sein kennen, tragen Sie zu diesem Dokument. Wenn eine Anwendungskompatibilitäts-Konfiguration, die Sie suchen vorliegt, aber keinesfalls zu seiner Aktivierung nicht auffindbar [eröffnen Sie ein Problem](https://github.com/PowerShell/vscode-powershell/issues/new/choose) und stellen Sie Ihre Fragen!

Wir freuen uns immer zum Akzeptieren von PRs und Beiträge auch!

## <a name="vscode-tips"></a>VSCode-Tipps

### <a name="command-palette"></a>Befehlspalette

<kbd>F1</kbd> oder <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Shift</kbd>+<kbd>P</kbd> unter MacOS)

Eine praktische Möglichkeit der Ausführung von Befehlen in Visual Studio Code.
Weitere Informationen finden Sie unter [VSCode Dokumentation](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Befehlspalette]: #command-palette
