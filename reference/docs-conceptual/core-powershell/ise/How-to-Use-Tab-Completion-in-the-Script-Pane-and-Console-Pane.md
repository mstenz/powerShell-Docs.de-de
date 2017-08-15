---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: "Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich"
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: ba8d0af7e7fc0f1df9f65116be899097b0a97a3c
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich
Vervollständigung mit der TAB-TASTE bietet automatische Hilfe, wenn Sie eine Eingabe im Skriptbereich oder Befehlsbereich vornehmen. Gehen Sie folgendermaßen vor, um dieses Feature zu nutzen:

## <a name="to-automatically-complete-a-command-entry"></a>So wird ein Befehlseintrag automatisch vervollständigt
Geben Sie im Befehlsbereich oder Skriptbereich einige Zeichen eines Befehls ein, und drücken Sie dann die TAB-TASTE, um den gewünschten Vervollständigungstext auszuwählen. Gibt es mehrere Elemente, die mit dem Text beginnen, den Sie ursprünglich eingegeben haben, drücken Sie weiterhin die TAB-TASTE, bis das gewünschte Element angezeigt wird. Vervollständigung mit der TAB-TASTE kann als Unterstützung beim Eingeben eines Cmdlet-Namens, Parameternamens, Variablennamens, Objekteigenschaftsnamens oder Dateipfads verwendet werden.

> [!NOTE]
> Im Skriptbereich wird durch Drücken der TAB-TASTE ein Befehl nur dann automatisch vervollständigt, wenn Sie PS1-, PSD1- oder PSM1-Dateien bearbeiten. Vervollständigung mit der TAB-TASTE funktioniert immer, wenn Sie im Befehlsbereich eingeben.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>So wird ein Parametereintrag eines Cmdlets automatisch vervollständigt
Geben Sie im Befehlsbereich oder Skriptbereich ein Cmdlet gefolgt von einem Bindestrich ein, und drücken Sie dann die TAB-TASTE.

Geben Sie z. B. `Get-Process -` ein, und drücken Sie dann mehrmals die TAB-TASTE, um jeden der Parameter des Cmdlets der Reihe nach anzuzeigen.

## <a name="see-also"></a>Weitere Informationen
- [Verwenden von Windows PowerShell ISE](using-the-windows-powershell-ise.md)
- [Erstellen einer PowerShell-Registerkarte](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

