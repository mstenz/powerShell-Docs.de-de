---
title: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
description: Replizieren der ISE-Benutzeroberfläche in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 899e1c393fd49b0659631b88d610e80ec885e69e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81005600"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Replizieren der ISE-Benutzeroberfläche in Visual Studio Code

Obwohl die PowerShell-Erweiterung für VS Code keine vollständige Funktionsparität mit der PowerShell ISE anstrebt, gibt es Funktionen, die die VS Code-Benutzeroberfläche für Benutzer der ISE natürlicher gestalten.

In diesem Dokument sind Einstellungen aufgeführt, die Sie in VS Code konfigurieren können, um die Benutzerfreundlichkeit im Vergleich zur ISE etwas vertrauter zu gestalten.

## <a name="ise-mode"></a>ISE-Modus

> [!NOTE]
> Dieses Feature ist in der PowerShell Preview-Erweiterung seit Version 2019.12.0 und in der PowerShell-Erweiterung seit Version 2020.3.0 verfügbar.

Die einfachste Möglichkeit zum Replizieren der ISE-Benutzeroberfläche in Visual Studio Code ist das Aktivieren des ISE-Modus.
Öffnen Sie hierzu die Befehlspalette (<kbd>F1</kbd> oder <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> oder <kbd>BEFEHLSTASTE</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> unter macOS), und geben Sie „ISE-Modus“ ein. Wählen Sie in der Liste „PowerShell: ISE-Modus aktivieren“ aus.

Mit diesem Befehl werden die unten beschriebenen Einstellungen automatisch angewendet. Das Ergebnis sieht wie folgt aus:

![ISE-Modus](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a>ISE-Modus-Konfigurationseinstellungen

Der ISE-Modus nimmt die folgenden Änderungen an den VS Code-Einstellungen vor.

- Schlüsselbindungen

  |               Funktion                |         ISE-Bindung          |              VS Code-Bindung                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | Unterbrechen und Pausieren des Debuggers          | <kbd>STRG</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
  | Ausführen der aktuellen Zeile/des hervorgehobenen Texts | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
  | Auflisten verfügbarer Codeausschnitte               | <kbd>STRG</kbd>+<kbd>J</kbd> | <kbd>STRG</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

  > [!NOTE]
  > Sie können in VS Code auch [Ihre eigenen Schlüsselbindungen konfigurieren](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings).

- Vereinfachte, ISE-ähnliche Benutzeroberfläche

  Wenn Sie nach einer Möglichkeit zur Vereinfachung der Visual Studio Code-Benutzeroberfläche suchen, damit diese der ISE-Benutzeroberfläche ähnelt, wenden Sie diese zwei Einstellungen an:

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  Durch diese Einstellungen werden die Aktivitätsleiste und die Seitenleiste zum Debuggen innerhalb des unten gezeigten roten Kastens verborgen:

  ![Hervorgehobener Abschnitt mit Aktivitätsleiste und der Seitenleiste zum Debuggen](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  Das Endergebnis sieht so aus:

  ![Vereinfachte Ansicht von VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- Registerkartenvervollständigung

  Fügen Sie die folgende Einstellung hinzu, um Vervollständigung mit der TAB-TASTE zu erzielen, die der ISE ähnlicher ist:

  ```json
  "editor.tabCompletion": "on",
  ```

- Kein Fokus auf der Konsole beim Ausführen

  So bleibt der Fokus bei der Ausführung mit <kbd>F8</kbd> im Editor:

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  Der Standardwert lautet aus Gründen der Barrierefreiheit `true`.

- Integrierte Konsole beim Start nicht starten

  Legen Sie Folgendes fest, um die integrierte Konsole beim Start zu beenden:

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > Der PowerShell-Hintergrundprozess stellt dennoch IntelliSense, Skriptanalyse, Symbolnavigation usw. bereit. Die Konsole wird jedoch nicht angezeigt.

- Standardmäßige Annahme, dass es sich um PowerShell-Dateien handelt

  Um neue/unbenannte Dateien zu erstellen, registrieren Sie sie standardmäßig als PowerShell:

  ```json
  "files.defaultLanguage": "powershell",
  ```

- Farbschema

  Für VS Code stehen eine Reihe von ISE-Designs zur Verfügung, damit die Darstellung des Editors deutlich mehr der ISE ähnelt.

  Geben Sie `theme` in der [Befehlspalette][] ein, um `Preferences: Color Theme` abzurufen, und drücken Sie die <kbd>EINGABETASTE</kbd>. Wählen Sie in der Dropdownliste `PowerShell ISE` aus.

  Sie können dieses Design in den Einstellungen wie folgt festlegen:

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- PowerShell-Befehls-Explorer

  Dank der Arbeit von [@corbob](https://github.com/corbob) weist die PowerShell-Erweiterung Anfänge eines eigenen Befehls-Explorers auf.

  Geben Sie `PowerShell Command Explorer` in der [Befehlspalette][] ein, und drücken Sie die <kbd>EINGABETASTE</kbd>.

- Öffnen in der ISE

  Wenn Sie dennoch eine Datei in der Windows PowerShell ISE öffnen möchten, öffnen Sie die [Befehlspalette][], suchen Sie nach „in ISE öffnen“, und wählen Sie **PowerShell: aktuelle Datei in PowerShell ISE öffnen** aus.

## <a name="other-resources"></a>Weitere Ressourcen

- 4sysops bietet [einen großartigen Artikel][4sysops] zur Konfiguration von VS Code, um der ISE ähnlicher zu sein.
- Mike F. Robbins hat [einen hervorragenden Beitrag][mikefrobbins] zum Einrichten von VS Code verfasst.
- Learn PowerShell bietet [eine ausgezeichnete Zusammenfassung][learnpwsh] zur Einrichtung für PowerShell.

## <a name="vs-code-tips"></a>Tipps für VS Code

- Befehlspalette

  Die Befehlspalette ist ein äußerst nützliches Tool zum Ausführen von Befehlen in VS Code. Unter macOS öffnen Sie die Befehlspalette über <kbd>F1</kbd> oder <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> oder <kbd>BEFEHLSTASTE</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>.

  Weitere Informationen finden Sie in der [Dokumentation zu VS Code][vsc-docs].

- Deaktivieren der Debugging-Konsole

  Wenn Sie VS Code für die PowerShell-Skripterstellung verwenden möchten, können Sie die **Debugging-Konsole** deaktivieren (sie wird nicht von der PowerShell-Erweiterung verwendet). Klicken Sie dazu mit der rechten Maustaste auf **Debugging-Konsole**, und klicken Sie dann auf das Häkchen zum Ausblenden der Konsole.

## <a name="more-settings"></a>Weitere Einstellungen

Wenn Sie weitere Möglichkeiten kennen, wie Sie VS Code für ISE-Benutzer vertrauter gestalten können, tragen Sie zu diesem Dokument bei. Wenn Sie nach einer Kompatibilitätskonfiguration suchen, aber keine Möglichkeit finden, diese zu aktivieren, [Problem erstellen][], und fragen Sie nach einer Lösung!

Wir freuen uns immer über PRs und Beiträge!

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Befehlspalette]: #vs-code-tips
[Problem erstellen]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
