---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225690"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="afed7-102">Modulunterstützung für das Deklarieren von Versionsbereichen (1.\* usw.)</span><span class="sxs-lookup"><span data-stu-id="afed7-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="afed7-103">In Kombination mit **-MinimumVersion** ermöglicht **-MaximumVersion** Benutzern nun das Abrufen/Importieren von Modulen innerhalb eines bestimmten Bereichs.</span><span class="sxs-lookup"><span data-stu-id="afed7-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="afed7-104">Der Parameter unterstützt auch **.**\*.</span><span class="sxs-lookup"><span data-stu-id="afed7-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="afed7-105">Im folgenden Beispiel wird die Funktionsweise gezeigt:</span><span class="sxs-lookup"><span data-stu-id="afed7-105">The following example shows how it works:</span></span>

<span data-ttu-id="afed7-106">Nun können Sie **-MinimumVersion** und **-MaximumVersion** kombinieren, um das Modul innerhalb eines bestimmten Bereichs zu importieren:</span><span class="sxs-lookup"><span data-stu-id="afed7-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

```powershell
PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```
