---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 12c47d3583274e58edbd2171fef50c779aac9fce
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Modulunterstützung für das Deklarieren von Versionsbereichen (1.* usw.)
In Kombination mit **-MinimumVersion** ermöglicht **-MaximumVersion** Benutzern nun das Abrufen/Importieren von Modulen innerhalb eines bestimmten Bereichs. Der Parameter unterstützt auch **.** \*. Im folgenden Beispiel wird die Funktionsweise gezeigt:

```powershell
Now, you can combine **-MinimumVersion** and **-MaximumVersion** to import module within specific range:

PS C:\> Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*

VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```