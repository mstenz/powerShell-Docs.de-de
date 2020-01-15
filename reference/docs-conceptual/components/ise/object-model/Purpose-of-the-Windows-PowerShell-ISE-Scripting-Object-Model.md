---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Zweck des Windows PowerShell ISE-Skriptobjektmodells
ms.openlocfilehash: 1f48df112bd19297baa311116e79d3d7603d7c81
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736231"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Zweck des Windows PowerShell ISE-Skriptobjektmodells

Objekte sind der Form und Funktion von Windows PowerShell Integrated Scripting Environment (ISE) zugeordnet. Die Modellreferenz bietet Details zu den Elementeigenschaften und Methoden, die diese Objekte verfügbar machen. Die Beispiele zeigen Ihnen, wie Sie mithilfe von Skripts direkt auf diese Methoden und Eigenschaften zugreifen können. Das Skriptobjektmodell erleichtert die folgenden Aufgaben.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Anpassen der Darstellung von Windows PowerShell ISE

Sie können das Objektmodell verwenden, um die Anwendungseinstellungen und -optionen zu ändern. Sie können sie beispielsweise folgendermaßen ändern:

- Ändern Sie die Farbe von Fehlermeldungen, Warnungen, ausführlichen Ausgaben und Debugausgaben.
- Rufen Sie die Hintergrundfarben für den Befehlsbereich, den Ausgabebereich und den Skriptbereich ab, oder legen Sie sie fest.
- Legen Sie die Vordergrundfarbe für den Ausgabebereich fest.
- Legen Sie die Schriftart und Schriftgröße für Windows PowerShell ISE fest.
- Konfigurieren Sie Warnungen. Diese Einstellung schließt Warnungen ein, die ausgegeben werden, wenn eine Datei in mehreren PowerShell-Registerkarten geöffnet wird oder wenn eine Datei ausgeführt wird, bevor sie gespeichert wurde.
- Wechseln Sie zwischen zwei Ansichten: Entweder werden der Skriptbereich und der Ausgabebereich nebeneinander angezeigt, oder der Skriptbereich wird über dem Ausgabebereich angezeigt.
- Docken Sie den Befehlsbereich oben oder unten an den Ausgabebereich an.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Erweitern der Funktionalität von Windows PowerShell ISE

Sie können das Objektmodell verwenden, um die Funktionalität von Windows PowerShell ISE zu erweitern. Beispielsweise können Sie folgende Aktionen ausführen:

- Fügen Sie Instanzen von Windows PowerShell ISE hinzu und ändern Sie sie. Sie können z.B. neue Menüelemente hinzufügen und die neuen Elemente Skripts zuordnen, um die Menüs zu ändern.
- Erstellen Sie Skripts, die einige der Aufgaben ausführen, die Sie mithilfe der Menübefehle und Schaltflächen in Windows PowerShell ISE ausführen können. Beispielsweise können Sie eine PowerShell-Registerkarte hinzufügen, entfernen oder auswählen.
- Ergänzen Sie Aufgaben, die mithilfe der Menübefehle und Schaltflächen ausgeführt werden können. Beispielsweise können Sie eine PowerShell-Registerkarte umbenennen.
- Ändern Sie Textpuffer für den Befehlsbereich, den Ausgabebereich und den Skriptbereich, die einer Datei zugeordnet sind. Beispielsweise können Sie folgende Aktionen ausführen:
  - Den gesamten Text abrufen oder festlegen.
  - Eine Textauswahl abrufen oder festlegen.
  - Ein Skript ausführen oder einen ausgewählten Teil eines Skripts ausführen.
  - So scrollen, dass eine bestimmte Zeile in der Ansicht erscheint.
  - Text an der Position des Caretzeichens einfügen.
  - Einen Textblock auswählen.
  - Die letzte Zeilennummer abrufen.
- Dateivorgänge ausführen. Beispielsweise können Sie folgende Aktionen ausführen:
  - Eine Datei öffnen, speichern oder unter einem anderen Namen speichern.
  - Feststellen, ob eine Datei seit der letzten Speicherung geändert wurde.
  - Den Dateinamen abrufen.
  - Eine Datei auswählen.

## <a name="automating-tasks"></a>Automatisieren von Aufgaben

Das Skriptobjektmodell verwenden, um Tastenkombinationen für häufige Vorgänge zu erstellen.

## <a name="see-also"></a>Weitere Informationen

- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
