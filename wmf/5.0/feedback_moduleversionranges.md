---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: e2c9233734a6ede04e8ec2bbad05950cbb31cbba
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057504"
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="e20f8-102">Modulunterstützung für das Deklarieren von Versionsbereichen (1.\* usw.)</span><span class="sxs-lookup"><span data-stu-id="e20f8-102">Modules support for declaring version ranges (1.\*, etc)</span></span>
<span data-ttu-id="e20f8-103">In Kombination mit **-MinimumVersion** ermöglicht **-MaximumVersion** Benutzern nun das Abrufen/Importieren von Modulen innerhalb eines bestimmten Bereichs.</span><span class="sxs-lookup"><span data-stu-id="e20f8-103">Combined with **-MinimumVersion**, **-MaximumVersion** now allows user to get/import module within specific range.</span></span> <span data-ttu-id="e20f8-104">Der Parameter unterstützt auch **.**\*.</span><span class="sxs-lookup"><span data-stu-id="e20f8-104">The parameter also support **.**\*.</span></span> <span data-ttu-id="e20f8-105">Im folgenden Beispiel wird die Funktionsweise gezeigt:</span><span class="sxs-lookup"><span data-stu-id="e20f8-105">The following example shows how it works:</span></span>

<span data-ttu-id="e20f8-106">Nun können Sie **-MinimumVersion** und **-MaximumVersion** kombinieren, um das Modul innerhalb eines bestimmten Bereichs zu importieren:</span><span class="sxs-lookup"><span data-stu-id="e20f8-106">Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:</span></span>

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
