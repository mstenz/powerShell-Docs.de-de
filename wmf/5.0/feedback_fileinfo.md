---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225639"
---
# <a name="updates-to-fileinfo-object"></a>Aktualisierungen beim „FileInfo“-Objekt
Dateiversionsinformationen können irreführend sein, insbesondere in Fällen, bei denen die Datei geändert wurde. Diese WMF 5.0-Version fügt FileInfo-Objekten die neuen Skripteigenschaften **FileVersionRaw** und **ProductVersionRaw** hinzu. Es folgen die für „powershell.exe“ angezeigten Eigenschaften (vorausgesetzt wird, dass „$pid“ die ID des PowerShell-Prozesses ist):

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
