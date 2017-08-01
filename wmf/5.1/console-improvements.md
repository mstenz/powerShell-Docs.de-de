---
title: Verbesserungen an der Konsole in WMF 5.1 (Vorschau)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 574fec8e1f4948021988d8489532d7325277fed6
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="console-improvements-in-wmf-51-preview"></a><span data-ttu-id="f3dd3-103">Verbesserungen an der Konsole in WMF 5.1 (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="f3dd3-103">Console Improvements in WMF 5.1 (Preview)</span></span>#

## <a name="powershell-console-improvements"></a><span data-ttu-id="f3dd3-104">Verbesserungen an der PowerShell-Konsole</span><span class="sxs-lookup"><span data-stu-id="f3dd3-104">PowerShell console improvements</span></span>

<span data-ttu-id="f3dd3-105">Die folgenden Änderungen wurden in WMF 5.1 an powershell.exe vorgenommen, um die Konsolenumgebung zu verbessern:</span><span class="sxs-lookup"><span data-stu-id="f3dd3-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="f3dd3-106">Unterstützung von VT100</span><span class="sxs-lookup"><span data-stu-id="f3dd3-106">VT100 support</span></span>

<span data-ttu-id="f3dd3-107">Windows 10 unterstützt nun [VT100-Escapesequenzen](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="f3dd3-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="f3dd3-108">Bei der Berechnung von Tabellenbreiten ignoriert PowerShell bestimmte VT100-Escapesequenzen für die Formatierung.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="f3dd3-109">PowerShell bietet nun auch eine neue API, die in Formatierungscode verwendet werden kann, um festzustellen, ob VT100 unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="f3dd3-110">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="f3dd3-110">For example:</span></span>

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
<span data-ttu-id="f3dd3-111">Es folgt ein vollständiges [Beispiel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7), das zum Hervorheben von Übereinstimmungen aus „Select-String“ verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="f3dd3-112">Speichern Sie das Beispiel in einer Datei namens `MatchInfo.format.ps1xml`. Verwenden Sie sie in Ihrem Profil oder an anderer Stelle, und führen Sie `Update-FormatData -Prepend MatchInfo.format.ps1xml` aus.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="f3dd3-113">Beachten Sie, dass VT100-Escapesequenzen erst ab dem Anniversary-Update für Windows 10 unterstützt werden. Von vorherigen Systemen werden sie nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>   

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="f3dd3-114">Unterstützung des vi-Modus in PSReadline</span><span class="sxs-lookup"><span data-stu-id="f3dd3-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="f3dd3-115">[PSReadline](https://github.com/lzybkr/PSReadLine) bietet nun Unterstützung den für vi-Modus.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="f3dd3-116">Führen Sie zur Verwendung des vi-Modus `Set-PSReadline -EditMode vi` aus.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-116">To use vi mode, run `Set-PSReadline -EditMode vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="f3dd3-117">Umgeleitetes stdin mit interaktiver Eingabe</span><span class="sxs-lookup"><span data-stu-id="f3dd3-117">Redirected stdin with interactive input</span></span> 

<span data-ttu-id="f3dd3-118">In früheren Versionen war das Starten von PowerShell mit `powershell -File -` erforderlich, wenn stdin umgeleitet wurde und Sie Befehle interaktiv eingeben wollten.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="f3dd3-119">Bei WMF 5.1 ist diese schwer zu findende Option nicht mehr erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="f3dd3-120">Sie können PowerShell ohne Optionen starten, z. B. mit `powershell`.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="f3dd3-121">Beachten Sie, dass PSReadline derzeit umgeleitetes stdin nicht unterstützt und dass die integrierte Bearbeitungsumgebung für die Befehlszeile mit umgeleitetem stdin sehr eingeschränkt ist. Beispielsweise funktionieren die Pfeiltasten nicht.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="f3dd3-122">In einer künftigen Version von PSReadline soll dieses Problem behoben werden.</span><span class="sxs-lookup"><span data-stu-id="f3dd3-122">A future release of PSReadline should address this issue.</span></span>   
