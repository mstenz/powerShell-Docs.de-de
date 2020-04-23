---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich
ms.openlocfilehash: 07cf9ff75db8d33ed018542153bfcd7503035e40
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75737082"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich

Vervollständigung mit der TAB-TASTE bietet automatische Hilfe, wenn Sie eine Eingabe im Skriptbereich oder Befehlsbereich vornehmen. Gehen Sie folgendermaßen vor, um dieses Feature zu nutzen:

## <a name="to-automatically-complete-a-command-entry"></a>So wird ein Befehlseintrag automatisch vervollständigt

Geben Sie im Befehlsbereich oder Skriptbereich einige Zeichen eines Befehls ein, und drücken Sie dann die <kbd>TAB-TASTE</kbd>, um den gewünschten Vervollständigungstext auszuwählen. Gibt es mehrere Elemente, die mit dem Text beginnen, den Sie ursprünglich eingegeben haben, drücken Sie so lange die <kbd>TAB-TASTE</kbd>, bis das gewünschte Element angezeigt wird. Vervollständigung mit der TAB-TASTE kann als Unterstützung beim Eingeben eines Cmdlet-Namens, Parameternamens, Variablennamens, Objekteigenschaftsnamens oder Dateipfads verwendet werden.

> [!NOTE]
> Im Skriptbereich wird durch Drücken der <kbd>TAB-TASTE</kbd> ein Befehl nur dann automatisch vervollständigt, wenn Sie `.ps1`-, `.psd1`- oder `.psm1`-Dateien bearbeiten. Vervollständigung mit der TAB-TASTE funktioniert immer, wenn Sie im Befehlsbereich eingeben.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>So wird ein Parametereintrag eines Cmdlets automatisch vervollständigt

Geben Sie im Befehlsbereich oder Skriptbereich ein Cmdlet gefolgt von einem Bindestrich ein, und drücken Sie dann die <kbd>TAB-TASTE</kbd>.

Geben Sie z. B. `Get-Process -` ein, und drücken Sie dann mehrmals die <kbd>TAB-TASTE</kbd>, um jeden der Parameter des Cmdlets der Reihe nach anzuzeigen.

## <a name="see-also"></a>Weitere Informationen

- [Einführung in die Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Erstellen einer PowerShell-Registerkarte](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
