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
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="a1cc8-102">Aktualisierungen beim „FileInfo“-Objekt</span><span class="sxs-lookup"><span data-stu-id="a1cc8-102">Updates to FileInfo object</span></span>
<span data-ttu-id="a1cc8-103">Dateiversionsinformationen können irreführend sein, insbesondere in Fällen, bei denen die Datei geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="a1cc8-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="a1cc8-104">Diese WMF 5.0-Version fügt FileInfo-Objekten die neuen Skripteigenschaften **FileVersionRaw** und **ProductVersionRaw** hinzu.</span><span class="sxs-lookup"><span data-stu-id="a1cc8-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="a1cc8-105">Es folgen die für „powershell.exe“ angezeigten Eigenschaften (vorausgesetzt wird, dass „$pid“ die ID des PowerShell-Prozesses ist):</span><span class="sxs-lookup"><span data-stu-id="a1cc8-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
