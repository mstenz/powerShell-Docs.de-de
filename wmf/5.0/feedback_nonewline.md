---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 8c6a7d55e40f64bde6c2a2074ca3adb9cd210322
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="nonewline-parameter"></a><span data-ttu-id="18cda-102">„NoNewLine“-Parameter</span><span class="sxs-lookup"><span data-stu-id="18cda-102">NoNewLine parameter</span></span>
<span data-ttu-id="18cda-103">**Out-File**, **Add-Content** und **Set-Content** haben nun den neuen Schalter **–NoNewline**, der einfach eine neue Zeile hinter der Ausgabe weglässt.</span><span class="sxs-lookup"><span data-stu-id="18cda-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="18cda-104">Ohne Angabe von **–NoNewline** befindet sich jedes Fragment in einer getrennten Zeile:</span><span class="sxs-lookup"><span data-stu-id="18cda-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```

