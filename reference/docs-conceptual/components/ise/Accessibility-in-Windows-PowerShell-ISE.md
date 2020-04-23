---
ms.date: 12/19/2019
keywords: powershell,cmdlet
title: Barrierefreiheit in Windows PowerShell ISE
ms.openlocfilehash: 89eff839d69fdbd5a1fa48b61dab627ef83f751b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500965"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Barrierefreiheit in Windows PowerShell ISE

In diesen Thema werden die Barrierefreiheitsfeatures von Windows PowerShell Integrated Scripting Environment (ISE) geschrieben, die Sie ggf. hilfreich finden.

- [Ändern der Größe und Position des Konsolen- und Skriptbereichs](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [Tastenkombinationen zum Bearbeiten von Text](#keyboard-shortcuts-for-editing-text)
- [Tastenkombinationen zum Ausführen von Skripts](#keyboard-shortcuts-for-running-scripts)
- [Tastenkombinationen zum Anpassen der Ansicht](#keyboard-shortcuts-for-customizing-the-view)
- [Tastenkombinationen zum Debuggen von Skripts](#keyboard-shortcuts-for-debugging-scripts)
- [Tastenkombinationen für Windows PowerShell-Registerkarten](#keyboard-shortcuts-for-windows-powershell-tabs)
- [Tastenkombinationen für Starten und Beenden](#keyboard-shortcuts-for-starting-and-exiting)
- [Haltepunktverwaltung mit Cmdlets](#breakpoint-management)

Microsoft ist bestrebt, seine Produkte und Dienste so benutzerfreundlich wie möglich zu gestalten. In den folgenden Abschnitten werden Informationen zu den Funktionen, Produkten und Dienstleistungen vermittelt, mit deren Hilfe Personen mit Behinderungen der Zugriff auf Windows PowerShell ISE erleichtert wird.

Neben den Barrierefreiheitsfeatures und Hilfsprogrammen von Microsoft Windows sorgen die folgenden Windows PowerShell ISE-Features für Personen mit Behinderungen für mehr Barrierefreiheit:

- Tastenkombinationen

- Syntaxfarbtabelle und Möglichkeit des Änderns anderer Farbeinstellungen mithilfe des Skripterstellungsobjekts [$psISE.Options](object-model/The-ISEOptions-Object.md)

- Änderung der Textgröße

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Ändern der Größe und Position des Konsolen- und Skriptbereichs

Sie können über die folgenden Schritte die Größe und Position des Konsolen- und Skriptbereichs ändern. Die vorgenommenen Größen- und Positionsänderungen werden beibehalten, wenn Sie Windows PowerShell ISE erneut öffnen.

### <a name="to-resize-the-script-pane-and-console-pane"></a>So ändern Sie Größe des Skript- und Konsolenbereichs

1. Setzen Sie den Mauszeiger auf die Trennlinie zwischen Skript- und Konsolenbereich.

2. Wenn sich der Mauszeiger in einen Pfeil mit zwei Spitzen ändert, ziehen Sie den Rand zum Ändern der Größe des Bereichs.

### <a name="to-move-the-script-pane-and-console-pane"></a>So verschieben Sie den Skript- und Konsolenbereich

Führen Sie eines der folgenden Verfahren aus:

- Drücken Sie zum Verschieben des Skriptbereichs über den Konsolenbereich <kbd>STRG</kbd>+<kbd>1</kbd>. Alternativ können Sie auf der Symbolleiste auf das Symbol **Skriptbereich oben anzeigen** oder im Menü **Ansicht** auf **Skriptbereich oben anzeigen** klicken.

- Drücken Sie zum Verschieben des Skriptbereichs rechts neben den Konsolenbereich <kbd>STRG</kbd>+<kbd>2</kbd>. Alternativ können Sie auf der Symbolleiste auf das Symbol **Skriptbereich rechts anzeigen** oder im Menü **Ansicht** auf **Skriptbereich rechts anzeigen** klicken.

- Drücken Sie zum Maximieren des Skriptbereichs <kbd>STRG</kbd>+<kbd>3</kbd>. Alternativ können Sie auf der Symbolleiste auf das Symbol **Skriptbereich maximiert anzeigen** oder im Menü **Ansicht** auf **Skriptbereich maximiert anzeigen** klicken.

- Klicken Sie zum Maximieren des Konsolenbereichs und Ausblenden des Skriptbereich ganz rechts in der Reihe der Registerkarten auf das Symbol **Skriptbereich ausblenden**. Oder deaktivieren Sie im Menü **Ansicht** die Option **Skriptbereich anzeigen**.

- Klicken Sie Anzeigen des Skriptbereichs, wenn der Konsolenbereich maximiert ist, ganz rechts in der Reihe der Registerkarten auf das Symbol **Skriptbereich anzeigen**. Oder aktivieren Sie im Menü **Ansicht** die Option **Skriptbereich anzeigen**.

## <a name="keyboard-shortcuts-for-editing-text"></a>Tastenkombinationen zum Bearbeiten von Text

Sie können die folgenden Tastenkombinationen verwenden, wenn Sie Text bearbeiten.

|           Aktion            |       Tastenkombinationen       |          Verwenden in           |
| --------------------------- | ------------------------------ | ------------------------- |
| **Copy**                    | <kbd>STRG</kbd>+<kbd>C</kbd>   | Skriptbereich, Konsolenbereich |
| **Ausschneiden**                     | <kbd>STRG</kbd>+<kbd>X</kbd>   | Skriptbereich, Konsolenbereich |
| **Im Skript suchen**          | <kbd>STRG</kbd>+<kbd>F</kbd>   | Skriptbereich               |
| **Im Skript weitersuchen**     | <kbd>F3</kbd>                  | Skriptbereich               |
| **Vorheriges im Skript suchen** | <kbd>UMSCHALT</kbd>+<kbd>F3</kbd> | Skriptbereich               |
| **Einfügen**                   | <kbd>STRG</kbd>+<kbd>V</kbd>   | Skriptbereich, Konsolenbereich |
| **Wiederholen**                    | <kbd>STRG</kbd>+<kbd>Y</kbd>   | Skriptbereich, Konsolenbereich |
| **Im Skript ersetzen**       | <kbd>STRG</kbd>+<kbd>H</kbd>   | Skriptbereich               |
| **Speichern**                    | <kbd>STRG</kbd>+<kbd>S</kbd>   | Skriptbereich               |
| **Alles markieren**              | <kbd>STRG</kbd>+<kbd>A</kbd>   | Skriptbereich, Konsolenbereich |
| **Rückgängig**                    | <kbd>STRG</kbd>+<kbd>Z</kbd>   | Skriptbereich, Konsolenbereich |

## <a name="keyboard-shortcuts-for-running-scripts"></a>Tastenkombinationen zum Ausführen von Skripts

Sie können die folgenden Tastenkombinationen verwenden, wenn Sie Skripts im Skriptbereich ausführen.

|            Aktion            |                                                                                                     Tastenkombination                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Neu**                      | <kbd>STRG</kbd>+<kbd>N</kbd>                                                                                                                                                                                               |
| **Öffnen**                     | <kbd>STRG</kbd>+<kbd>O</kbd>                                                                                                                                                                                               |
| **Ausführen**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **Auswahl ausführen**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **Vorgang beenden**           | <kbd>STRG</kbd>+<kbd>UNTBR</kbd> <kbd>STRG</kbd>+<kbd>C</kbd> kann verwendet werden, wenn der Kontext eindeutig ist (und kein Text ausgewählt wurde).                                                                               |
| **Registerkarte** (zum nächsten Skript)     | <kbd>STRG</kbd>+<kbd>TAB</kbd> **Hinweis:** Mit dieser Kombination zum nächsten Skript wechseln funktioniert nur, wenn Sie eine einzige PowerShell-Registerkarte geöffnet haben, oder wenn Sie mehrere PowerShell-Registerkarten geöffnet haben und sich der Fokus im Skriptbereich befindet.                |
| **Registerkarte** (zum vorherigen Skript) | <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>TAB</kbd> **Hinweis:** Mit dieser Kombination zum vorherigen Skript wechseln funktioniert nur, wenn Sie eine einzige PowerShell-Registerkarte geöffnet haben, oder wenn Sie mehrere PowerShell-Registerkarten geöffnet haben und sich der Fokus im Skriptbereich befindet. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Tastenkombinationen zum Anpassen der Ansicht

Sie können die folgenden Tastenkombinationen verwenden, um die Ansicht in Windows PowerShell ISE anzupassen. Diese Tastenkombinationen sind in allen Bereichen in der Anwendung wirksam.

|           Aktion           |         Tastenkombination        |
| -------------------------- | -------------------------------- |
| **Zur Konsole wechseln**     | <kbd>STRG</kbd>+<kbd>D</kbd>     |
| **Zum Skriptbereich gehen**      | <kbd>STRG</kbd>+<kbd>I</kbd>     |
| **Skriptbereich anzeigen**       | <kbd>STRG</kbd>+<kbd>R</kbd>     |
| **Skriptbereich ausblenden**       | <kbd>STRG</kbd>+<kbd>R</kbd>     |
| **Skriptbereich nach oben verschieben**    | <kbd>STRG</kbd>+<kbd>1</kbd>     |
| **Skriptbereich nach rechts verschieben** | <kbd>STRG</kbd>+<kbd>2</kbd>     |
| **Skriptbereich maximiert anzeigen**   | <kbd>STRG</kbd>+<kbd>3</kbd>     |
| **Vergrößern**                | <kbd>STRG</kbd>+<kbd>PLUSZEICHEN</kbd>  |
| **Verkleinern**               | <kbd>STRG</kbd>+<kbd>MINUSZEICHEN</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Tastenkombinationen zum Debuggen von Skripts

Sie können die folgenden Tastenkombinationen verwenden, wenn Sie Skripts debuggen.

|           Aktion           |               Tastenkombination                |                Verwenden in                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **Ausführen/Fortsetzen**           | <kbd>F5</kbd>                                  | Skriptbereich beim Debuggen eines Skripts |
| **Einzelschritt**              | <kbd>F11</kbd>                                 | Skriptbereich beim Debuggen eines Skripts |
| **Überspringen**              | <kbd>F10</kbd>                                 | Skriptbereich beim Debuggen eines Skripts |
| **Rücksprung**               | <kbd>UMSCHALT</kbd>+<kbd>F11</kbd>                | Skriptbereich beim Debuggen eines Skripts |
| **Aufrufliste anzeigen**     | <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>D</kbd>  | Skriptbereich beim Debuggen eines Skripts |
| **Haltepunkte auflisten**       | <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>L</kbd>  | Skriptbereich beim Debuggen eines Skripts |
| **Haltepunkt umschalten**      | <kbd>F9</kbd>                                  | Skriptbereich beim Debuggen eines Skripts |
| **Alle Haltepunkte entfernen** | <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>F9</kbd> | Skriptbereich beim Debuggen eines Skripts |
| **Debugger beenden**          | <kbd>UMSCHALT</kbd>+<kbd>F5</kbd>                 | Skriptbereich beim Debuggen eines Skripts |

> [!NOTE]
> Sie können beim Debuggen von Skripts in der Windows PowerShell ISE auch die Tastenkombinationen verwenden, die für die Windows PowerShell-Konsole vorgesehen sind. Um diese Tastenkombinationen zu verwenden, müssen Sie die jeweilige Kombination im Konsolenbereich eingeben und die <kbd>EINGABETASTE</kbd> drücken.

|                 Aktion                  |      Tastenkombination       |                Verwenden in                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **Fortsetzen**                            | <kbd>C</kbd>                 | Konsolenbereich, wenn ein Skript debuggt wird |
| **Einzelschritt**                           | <kbd>S</kbd>                 | Konsolenbereich, wenn ein Skript debuggt wird |
| **Überspringen**                           | <kbd>B</kbd>                 | Konsolenbereich, wenn ein Skript debuggt wird |
| **Rücksprung**                            | <kbd>O</kbd>                 | Konsolenbereich, wenn ein Skript debuggt wird |
| **Letzten Befehl wiederholen**(Einzelschritt/Überspringen) | <kbd>EINGABETASTE</kbd>             | Konsolenbereich, wenn ein Skript debuggt wird |
| **Aufrufliste anzeigen**                  | <kbd>K</kbd>                 | Konsolenbereich, wenn ein Skript debuggt wird |
| **Debuggen beenden**                      | <kbd>Q</kbd>                 | Konsolenbereich, wenn ein Skript debuggt wird |
| **Das Skript auflisten**                     | <kbd>L</kbd>                 | Konsolenbereich, wenn ein Skript debuggt wird |
| **Konsolendebugbefehle anzeigen**  | <kbd>H</kbd> oder <kbd>?</kbd> | Konsolenbereich, wenn ein Skript debuggt wird |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Tastenkombinationen für Windows PowerShell-Registerkarten

Sie können die folgenden Tastenkombinationen verwenden, wenn Sie Windows PowerShell-Registerkarten verwenden.

|             Aktion              |                                 Tastenkombination                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **PowerShell-Registerkarte schließen**        | <kbd>STRG</kbd>+<kbd>W</kbd>                                                       |
| **Neue PowerShell-Registerkarte**          | <kbd>STRG</kbd>+<kbd>T</kbd>                                                       |
| **Vorherige PowerShell-Registerkarte**     | <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>TAB</kbd> (Funktioniert nur, wenn keine Dateien in einer der PowerShell-Registerkarten geöffnet sind) |
| **Nächste Windows PowerShell-Registerkarte** | <kbd>STRG</kbd>+<kbd>TAB</kbd> (Funktioniert nur, wenn keine Dateien in einer der PowerShell-Registerkarten geöffnet sind) |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Tastenkombinationen für Starten und Beenden

Sie können die folgenden Tastenkombinationen verwenden, um die Windows PowerShell-Konsole (**PowerShell.exe**) zu starten oder Windows PowerShell ISE zu beenden.

|                        Aktion                         |               Tastenkombination               |
| ----------------------------------------------------- | --------------------------------------------- |
| **Beenden**                                              | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **PowerShell.exe starten** (Windows PowerShell-Konsole) | <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd> |

## <a name="breakpoint-management"></a>Haltepunktverwaltung

Für Sehbehinderte stehen Haltepunktinformationen über die Cmdlets zum Verwalten von Haltepunkten zur Verfügung, wie z. B. [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) und [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint). Weitere Informationen finden Sie unter „Verwalten von Haltepunkten“ in [Debuggen von Skripts in der Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md).

## <a name="see-also"></a>Weitere Informationen

[Einführung in die Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
