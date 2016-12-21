---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Zweck des Windows PowerShell ISE-Skriptobjektmodells
ms.technology: powershell
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 079b23ca1338fdb888e13cc187e9498a141916aa
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Zweck des Windows PowerShell ISE-Skriptobjektmodells
  Objekte sind der Form und Funktion von Windows PowerShell Integrated Scripting Environment (ISE) zugeordnet. Die Modellreferenz bietet Details zu den Elementeigenschaften und Methoden, die diese Objekte verfügbar machen. Die Beispiele zeigen Ihnen, wie Sie mithilfe von Skripts direkt auf diese Methoden und Eigenschaften zugreifen können. Das Skriptobjektmodell erleichtert die folgenden Aufgaben.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Anpassen der Darstellung von Windows PowerShell ISE
 Sie können das Objektmodell verwenden, um die Anwendungseinstellungen und -optionen zu ändern. Sie können sie beispielsweise folgendermaßen ändern:

-   Sie können die Farbe der Fehlermeldungen, Warnungen, ausführlichen Ausgaben, und Debugausgaben ändern.

-   Sie können die Hintergrundfarben für den Befehlsbereich, den Ausgabebereich und den Skriptbereich abrufen oder festlegen.

-   Sie können die Vordergrundfarbe im Ausgabebereich festlegen.

-   Sie können die Schriftart und Schriftgröße für Windows PowerShell ISE festlegen.

-   Sie können Warnungen konfigurieren. Diese Einstellung schließt Warnungen ein, die ausgegeben werden, wenn eine Datei in mehreren PowerShell-Registerkarten geöffnet wird oder wenn eine Datei ausgeführt wird, bevor sie gespeichert wurde.

-   Sie können zwischen zwei Ansichten wechseln: Entweder werden der Skriptbereich und der Ausgabebereich nebeneinander angezeigt, oder der Skriptbereich wird über dem Ausgabebereich angezeigt. Sie können den Befehlsbereich oben oder unten an den Ausgabebereich andocken.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Erweitern der Funktionalität von Windows PowerShell ISE
 Sie können das Objektmodell verwenden, um die Funktionalität von Windows PowerShell ISE zu erweitern. Beispielsweise können Sie folgende Aktionen ausführen:

-   Fügen Sie Instanzen von Windows PowerShell ISE hinzu und ändern Sie sie. Sie können z.B. neue Menüelemente hinzufügen und die neuen Elemente Skripts zuordnen, um die Menüs zu ändern.

-   Erstellen Sie Skripts, die einige der Aufgaben ausführen, die Sie mithilfe der Menübefehle und Schaltflächen in Windows PowerShell ISE ausführen können. Beispielsweise können Sie eine PowerShell-Registerkarte hinzufügen, entfernen oder auswählen.

-   Ergänzen Sie Aufgaben, die mithilfe der Menübefehle und Schaltflächen ausgeführt werden können. Beispielsweise können Sie eine PowerShell-Registerkarte umbenennen.

-   Ändern Sie Textpuffer für den Befehlsbereich, den Ausgabebereich und den Skriptbereich, die einer Datei zugeordnet sind. Beispielsweise können Sie folgende Aktionen ausführen:

    -   Den gesamten Text abrufen oder festlegen.

    -   Eine Textauswahl abrufen oder festlegen.

    -   Ein Skript ausführen oder einen ausgewählten Teil eines Skripts ausführen.

    -   So scrollen, dass eine bestimmte Zeile in der Ansicht erscheint.

    -   Text an der Position des Caretzeichens einfügen.

    -   Einen Textblock auswählen.

    -   Die letzte Zeilennummer abrufen.

-   Dateivorgänge ausführen. Beispielsweise können Sie folgende Aktionen ausführen:

    -   Eine Datei öffnen, speichern oder unter einem anderen Namen speichern.

    -   Feststellen, ob eine Datei seit der letzten Speicherung geändert wurde.

    -   Den Dateinamen abrufen.

    -   Eine Datei auswählen.

## <a name="automating-tasks"></a>Automatisieren von Aufgaben
 Das Skriptobjektmodell verwenden, um Tastenkombinationen für häufige Vorgänge zu erstellen.

## <a name="see-also"></a>Weitere Informationen
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md) 
- [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
