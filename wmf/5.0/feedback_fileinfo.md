---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 587f3f592f4aab53c95bbc6d37ea37d7f2364aec
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="198b8-102">Aktualisierungen beim „FileInfo“-Objekt</span><span class="sxs-lookup"><span data-stu-id="198b8-102">Updates to FileInfo object</span></span>
<span data-ttu-id="198b8-103">Dateiversionsinformationen können irreführend sein, insbesondere in Fällen, bei denen die Datei geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="198b8-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="198b8-104">Diese WMF 5.0-Version fügt FileInfo-Objekten die neuen Skripteigenschaften **FileVersionRaw** und **ProductVersionRaw** hinzu.</span><span class="sxs-lookup"><span data-stu-id="198b8-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="198b8-105">Es folgen die für „powershell.exe“ angezeigten Eigenschaften (vorausgesetzt wird, dass „$pid“ die ID des PowerShell-Prozesses ist):</span><span class="sxs-lookup"><span data-stu-id="198b8-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117

