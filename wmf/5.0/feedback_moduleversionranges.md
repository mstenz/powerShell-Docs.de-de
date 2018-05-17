---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: f491e30859cbe6cbaa58f94389382ff231c52956
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Modulunterstützung für das Deklarieren von Versionsbereichen (1.* usw.)
In Kombination mit **-MinimumVersion** ermöglicht **-MaximumVersion** Benutzern nun das Abrufen/Importieren von Modulen innerhalb eines bestimmten Bereichs. Der Parameter unterstützt auch **.**\*. Im folgenden Beispiel wird die Funktionsweise gezeigt:

Nun können Sie **-MinimumVersion** und **-MaximumVersion** kombinieren, um das Modul innerhalb eines bestimmten Bereichs zu importieren:

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
