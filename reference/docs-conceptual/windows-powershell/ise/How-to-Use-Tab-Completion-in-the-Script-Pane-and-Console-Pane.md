---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich
ms.openlocfilehash: 07cf9ff75db8d33ed018542153bfcd7503035e40
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808826"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="cd614-103">Verwenden von Vervollständigung mit der TAB-TASTE im Skriptbereich und Konsolenbereich</span><span class="sxs-lookup"><span data-stu-id="cd614-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="cd614-104">Vervollständigung mit der TAB-TASTE bietet automatische Hilfe, wenn Sie eine Eingabe im Skriptbereich oder Befehlsbereich vornehmen.</span><span class="sxs-lookup"><span data-stu-id="cd614-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="cd614-105">Gehen Sie folgendermaßen vor, um dieses Feature zu nutzen:</span><span class="sxs-lookup"><span data-stu-id="cd614-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="cd614-106">So wird ein Befehlseintrag automatisch vervollständigt</span><span class="sxs-lookup"><span data-stu-id="cd614-106">To automatically complete a command entry</span></span>

<span data-ttu-id="cd614-107">Geben Sie im Befehlsbereich oder Skriptbereich einige Zeichen eines Befehls ein, und drücken Sie dann die <kbd>TAB-TASTE</kbd>, um den gewünschten Vervollständigungstext auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="cd614-107">In the Command Pane or Script Pane, type a few characters of a command and then press <kbd>TAB</kbd> to select the desired completion text.</span></span> <span data-ttu-id="cd614-108">Gibt es mehrere Elemente, die mit dem Text beginnen, den Sie ursprünglich eingegeben haben, drücken Sie so lange die <kbd>TAB-TASTE</kbd>, bis das gewünschte Element angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="cd614-108">If multiple items begin with the text that you initially typed, then continue pressing <kbd>TAB</kbd> until the item you want appears.</span></span> <span data-ttu-id="cd614-109">Vervollständigung mit der TAB-TASTE kann als Unterstützung beim Eingeben eines Cmdlet-Namens, Parameternamens, Variablennamens, Objekteigenschaftsnamens oder Dateipfads verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="cd614-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="cd614-110">Im Skriptbereich wird durch Drücken der <kbd>TAB-TASTE</kbd> ein Befehl nur dann automatisch vervollständigt, wenn Sie `.ps1`-, `.psd1`- oder `.psm1`-Dateien bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="cd614-110">In the Script Pane, pressing <kbd>TAB</kbd> will automatically complete a command only when you are editing `.ps1`, `.psd1`, or `.psm1` files.</span></span> <span data-ttu-id="cd614-111">Vervollständigung mit der TAB-TASTE funktioniert immer, wenn Sie im Befehlsbereich eingeben.</span><span class="sxs-lookup"><span data-stu-id="cd614-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="cd614-112">So wird ein Parametereintrag eines Cmdlets automatisch vervollständigt</span><span class="sxs-lookup"><span data-stu-id="cd614-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="cd614-113">Geben Sie im Befehlsbereich oder Skriptbereich ein Cmdlet gefolgt von einem Bindestrich ein, und drücken Sie dann die <kbd>TAB-TASTE</kbd>.</span><span class="sxs-lookup"><span data-stu-id="cd614-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press <kbd>TAB</kbd>.</span></span>

<span data-ttu-id="cd614-114">Geben Sie z. B. `Get-Process -` ein, und drücken Sie dann mehrmals die <kbd>TAB-TASTE</kbd>, um jeden der Parameter des Cmdlets der Reihe nach anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="cd614-114">For example, type `Get-Process -` and then press <kbd>TAB</kbd> multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd614-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cd614-115">See Also</span></span>

- [<span data-ttu-id="cd614-116">Einführung in die Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="cd614-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="cd614-117">Erstellen einer PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="cd614-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
