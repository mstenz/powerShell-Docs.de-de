---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwenden des Konsolenbereichs in der Windows PowerShell ISE
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 5bbbdd3b1f0324ff1a4f2298459f58640c4dc9a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Verwenden des Konsolenbereichs in der Windows PowerShell ISE

Der Konsolenbereich in Windows PowerShell Integrated Scripting Environment (ISE) funktioniert genauso wie das eigenständige Windows PowerShell ISE-Konsolenfenster.

Um einen Befehl im Konsolenbereich ausführen, geben Sie einen Befehl ein, und drücken Sie dann die EINGABETASTE. Um mehrere Befehle einzugeben, die nacheinander ausgeführt werden sollen, drücken Sie UMSCHALT+EINGABETASTE zwischen den Befehlen. Hilfe zum Eingeben von Befehlen finden Sie unter [Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md).

Um einen Befehl zu beenden, klicken Sie auf der Symbolleiste auf **Vorgang beenden**, oder drücken Sie STRG+UNTBR. Sie können auch STRG+C verwenden, um einen Befehl zu beenden, sofern der Kontext eindeutig ist. Wenn im aktuellen Bereich beispielsweise Text ausgewählt ist,wird STRG+C dem Kopiervorgang zugeordnet.

Seit Windows PowerShell Version 3 ist der Ausgabebereich mit dem Konsolenbereich kombiniert. Dies hat den Vorteil, dass sich das System wie die eigenständige Windows PowerShell-Konsole verhält, und beseitigt die Unterschiede in den Vorgehensweisen, die erforderlich waren, als die Bereiche getrennt waren. Sie haben folgende Möglichkeiten:

- Markieren von Text im Konsolenbereich und Kopieren des markierten Texts in die Zwischenablage, um ihn in einem anderen Fenster einzufügen. Um Text zu markieren, ziehen Sie mit der Maus bei gedrückter linker Maustaste über den Text, den Sie erfassen möchten. Sie können Text auch markieren, indem Sie bei gedrückter **UMSCHALTTASTE** die Cursortasten verwenden. Drücken Sie dann STRG+C, oder klicken Sie auf der Symbolleiste auf das Symbol **Kopieren**.

- Einfügen des markierten Texts an der aktuellen Cursorposition. Klicken Sie auf der Symbolleiste auf das Symbol **Einfügen**.

- Löschen des gesamten Texts im Konsolenbereich. Sie können auf der Symbolleiste auf das Symbol **Konsolenbereich löschen** klicken, oder Sie führen den Befehl **Clear-Host** oder dessen Alias **cls** aus, um den Konsolenbereich zu löschen.

## <a name="see-also"></a>Weitere Informationen

- [Einführung in die Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)