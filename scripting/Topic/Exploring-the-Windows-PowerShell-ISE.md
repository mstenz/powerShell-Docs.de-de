---
title: Kennenlernen der Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
---
# Kennenlernen der Windows PowerShell ISE
Sie können die [!INCLUDE[ise_1](../Token/ise_1_md.md)] zum Erstellen, Ausführen und Debuggen von Befehlen und Skripts nutzen. Die [!INCLUDE[ise_2](../Token/ise_2_md.md)] besteht aus Menüleiste, Windows PowerShell-Registerkarten, Symbolleiste, Skriptregisterkarten, Skriptbereich, Konsolenbereich, Statusleiste, Schieberegler für die Textgröße und kontextabhängiger Hilfe.

> [!NOTE]
> Ab [!INCLUDE[ise_2](../Token/ise_2_md.md)] 3.0 wurden der Befehls- und Ausgabebereich in einer zentralen Konsole zusammengefasst.

## Menüleiste
Die Menüleiste enthält die Menüs **Datei**, **Bearbeiten**, **Ansicht**, **Tools**, **Debuggen**, **Add-Ons** und **Hilfe**. Über die Schaltflächen in den Menüs können Sie Aufgaben im Zusammenhang mit dem Schreiben und Ausführen von Skripts und Ausführen von Befehlen in der [!INCLUDE[ise_2](../Token/ise_2_md.md)] erledigen. Darüber hinaus kann das Menü [Add-Ons ](https://technet.microsoft.com/en-us/library/412dd662-417a-4661-ada2-558802d0f6d2#submenus) auf der Menüleiste platziert werden, indem Skripts ausgeführt werden, die das [Windows PowerShell ISE-Skriptobjektmodell](https://technet.microsoft.com/en-us/library/1737ddb7-c20d-4e6b-a0d3-68cc2650f2a1) verwenden.

> [!NOTE]
> In [!INCLUDE[ise_2](../Token/ise_2_md.md)] 2.0 gab es die Menüs **Tools** und **Add-Ons** nicht.

## Windows PowerShell-Registerkarten
Eine Windows PowerShell-Registerkarte ist die Umgebung, in der ein Windows PowerShell-Skript ausgeführt wird. Sie können neue Windows PowerShell-Registerkarten in der [!INCLUDE[ise_2](../Token/ise_2_md.md)] öffnen, um auf dem lokalen Computer oder auf Remotecomputern getrennte Umgebungen zu erstellen. Gleichzeitig können maximal acht PowerShell-Registerkarten geöffnet sein.

## Symbolleiste
Die folgenden Schaltflächen befinden sich auf der Symbolleiste.

|Schaltfläche|Funktion|
|----------|------------|
|**Neu**|Öffnet ein neues Skript.|
|**Öffnen**|Öffnet ein vorhandenes Skript oder eine Datei.|
|**Speichern**|Speichert ein Skript oder eine Datei.|
|**Ausschneiden**|Schneidet den ausgewählten Text aus und kopiert ihn in die Zwischenablage.|
|**Kopieren**|Kopiert den ausgewählten Text in die Zwischenablage.|
|**Einfügen**|Fügt den Inhalt der Zwischenablage an der Cursorposition ein.|
|**Ausgabebereich löschen**|Löscht den gesamten Inhalt aus dem Ausgabebereich.|
|**Rückgängig machen**|Macht die Aktion rückgängig, die zuvor erfolgt ist.|
|**Wiederholen**|Führt die Aktion aus, die zuvor rückgängig gemacht wurde.|
|**Skript ausführen**|Führt ein Skript aus.|
|**Auswahl ausführen**|Führt einen ausgewählten Teil eines Skripts aus.|
|**Ausführung beenden**|Beendet ein Skript, das ausgeführt wird.|
|**Neue Registerkarte „Remote-PowerShell“**|Erstellt eine neue PowerShell-Registerkarte, die eine Sitzung auf einem Remotecomputer herstellt. Ein Dialogfeld wird angezeigt und fordert Sie zur Eingabe von Details auf, die zum Herstellen der Remoteverbindung erforderlich sind.|
|**„PowerShell.exe“ starten**|Öffnet eine PowerShell-Konsole.|
|**Skriptbereich oben anzeigen**|Verschiebt den Skriptbereich in der Anzeige nach oben.|
|**Skriptbereich rechts anzeigen**|Verschiebt den Skriptbereich in der Anzeige nach rechts.|
|**Skriptbereich maximiert anzeigen**|Maximiert den Skriptbereich.|

## Skriptregisterkarte
Zeigt den Namen des Skripts an, das Sie bearbeiten. Sie können auf eine Skriptregisterkarte klicken, um das Skript auszuwählen, das Sie bearbeiten möchten.

Wenn Sie auf die Skriptregisterkarte zeigen, wird der vollqualifizierte Pfad der Skriptdatei als QuickInfo angezeigt.

## Skriptbereich
Ermöglicht das Erstellen und Ausführen von Skripts. Sie können im Skriptbereich vorhandene Skripts öffnen, bearbeiten und ausführen.

## Ausgabebereich
Zeigt die Ergebnisse der Befehle und Skripts an, die ausgeführt wurden. Sie können den Inhalt des Ausgabebereich auch kopieren und löschen.

## Befehlsbereich
Ermöglicht das Schreiben von Befehlen. Sie können im Befehlsbereich einen Befehl mit einer oder mehreren Zeilen ausführen. Drücken Sie UMSCHALT+EINGABETASTE, um jede Zeile eines mehrzeiligen Befehls einzugeben. Drücken Sie nach der letzten Zeile die EINGABETASTE, um den mehrzeiligen Befehl auszuführen. Die oben im Befehlsbereich angezeigte Aufforderung zeigt den Pfad zum aktuellen Arbeitsverzeichnis.

## Statusleiste
Ermöglicht festzustellen, ob Ihre Befehle und Skripts vollständig ausgeführt wurden. Die Statusleiste befindet sich ganz unten in der Anzeige. Ausgewählte Teile von Fehlermeldungen werden auf der Statusleiste angezeigt.

## Schieberegler für die Textgröße
Erhöht oder verringert die Größe des Texts auf dem Bildschirm.

## Hilfe
Hilfe für [!INCLUDE[ise_2](../Token/ise_2_md.md)] ist im Web in der TechNet-Bibliothek verfügbar. Sie können die Hilfe öffnen, indem Sie im Menü **Hilfe** auf **Hilfe zu Windows PowerShell ISE** klicken oder die Taste F1 drücken, wobei sich der Cursor allerdings nicht über einem Cmdlet-Namen im Skript- oder Konsolenbereich befinden darf. Im Menü **Hilfe** können Sie auch das Cmdlet „Update-Help“ ausführen und das Befehlsfenster anzeigen. Dieses unterstützt Sie beim Erstellen von Befehlen, indem alle Parameter für ein Cmdlet angezeigt werden und Sie die Parameter in einem benutzerfreundlichen Formular ausfüllen können.

## Weitere Informationen
[Verwenden der Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO2-->


