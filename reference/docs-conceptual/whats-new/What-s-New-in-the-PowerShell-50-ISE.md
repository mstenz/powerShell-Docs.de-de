---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: Neuigkeiten bei PowerShell 5.0 ISE
ms.openlocfilehash: 8f15e99c5a6ae33aeae9bd33eb0cf58fb27e3b90
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416646"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Neuigkeiten bei Windows PowerShell 5.0 ISE

In diesem Thema werden die neuen und aktualisierten Features vorgestellt, die in Version 5.0 der Windows PowerShell Integrated Scripting Environment (ISE) eingeführt wurden.

> [!NOTE]
> Die PowerShell ISE befindet sich nicht mehr in der aktiven Featureentwicklung. Als in Windows enthaltene Komponente wird sie weiterhin offiziell mit Sicherheits- und Wartungsfixes hoher Priorität unterstützt.
> Zurzeit ist es nicht geplant, die ISE aus Windows zu entfernen.
>
> Es besteht keine Unterstützung für die ISE in PowerShell v6 oder höher. Benutzer, die einen Ersatz für die ISE suchen, sollten [Visual Studio Code](https://code.visualstudio.com/) mit der [PowerShell-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell) verwenden.

## <a name="feature-description"></a>Featurebeschreibung

Die Windows PowerShell ISE ist eine Hostanwendung, die es Ihnen ermöglicht, Skripts und Module in einer grafischen und intuitiven Umgebung zu schreiben, auszuführen und zu testen. Wichtige Features wie farbliche Syntaxkennzeichnung, Vervollständigung mit der TAB-Taste, visuelles Debuggen, Unicode-Kompatibilität und kontextbezogene Hilfe ermöglichen eine komfortable Skripterstellung.

Weitere Informationen finden Sie unter [Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).

Die folgende Tabelle enthält die neuen und geänderten Funktionen für diese Version von Windows PowerShell ISE in Windows PowerShell.

## <a name="intellisense"></a>IntelliSense

> In ISE 3.0 hinzugefügt

IntelliSense ist ein Feature für die automatische Vervollständigung, das zur Windows PowerShell ISE gehört.
IntelliSense zeigt während der Eingabe klickbare Menüs möglicherweise übereinstimmender Cmdlets, Parameter, Parameterwerte, Dateien oder Ordner an.

**Welchen Nutzen bietet diese Änderung?**

Durch Hinzufügen von IntelliSense ist es einfacher, Cmdlets und Syntax zu ermitteln, wenn Sie die Windows PowerShell ISE zum Erstellen von Skripts nutzen. Sie können mithilfe von Windows PowerShell ISE auch Windows PowerShell erlernen, während Sie neue Skripts erstellen.

**Worin bestehen die Unterschiede?**

Bei Eingabe von Cmdlets in die Windows PowerShell ISE wird ein scrollfähiges und klickbares Menü angezeigt, das Ihnen das Durchsuchen und Auswählen der entsprechenden Befehle ermöglicht.

## <a name="snippets"></a>Codeausschnitte

> In ISE 3.0 hinzugefügt

*Codeausschnitte* sind kurze Abschnitte von Windows PowerShell-Code, die Sie in die in Windows PowerShell ISE erstellten Skripts einfügen können. Windows PowerShell ISE bietet einen Standardsatz von Codeausschnitten. Beim Arbeiten in der Windows PowerShell ISE können Sie Codeausschnitte mithilfe des Cmdlets `New-Snippet` hinzufügen.

**Welchen Nutzen bietet diese Änderung?**

Mithilfe von Codeausschnitten können Sie Skripts zum Automatisieren Ihrer Umgebung schnell zusammenstellen und erstellen.

**Worin bestehen die Unterschiede?**

Klicken Sie zum Verwenden von Codeausschnitten in Windows PowerShell 3.0 oder höher im Menü **Bearbeiten** auf **Codeausschnitte starten**, oder drücken Sie <kbd>STRG</kbd>+<kbd>J</kbd>.

## <a name="add-on-tools"></a>Add-On-Tools

> In PowerShell 3.0 hinzugefügt

Windows PowerShell ISE unterstützt jetzt Add-On-Tools, die das Objektmodell verwenden. Diese Add-Ons sind Windows Presentation Foundation-Steuerelemente (WPF), die in der Konsole als vertikaler oder horizontaler Bereich angezeigt werden. Mehrere Add-On-Tools in einem Bereich werden als Registerkarten-Steuerelement angezeigt. Sie können auch Add-On-Tools von anderen Anbietern als Microsoft hinzufügen oder entfernen. Weitere Informationen finden Sie unter [Zweck des Windows PowerShell ISE-Skriptobjektmodells](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).

**Welchen Nutzen bietet diese Änderung?**

Add-Ons ermöglichen Ihnen das Erweitern und Anpassen der Windows PowerShell ISE mit Tools, die die Funktionalität erweitern und Ihre Skripterstellungsumgebung verbessern.

**Worin bestehen die Unterschiede?**

Zum Funktionsumfang der Windows PowerShell ISE 3.0 und höher gehört das Add-On **Befehle**. Das Add-On **Befehle** ermöglicht das Durchsuchen von Cmdlets und das Zugreifen auf die Hilfe zu den Cmdlets. Es wird neben den Bereichen **Skript** und **Konsole** angezeigt.

Zusätzliche Add-Ons finden Sie über den Befehl **Website mit Add-On-Tools öffnen** im Menü**Add-Ons**.

## <a name="restart-manager-and-auto-save"></a>Neustart-Manager und automatisches Speichern

> In PowerShell 3.0 hinzugefügt

Windows PowerShell ISE speichert nun Ihre geöffneten Skripts automatisch alle zwei Minuten an einem gesonderten Speicherort. Wenn Windows PowerShell ISE nach einem unerwarteten Absturz oder geplant neu startet, werden die in der letzten Sitzung geöffneten Skripts auch dann wiederhergestellt, wenn die Skripts nicht gespeichert wurden.

Führen Sie im Konsolenbereich den folgenden Befehl aus, um das Intervall für die automatische Speicherung zu ändern: `$psise.Options.AutoSaveMinuteInterval`.

**Welchen Nutzen bietet diese Änderung?**

Sie können jetzt mit Windows PowerShell ISE mit dem Wissen arbeiten, dass Ihre geöffneten Skripts automatisch gespeichert werden.

**Worin bestehen die Unterschiede?**

In Windows PowerShell ISE 2.0 werden die Skripts nicht automatisch gespeichert.

## <a name="most-recently-used-list"></a>Liste „Zuletzt verwendet“

> In PowerShell 3.0 hinzugefügt

Die Windows PowerShell ISE bietet jetzt eine Liste der zuletzt verwendeten Dateien. Beim Öffnen einer Datei in der Windows PowerShell ISE wird die Datei der Liste „Zuletzt verwendet“ im Menü **Datei** hinzugefügt.

Führen Sie im Konsolenbereich den folgenden Befehl aus, um die Standardanzahl von Dateien in der Liste „Zuletzt verwendet“ zu ändern: `$psise.Options.MruCount`.

**Welchen Nutzen bietet diese Änderung?**

Über die Liste „Zuletzt verwendet“ können Sie nun mühelos auf die zuletzt verwendeten Dateien zugreifen.

**Worin bestehen die Unterschiede?**

Die Windows PowerShell ISE 2.0 bietet keine solche Liste.

## <a name="console-pane"></a>Konsolenbereich

> In PowerShell 3.0 hinzugefügt

Die separaten Befehls- und Ausgabebereiche, die in der ersten Version der Windows PowerShell ISE verfügbar waren, wurden in einem Konsolenbereich kombiniert. Von der Funktion und Darstellung ähnelt der Konsolenbereich einer typischen Windows PowerShell-Konsole, er bietet aber die im Folgenden aufgeführten Erweiterungen:

- Syntaxfarben für Eingabetext (nicht für Ausgabetext), einschließlich XML-Syntax
- IntelliSense
- Zugehörige Klammer
- Fehleranzeige
- Vollständige Unicode-Unterstützung
- Kontextbezogene Hilfe über <kbd>F1</kbd>
- Kontextbezogene Befehlsanzeige (Show-Command) über <kbd>STRG</kbd>+<kbd>F1</kbd>
- Unterstützung für komplexe Skripts und Sprachen mit Leserichtung von rechts nach links
- Schriftartenunterstützung
- Zoom
- Modi für Linien- und Blockauswahl
- Beibehaltung von über die Befehlszeile eingegebenem Inhalt, wenn Sie mithilfe der <kbd>NACH-OBEN-TASTE</kbd> den Verlauf in der Konsole anzeigen

**Welchen Nutzen bietet diese Änderung?**

Diese Änderungen im Konsolenbereich ermöglichen eine Skripterstellungsumgebung, die mit der Konsolenschnittstelle konsistenter ist.

**Worin bestehen die Unterschiede?**

Die Windows PowerShell ISE 2.0 verfügt über getrennte Befehls- und Ausgabebereiche.

## <a name="command-line-switches"></a>Befehlszeilenschalter

> In PowerShell 3.0 hinzugefügt

Wenn Sie die Windows PowerShell ISE über die Befehlszeile starten (indem Sie **powershell_ise.exe** eingeben), können Sie die folgenden neuen Befehlszeilenschalter hinzufügen.

- `-NoProfile`: Startet die Windows PowerShell ISE ohne Ausführung von `$profile`
- `-Help`: Zeigt ein Hilfefenster an.
- `-mta`: Startet die Windows PowerShell ISE im Multithread-Apartment-Modus Der Standardbetriebsmodus der Windows PowerShell ISE ist der Singlethread-Apartment-Modus bzw. `-sta`.

**Welchen Nutzen bietet diese Änderung?**

Das Hinzufügen dieser Befehlszeilenschalter ermöglicht Ihnen das Steuern der Umgebung, in der die Windows PowerShell ISE ausgeführt wird.

**Worin bestehen die Unterschiede?**

Die Windows PowerShell ISE 2.0 erkennt diese Befehlszeilenschalter nicht.

## <a name="new-editor-features"></a>Neue Features im Editor

> In PowerShell 3.0 hinzugefügt

Zu den weiteren Windows PowerShell ISE-Bearbeitungsfeatures zählen:

- **XML-Syntaxfarben**: Windows PowerShell ISE versieht die XML-Syntax jetzt ebenso mit Farben wie die Windows PowerShell-Syntax.
- **Zugehörige Klammer**: Die Windows PowerShell ISE bietet die Funktion „Zugehörige Klammer (Hervorhebung)“, die wie folgt verwendet werden kann: Wenn Sie z. B. den Befehl **Gehe zu Spiel** bzw. <kbd>STRG</kbd>+<kbd>]</kbd> verwenden, wird die schließende Klammer gefunden, wenn eine öffnende Klammer ausgewählt ist.
- **Gliederungsansicht** Der Skriptbereich unterstützt Gliederungen, sodass Codeabschnitte durch Klicken auf Plus- bzw. Minuszeichen am linken Rand auf- bzw. zugeklappt werden können. Sie können Klammern bzw. die Tags `#region` und `#endregion` verwenden, um den Anfang bzw. das Ende eines zuklappbaren Abschnitts zu markieren. Drücken Sie zum Auf- bzw. Zuklappen aller Bereiche <kbd>STRG</kbd>+<kbd>M</kbd>.
- **Textbearbeitung mit Drag & Drop**: Windows PowerShell ISE unterstützt nun die Textbearbeitung mit Drag & Drop. Sie können einen beliebigen Textblock auswählen und an eine andere Stelle im Editor oder in der Konsole ziehen, um den Text zu verschieben. Wenn Sie die <kbd>STRG</kbd>-Taste gedrückt halten, während Sie den markierten Text ziehen, wird der Text, sobald Sie die Maustaste loslassen, an den neuen Ort kopiert. In dieser Version von Windows PowerShell ISE wird beim Ziehen und Ablegen von Dateien auf Windows PowerShell ISE die Datei von Windows PowerShell ISE geöffnet.
- **Anzeige von Analysefehlern**: Analysefehler werden rot unterstrichen angezeigt. Wenn Sie auf einen Fehler zeigen, wird das im Code gefundene Problem als QuickInfo angezeigt.
- **Zoom**: Der Zoomprozentsatz des Konsoleninhalts kann mit einem Zoomschieberegler (rechts unten im Fenster der Windows PowerShell ISE) oder durch Eingabe des Befehls `$psise.options.Zoom` im Konsolenbereich festgelegt werden.
- **Umfassende Funktionen zum Kopieren und Einfügen von Text**: Beim Kopieren in die Zwischenablage in Windows PowerShell ISE bleiben Informationen zur Schriftart, Größe und Farbe der ursprünglichen Auswahl erhalten.
- **Blockauswahl**: Sie können einen Textblock auswählen, indem Sie bei gedrückter <kbd>ALT</kbd>-TASTE den Text im Skriptbereich mit der Maus auswählen, oder indem Sie <kbd>ALT</kbd>+<kbd>UMSCHALT</kbd>+<kbd>NACH-OBEN/NACH-UNTEN</kbd> drücken.

**Welchen Nutzen bietet diese Änderung?**

Die zusätzlichen Bearbeitungsfeatures bieten eine konsistentere und leistungsstärkere Bearbeitungsumgebung.

**Worin bestehen die Unterschiede?**

In Windows PowerShell ISE 2.0 waren diese Bearbeitungsoptimierungen nicht vorhanden.

## <a name="new-help-viewer-window"></a>Neues Anzeigefenster für Hilfe

> In PowerShell 3.0 hinzugefügt

Wenn Sie <kbd>F1</kbd> drücken, während sich der Cursor in einem Cmdlet befindet oder Sie einen Teil eines Cmdlets hervorgehoben haben, wird im neuen Anzeigefenster für Hilfe eine kontextbezogene Hilfe zum hervorgehobenen Cmdlet geöffnet. Um die **konzeptionelle Hilfe** für Windows PowerShell ISE anzuzeigen, geben Sie im Konsolenbereich `operators` ein, und drücken Sie dann <kbd>F1</kbd>.

Laden Sie die aktuelle Version der Windows PowerShell-Hilfethemen von der Microsoft-Website herunter, bevor Sie dieses Feature verwenden. Die einfachste Methode zum Herunterladen der Hilfethemen ist die Ausführung des Cmdlets `Update-Help` im Konsolenbereich, wenn Sie die Windows PowerShell ISE als Administrator ausführen.

Sie können ändern, wo über die Taste <kbd>F1</kbd> nach Hilfe gesucht wird. Im Menü **Extras**/**Optionen** können Sie auf der Registerkarte **Allgemeine Einstellungen** unter **Andere Einstellungen** das Kontrollkästchen **Lokale Hilfe anstatt Onlineinhalt verwenden** aktivieren bzw. deaktivieren. Wenn aktiviert, sucht der Client die Cmdlet-Hilfe in der heruntergeladenen Hilfe im Ordner „modules“. Wenn das Kontrollkästchen deaktiviert ist, sucht der Client online nach der Hilfe.

**Welchen Nutzen bietet diese Änderung?**

Durch eine kontextbezogene Hilfe ohne Verlassen des aktuellen Cmdlets oder Skripts machen Sie eine integrierte Lernerfahrung.

**Worin bestehen die Unterschiede?**

Durch Drücken von <kbd>F1</kbd> in früheren Versionen von Windows PowerShell ISE wurde die Hilfedatei auf dem lokalen Computer geöffnet. In Windows PowerShell ISE 3.0 und höher wird ein Fenster geöffnet, das die Hilfe für das Cmdlet enthält, die durchsuchbar und konfigurierbar ist. Diese Hilfe ist in Windows PowerShell ISE 3.0 neu. Die aktualisierbare Hilfe ist in Windows PowerShell 3.0 neu.

## <a name="show-command-cmdlet"></a>Cmdlet „Show-Command“

> In PowerShell 3.0 hinzugefügt

Das Cmdlet `Show-Command` ermöglicht das Erstellen und Ausführen eines Cmdlets oder einer Funktion, indem ein grafisches Formular ausgefüllt wird. Das Formular ermöglicht Benutzern das Arbeiten mit Windows PowerShell in einer grafischen Umgebung.
Mit `Show-Command` können erfahrene Skriptentwickler schnell eine Windows PowerShell-basierte grafische Benutzeroberfläche (GUI) erstellen.

**Welchen Nutzen bietet diese Änderung?**

Durch das Verwenden von `Show-Command` in Ihren Windows PowerShell-Skripts können Sie Ihren Benutzern die grafische Umgebung bereitstellen, mit der sie vertraut sind. `Show-Command` hilft darüber hinaus Einsteigern beim Erlernen von Windows PowerShell.

**Worin bestehen die Unterschiede?**

`Show-Command` ist neu in Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Siehe auch

Weitere Informationen über die Verwendung von Windows PowerShell ISE finden Sie unter [Kennenlernen der Windows PowerShell ISE](../components/ise/exploring-the-windows-powershell-ise.md).
