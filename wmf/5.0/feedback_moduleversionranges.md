---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 89e908969641afd9ad9541dcfedcc8eb6315d07c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="f3d55-102">Modulunterstützung für das Deklarieren von Versionsbereichen (1.\* usw.)</span><span class="sxs-lookup"><span data-stu-id="f3d55-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="f3d55-103">In Kombination mit **-MinimumVersion** ermöglicht **-MaximumVersion** Benutzern nun das Abrufen/Importieren von Modulen innerhalb eines bestimmten Bereichs.</span><span class="sxs-lookup"><span data-stu-id="f3d55-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="f3d55-104">Der Parameter unterstützt auch **.** \*.</span><span class="sxs-lookup"><span data-stu-id="f3d55-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="f3d55-105">Im folgenden Beispiel wird die Funktionsweise gezeigt:</span><span class="sxs-lookup"><span data-stu-id="f3d55-105">The following example shows how it works:</span></span>

<span data-ttu-id="f3d55-106">Sie können jetzt kombinieren **"- MinimumVersion"** und **- MaximumVersion** Modulen innerhalb eines bestimmten Bereichs zu importieren:</span><span class="sxs-lookup"><span data-stu-id="f3d55-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
