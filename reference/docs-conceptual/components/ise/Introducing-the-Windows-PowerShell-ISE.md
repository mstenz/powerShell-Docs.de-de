---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Einführung in die Windows PowerShell ISE
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057420"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell Integrated Scripting Environment (ISE) ist eine Hostanwendung für Windows PowerShell. Sie können mit ISE in einer Windows-basierten grafischen Benutzeroberfläche Befehle ausführen und Skripts schreiben, testen und debuggen. Die ISE ermöglicht mehrzeilige Bearbeitung, Vervollständigung mit der TAB-TASTE, Syntaxfarben, selektive Ausführung, kontextbezogene Hilfe und Unterstützung für Rechts-nach-links-Sprachen. Menüelemente und Tastenkombinationen sind vielen der Aufgaben zugeordnet, die Sie auch in der Windows PowerShell-Konsole ausführen würden. Wenn Sie z.B. ein Skript in ISE debuggen, können Sie mit der rechten Maustaste im Bearbeitungsbereich auf eine Codezeile klicken, um einen Breakpoint festzulegen.

## <a name="support"></a>Support

Die ISE wurde erstmals mit Windows PowerShell V2 eingeführt und in PowerShell V3 überarbeitet. Die ISE wird in allen unterstützten Versionen von Windows PowerShell bis einschließlich Windows PowerShell V5.1 unterstützt. Die ISE befindet sich jedoch im Wartungsmodus, und es werden wahrscheinlich keine neuen Funktionen hinzugefügt.
Darüber hinaus besteht keine Unterstützung für die ISE mit PowerShell v6 oder höher. Benutzer, die ein grafisches Tool zur Verwaltung von PowerShell-Skripts usw. benötigen, sollten [Visual Studio Code](https://code.visualstudio.com/) in Betracht ziehen.

## <a name="key-features"></a>Wichtige Funktionen

Zu den wichtigsten Funktionen von Windows PowerShell ISE gehören:

- Mehrzeilige Bearbeitung: Drücken Sie zum Einfügen einer leeren Zeile unter der aktuellen Zeile im Befehlsbereich UMSCHALT+EINGABETASTE.
- Selektive Ausführung: Um einen Teil eines Skripts auszuführen, markieren Sie den Text, den Sie ausführen möchten, und klicken Sie dann auf die Schaltfläche **Skript ausführen**. Oder drücken Sie F5.
- Kontextbezogene Hilfe: Geben Sie **Invoke-Item** ein, und drücken Sie dann F1. Die Hilfedatei wird mit dem Artikel für das Cmdlet **Invoke-Item** geöffnet.

Die Windows PowerShell ISE ermöglicht Ihnen das Anpassen einiger Aspekte ihrer Darstellung. Sie enthält auch ein eigenes Windows PowerShell-Profilskript.

## <a name="to-start-the-windows-powershell-ise"></a>So starten Sie die Windows PowerShell ISE

Klicken Sie auf **Start**, wählen Sie **Windows PowerShell** aus, und klicken Sie dann auf **Windows PowerShell ISE**.
Alternativ können Sie `powershell_ise.exe` in eine Befehlsshell oder im Feld „Ausführen“ eingeben.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>So rufen Sie Hilfe in der Windows PowerShell ISE ab

Klicken Sie im Menü **Hilfe** auf **Windows PowerShell-Hilfe**. Oder drücken Sie F1. Die Datei, die geöffnet wird, beschreibt die Windows PowerShell ISE und Windows PowerShell, einschließlich sämtlicher Hilfe, die über das Cmdlet „Get-Help“ verfügbar ist.
