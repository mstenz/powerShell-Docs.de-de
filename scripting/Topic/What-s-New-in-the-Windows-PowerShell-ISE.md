---
title: Neuerungen bei der Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
---
# Neuerungen bei der Windows PowerShell ISE
In diesem Thema werden die neuen und aktualisierten Features vorgestellt, die in Versionen der [!INCLUDE[ise_1](../Token/ise_1_md.md)] eingeführt wurden.

## <a name="overview"></a>Featurebeschreibung
Die [!INCLUDE[ise_2](../Token/ise_2_md.md)] ist eine Hostanwendung, die es Ihnen ermöglicht, Skripts und Module in einer grafischen und intuitiven Umgebung zu schreiben, auszuführen und zu testen. Wichtige Features wie Syntaxfarben, Vervollständigung mit der TAB-TASTE, visuelles Debuggen, Unicode-Kompatibilität und kontextbezogene Hilfe ermöglichen eine komfortable Skripterstellung.

Eine Übersicht über die [!INCLUDE[ise_2](../Token/ise_2_md.md)] finden Sie unter [Windows PowerShell Integrated Scripting Environment (Übersicht)](assetId:///3c1892c2-bf84-4cb6-af26-1f453be9e671).

## <a name="versions"></a>Neue und geänderte Funktionen in der Windows PowerShell ISE
Die folgende Tabelle enthält die neuen und geänderten Funktionen für diese Version von [!INCLUDE[ise_2](../Token/ise_2_md.md)] in [!INCLUDE[wps_2](../Token/wps_2_md.md)].

|Feature/Funktionalität|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 4.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0|[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|**[IntelliSense](#BKMK_Intellisense)**|X|X||
|**[Codeausschnitte](#bkmk_snippets)**|X|X||
|**[Add-On-Tools](#BKMK_AddOnTools)**|X|X||
|**[Neustart-Manager und automatisches Speichern](#BKMK_RestartMgr)**|X|X||
|**[Konsolenbereich](#BKMK_ConsolePane)**|X|X||
|**[Liste „Zuletzt verwendet“](#BKMK_MRU)**|X|X||
|**[Befehlszeilenschalter](#BKMK_CommandLine)**|X|X||
|**[Neue Features im Editor](#BKMK_NewEditorFeatures)**|X|X||
|**[Neues Anzeigefenster für Hilfe](#BKMK_NewHelpViewer)**|X|X||
|**[Cmdlet „Show-Command“](#BKMK_ShowCommand)**|X|X||

### <a name="BKMK_Intellisense"></a>IntelliSense
**In ISE 3.0 hinzugefügt**

IntelliSense ist ein Feature für die automatische Vervollständigung, das zur [!INCLUDE[ise_2](../Token/ise_2_md.md)] gehört. IntelliSense zeigt während der Eingabe klickbare Menüs möglicherweise übereinstimmender Cmdlets, Parameter, Parameterwerte, Dateien oder Ordner an.

**Welchen Nutzen bietet diese Änderung?**

Durch das Hinzufügen von Intellisense ist es einfacher, Cmdlets und Syntax zu ermitteln, wenn Sie [!INCLUDE[ise_2](../Token/ise_2_md.md)] zum Erstellen von Skripts nutzen. Sie können auch mithilfe von [!INCLUDE[ise_2](../Token/ise_2_md.md)] auch [!INCLUDE[wps_2](../Token/wps_2_md.md)] erlernen, während Sie neue Skripts erstellen.

**Worin bestehen die Unterschiede?**

Bei Eingabe von Cmdlets in die [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 oder höher, wird ein scroll- und klickbares Menü angezeigt, das Ihnen das Durchsuchen und Auswählen der entsprechenden Befehle ermöglicht.

### <a name="BKMK_Snippets"></a>Codeausschnitte
**In ISE 3.0 hinzugefügt**

*Codeausschnitte* sind kurze Abschnitte von [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Code, die Sie in [!INCLUDE[ise_2](../Token/ise_2_md.md)] erstellte Skripts einfügen können. [!INCLUDE[ise_2](../Token/ise_2_md.md)] bietet einen Standardsatz von Codeausschnitten. Beim Arbeiten in [!INCLUDE[ise_2](../Token/ise_2_md.md)] können Sie Codeausschnitte mithilfe des Cmdlets **New-Snippet** hinzufügen.

**Welchen Nutzen bietet diese Änderung?**

Mithilfe von Codeausschnitten können Sie Skripts zum Automatisieren Ihrer Umgebung schnell zusammenstellen und erstellen.

**Worin bestehen die Unterschiede?**

Klicken Sie zum Verwenden von Codeausschnitten in [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0 oder höher im Menü **Bearbeiten** auf **Codeausschnitte starten**, oder drücken Sie **STRG+J**.

### <a name="BKMK_AddOnTools"></a>Add-On-Tools
**In PowerShell 3.0 hinzugefügt**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] unterstützt jetzt Add-On-Tools, bei denen es sich um WPF-Steuerelemente (Windows Presentation Foundation) handelt, die mithilfe des Objektmodells hinzugefügt werden. Add-On-Tools können in der Konsole in einem vertikalen oder horizontalen Bereich angezeigt werden. Mehrere Add-On-Tools in einem Bereich werden als Registerkarten-Steuerelement angezeigt. Sie können auch Add-On-Tools von anderen Anbietern als Microsoft hinzufügen oder entfernen. Weitere Informationen zum Importieren oder Entfernen von Add-On-Tools finden Sie unter [Windows PowerShell ISE-Vorgänge](http://technet.microsoft.com/library/cc732148.aspx).

**Welchen Nutzen bietet diese Änderung?**

Add-Ons ermöglichen Ihnen das Erweitern und Anpassen von [!INCLUDE[ise_2](../Token/ise_2_md.md)] mit Tools, die Ihre Skripterstellungsumgebung verbessern oder [!INCLUDE[ise_2](../Token/ise_2_md.md)] neue Funktionen hinzufügen können.

**Worin bestehen die Unterschiede?**

Zum Funktionsumfang von [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 und höher gehört das Add-On **Befehle**. Das Add-On **Befehle** ermöglicht das Durchsuchen von Cmdlets und Zugreifen auf Hilfe zu den Cmdlets. Es wird neben den Bereichen **Skript** und **Konsole** angezeigt.

Zusätzliche Add-Ons finden Sie über den Befehl **Website mit Add-On-Tools öffnen** im Menü**Add-Ons**.

### <a name="BKMK_RestartMgr"></a>Neustart-Manager und automatisches Speichern
**In PowerShell 3.0 hinzugefügt**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] speichert nun Ihre geöffneten Skripts automatisch alle zwei Minuten an einem gesonderten Speicherort.  Wenn [!INCLUDE[ise_2](../Token/ise_2_md.md)] unerwartet beendet oder das Betriebssystem neu gestartet wird, stellt [!INCLUDE[ise_2](../Token/ise_2_md.md)] die in der letzten Sitzung geöffneten Skripts wieder her (auch wenn sie nicht gespeichert wurden).

Um das Intervall für die automatische Speicherung zu ändern, führen im Konsolenbereich Sie den folgenden Befehl aus: **$psise.Options.AutoSaveMinuteInterval**.

**Welchen Nutzen bietet diese Änderung?**

Sie können jetzt mit [!INCLUDE[ise_2](../Token/ise_2_md.md)] mit dem Wissen arbeiten, dass Ihre geöffneten Skripts im Fall eines unerwarteten Neustarts automatisch gespeichert werden.

**Worin bestehen die Unterschiede?**

In [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 werden die Skripts bei einem Neustart nicht automatisch gespeichert.

### <a name="BKMK_MRU"></a>Liste „Zuletzt verwendet“
**In PowerShell 3.0 hinzugefügt**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] bietet jetzt eine Liste der zuletzt verwendeten Dateien. Beim Öffnen einer Datei in [!INCLUDE[ise_2](../Token/ise_2_md.md)] wird die Datei der Liste „Zuletzt verwendet“ im Menü **Datei** hinzugefügt.

Um die Standardanzahl von Dateien in der Liste „Zuletzt verwendet“ zu ändern, führen Sie im Konsolenbereich den folgenden Befehl aus: **$psise.Options.MruCount**.

**Welchen Nutzen bietet diese Änderung?**

Über die Liste „Zuletzt verwendet“ können Sie nun mühelos auf die zuletzt verwendeten Dateien zugreifen.

**Worin bestehen die Unterschiede?**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 bietet keine solche Liste.

### <a name="BKMK_ConsolePane"></a>Konsolenbereich
**In PowerShell 3.0 hinzugefügt**

Die separaten Befehls- und Ausgabebereiche, die in der ersten Version von [!INCLUDE[ise_2](../Token/ise_2_md.md)] verfügbar waren, wurden in einem Konsolenbereich kombiniert. Hinsichtlich Funktion und Darstellung ähnelt der Konsolenbereich einer typischen [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Konsole, bietet aber die im Folgenden aufgeführten Erweiterungen (von denen die meisten in diesem Thema beschrieben werden).

-   Syntaxfarben für Eingabetext (nicht für Ausgabetext), einschließlich XML-Syntax

-   IntelliSense

-   Zugehörige Klammer

-   Fehleranzeige

-   Vollständige Unicode-Unterstützung

-   Kontextbezogene Hilfe über **F1**

-   Kontextbezogenes Cmdlet „Show-Command“ über **STRG+F1**

-   Unterstützung von komplexen Skripts und Sprachen mit Leserichtung von rechts nach links

-   Schriftartenunterstützung

-   Zoom

-   Modi für Zeilen- und Blockauswahl

-   Beibehaltung von über die Befehlszeile eingegebenem Inhalt, wenn Sie mithilfe der NACH-OBEN-TASTE** **den Verlauf in der Konsole anzeigen

**Welchen Nutzen bietet diese Änderung?**

Diese Änderungen im Konsolenbereich ermöglichen eine Skriptumgebung, die mit der Konsolenschnittstelle konsistenter ist.

**Worin bestehen die Unterschiede?**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 verfügt über getrennte Befehls- und Ausgabebereiche.

### <a name="BKMK_CommandLine"></a>Befehlszeilenschalter
**In PowerShell 3.0 hinzugefügt**

Wenn Sie [!INCLUDE[ise_2](../Token/ise_2_md.md)] über die Befehlszeile starten (indem Sie **Powershell_ise.exe** eingeben), können Sie die folgenden neuen Befehlszeilenschalter hinzufügen.

-   *-NoProfile*: Startet [!INCLUDE[ise_2](../Token/ise_2_md.md)] ohne Ausführung von **$profile**

-   *-Help*: Zeigt ein Hilfefenster an.

-   *-mta*: Startet [!INCLUDE[ise_2](../Token/ise_2_md.md)] im Multithread-Apartment-Modus. Der Standardbetriebsmodus von [!INCLUDE[ise_2](../Token/ise_2_md.md)] ist der Singlethread-Apartment-Modus bzw. *-sta*.

**Welchen Nutzen bietet diese Änderung?**

Das Hinzufügen dieser Befehlszeilenschalter ermöglicht Ihnen das Steuern der Umgebung, in der die [!INCLUDE[ise_2](../Token/ise_2_md.md)] ausgeführt wird.

**Worin bestehen die Unterschiede?**

[!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 erkennt diese Befehlszeilenschalter nicht.

### <a name="BKMK_NewEditorFeatures"></a>Neue Features im Editor
**In PowerShell 3.0 hinzugefügt**

Es folgen weitere [!INCLUDE[ise_2](../Token/ise_2_md.md)]-Bearbeitungsfeatures:

-   **XML-Syntaxfarben**[!INCLUDE[ise_2](../Token/ise_2_md.md)] versieht XML-Syntax jetzt genauso wie [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Syntax mit Farben.

-   **Zugehörige Klammer ** [!INCLUDE[ise_2](../Token/ise_2_md.md)] bietet das Feature „Zugehörige Klammer (Hervorhebung)“, das wie folgt genutzt werden kann. Wenn Sie z. B. den Befehl **Gehe zu Übereinstimmung** bzw. **Ctrl+]** verwenden, wird die schließende Klammer gefunden, wenn eine öffnende Klammer ausgewählt ist).

-   **Gliederungsansicht** Der Skriptbereich unterstützt Gliederungen, sodass Codeabschnitte durch Klicken auf Plus- und Minuszeichen am linken Rand auf- bzw. zugeklappt werden können. Sie können Klammern bzw. **#region**- und **#endregion**-Tags verwenden, um den Anfang bzw. das Ende eines zuklappbaren Abschnitts zu markieren. Drücken Sie zum Auf- und Zuklappen aller Bereiche **STRG+M**.

-   **Textbearbeitung mit Drag & Drop**[!INCLUDE[ise_2](../Token/ise_2_md.md)] unterstützt nun die Textbearbeitung mit Drag & Drop. Sie können einen beliebigen Textblock auswählen und an eine andere Stelle im Editor oder in der Konsole ziehen, um den Text zu verschieben. Wenn Sie die STRG-Taste gedrückt halten, während Sie den markierten Text ziehen, wird der Text, sobald Sie die Maustaste loslassen, an den neuen Ort kopiert. In dieser Version von [!INCLUDE[ise_2](../Token/ise_2_md.md)] wird wie in der vorherigen Version von [!INCLUDE[ise_2](../Token/ise_2_md.md)] beim Ziehen und Ablegen von Dateien auf [!INCLUDE[ise_2](../Token/ise_2_md.md)] die Datei von [!INCLUDE[ise_2](../Token/ise_2_md.md)] geöffnet.

-   **Anzeige von Analysefehlern** Analysefehler werden rot unterstrichen angezeigt. Wenn Sie auf einen Fehler zeigen, wird das im Code gefundene Problem als QuickInfo angezeigt.

-   **Zoom** Der Zoomprozentsatz des Inhalts der Konsole kann mit einem Zoomschieberegler (rechts unten im [!INCLUDE[ise_2](../Token/ise_2_md.md)]-Fenster) oder durch Eingabe des Befehls **$psise.options.Zoom** im Konsolenbereich festgelegt werden.

-   **Umfassende Funktionen zum Kopieren und Einfügen von Text** Beim Kopieren in die Zwischenablage in [!INCLUDE[ise_2](../Token/ise_2_md.md)] bleiben Informationen zur Schriftart, Größe und Farbe der ursprünglichen Auswahl erhalten.

-   **Blockauswahl** Sie können einen Textblock auswählen, indem Sie die ALT-TASTE gedrückt halten, während Sie den Text im Skriptbereich mit der Maus auswählen, oder ** **ALT+UMSCHALT+NACH-OBEN/NACH-UNTEN drücken.

**Welchen Nutzen bietet diese Änderung?**

Die zusätzlichen Bearbeitungsfeatures bieten eine konsistentere und leistungsstärkere Bearbeitungsumgebung.

**Worin bestehen die Unterschiede?**

In [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 wurden diese Bearbeitungsoptimierungen nicht geboten.

### <a name="BKMK_NewHelpViewer"></a>Neues Anzeigefenster für Hilfe
**In PowerShell 3.0 hinzugefügt**

Wenn Sie **F1** drücken, während sich der Cursor in einem Cmdlet befindet oder Sie einen Teil eines Cmdlets markiert haben, wird im neuen Anzeigefenster für Hilfe eine kontextbezogene Hilfe zum markierten Cmdlet geöffnet. Um Hilfe für [!INCLUDE[wps_2](../Token/wps_2_md.md)] anzuzeigen, geben Sie im Konsolenbereich **operators** ein, und drücken Sie dann **F1**.

Laden Sie die aktuelle Version der [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Hilfethemen von der Microsoft-Website herunter, bevor Sie dieses Feature verwenden. Die einfachste Methode zum Herunterladen von Hilfethemen ist die Ausführung des Cmdlets **Update-Help** im Konsolenbereich, wenn Sie [!INCLUDE[ise_2](../Token/ise_2_md.md)] als Administrator ausführen.

Sie können ändern, wo über die Taste **F1** nach Hilfe gesucht wird. Im Menü **Extras** > **Optionen** können Sie auf der Registerkarte **Allgemeine Einstellungen** unter **Andere Einstellungen** das Kontrollkästchen **Lokale Hilfe anstatt Onlineinhalt verwenden** aktivieren bzw. deaktivieren. Falls aktiviert, sucht der Client die Cmdlet-Hilfe in der heruntergeladenen Hilfe im Ordner „modules“.  Falls das Kontrollkästchen deaktiviert ist, sucht der Client in der TechNet-Bibliothek nach der Cmdlet-Hilfe.

**Welchen Nutzen bietet diese Änderung?**

Durch eine kontextbezogene Hilfe ohne Verlassen des aktuellen Cmdlets oder Skripts erhalten Sie eine flüssige Lernerfahrung.

**Worin bestehen die Unterschiede?**

Durch Drücken von F1 in früheren Versionen von [!INCLUDE[ise_2](../Token/ise_2_md.md)] wurde die Hilfedatei auf dem lokalen Computer geöffnet. In [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 und höher wird ein Fenster geöffnet, das die Hilfe für das Cmdlet enthält, die durchsuchbar und konfigurierbar ist. Diese Hilfe ist für [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 neu. Aktualisierbare Hilfe ist für [!INCLUDE[wps_2](../Token/wps_2_md.md)] 3.0 neu.

### <a name="BKMK_ShowCommand"></a>Cmdlet „Show-Command“
**In PowerShell 3.0 hinzugefügt**

Das Cmdlet **Show-Command** ermöglicht das Erstellen und Ausführen eines Cmdlets oder einer Funktion, indem ein grafisches Formular ausgefüllt wird. Das Formular ermöglicht Benutzern das Arbeiten mit [!INCLUDE[wps_2](../Token/wps_2_md.md)] in einer grafischen Umgebung. Mit **Show-Command** können erfahrene Skriptentwickler schnell eine [!INCLUDE[wps_2](../Token/wps_2_md.md)]-basierte grafische Benutzeroberfläche (GUI) erstellen.

**Welchen Nutzen bietet diese Änderung?**

Durch Verwenden von **Show-Command** in Ihren [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Skripts können Sie Ihren Benutzern die grafische Umgebung bereitstellen, mit der sie vertraut sind. **Show-Command** hilft darüber hinaus Einsteigern beim Erlernen von [!INCLUDE[wps_2](../Token/wps_2_md.md)].

**Worin bestehen die Unterschiede?**

„Show-Command“ ist in [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 neu.

## <a name="BKMK_LINKS"></a>Siehe auch
Über die folgenden Links können Sie auf weitere Informationen zur Verwendung von [!INCLUDE[ise_2](../Token/ise_2_md.md)] in [!INCLUDE[wps_2](../Token/wps_2_md.md)] zugreifen.

-   [Verwenden der Windows PowerShell Integrated Scripting Environment (ISE)](assetId:///777ea82b-dd73-4269-b61a-69a17e6ff16f)

-   [ISE im TechNet Wiki](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)

-   [Script Center](http://technet.microsoft.com/scriptcenter/default)



<!--HONumber=Apr16_HO1-->


