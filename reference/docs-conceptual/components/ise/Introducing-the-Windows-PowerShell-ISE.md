---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Einführung in die Windows PowerShell ISE
ms.openlocfilehash: 1723c11f38966cfffec9a6b3e4cb7b2304f19e7a
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416289"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) ist eine Hostanwendung für Windows PowerShell. Sie können mit ISE in einer Windows-basierten grafischen Benutzeroberfläche Befehle ausführen und Skripts schreiben, testen und debuggen. Die ISE ermöglicht mehrzeilige Bearbeitung, Vervollständigung mit der TAB-TASTE, Syntaxfarben, selektive Ausführung, kontextbezogene Hilfe und Unterstützung für Rechts-nach-links-Sprachen. Menüelemente und Tastenkombinationen sind vielen der Aufgaben zugeordnet, die Sie auch in der Windows PowerShell-Konsole ausführen würden. Wenn Sie z.B. ein Skript in ISE debuggen, können Sie mit der rechten Maustaste im Bearbeitungsbereich auf eine Codezeile klicken, um einen Breakpoint festzulegen.

## <a name="support"></a>Support

Die ISE wurde erstmals mit Windows PowerShell V2 eingeführt und in PowerShell V3 überarbeitet. Die ISE wird in allen unterstützten Versionen von Windows PowerShell bis einschließlich Windows PowerShell V5.1 unterstützt.

> [!NOTE]
> Die PowerShell ISE befindet sich nicht mehr in der aktiven Featureentwicklung. Als in Windows enthaltene Komponente wird sie weiterhin offiziell mit Sicherheits- und Wartungsfixes hoher Priorität unterstützt.
> Zurzeit ist es nicht geplant, die ISE aus Windows zu entfernen.
>
> Es besteht keine Unterstützung für die ISE in PowerShell v6 oder höher. Benutzer, die einen Ersatz für die ISE suchen, sollten [Visual Studio Code](https://code.visualstudio.com/) mit der [PowerShell-Erweiterung](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell) verwenden.

## <a name="key-features"></a>Wichtige Funktionen

Zu den wichtigsten Funktionen von Windows PowerShell ISE gehören:

- Mehrzeilige Bearbeitung: Drücken Sie zum Einfügen einer leeren Zeile unter der aktuellen Zeile im Befehlsbereich <kbd>UMSCHALT</kbd>+<kbd>EINGABETASTE</kbd>.
- Selektive Ausführung: Um einen Teil eines Skripts auszuführen, markieren Sie den Text, den Sie ausführen möchten, und klicken Sie dann auf die Schaltfläche **Skript ausführen**. Drücken Sie alternativ dazu <kbd>F5</kbd>.
- Kontextbezogene Hilfe: Geben Sie `Invoke-Item` ein, und drücken Sie dann <kbd>F1</kbd>. Die Hilfedatei wird mit dem Artikel für das Cmdlet `Invoke-Item` geöffnet.

Die Windows PowerShell ISE ermöglicht Ihnen das Anpassen einiger Aspekte ihrer Darstellung. Sie enthält auch ein eigenes Windows PowerShell-Profilskript.

## <a name="to-start-the-windows-powershell-ise"></a>So starten Sie die Windows PowerShell ISE

Klicken Sie auf **Start**, wählen Sie **Windows PowerShell** aus, und klicken Sie dann auf **Windows PowerShell ISE**.
Alternativ können Sie `powershell_ise.exe` in eine Befehlsshell oder im Feld „Ausführen“ eingeben.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>So rufen Sie Hilfe in der Windows PowerShell ISE ab

Klicken Sie im Menü **Hilfe** auf **Windows PowerShell-Hilfe**. Drücken Sie alternativ dazu <kbd>F1</kbd>. Die daraufhin geöffnete Datei beschreibt die Windows PowerShell ISE und Windows PowerShell und enthält die gesamte Hilfe, die über das Cmdlet `Get-Help` verfügbar ist.
