---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Verbesserungen an der Konsole in WMF 5.1
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892925"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="0de73-103">Verbesserungen an der Konsole in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="0de73-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="0de73-104">Verbesserungen an der PowerShell-Konsole</span><span class="sxs-lookup"><span data-stu-id="0de73-104">PowerShell console improvements</span></span>

<span data-ttu-id="0de73-105">Die folgenden Änderungen wurden in WMF 5.1 an powershell.exe vorgenommen, um die Konsolenumgebung zu verbessern:</span><span class="sxs-lookup"><span data-stu-id="0de73-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="0de73-106">Unterstützung von VT100</span><span class="sxs-lookup"><span data-stu-id="0de73-106">VT100 support</span></span>

<span data-ttu-id="0de73-107">Windows 10 unterstützt nun [VT100-Escapesequenzen](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="0de73-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="0de73-108">Bei der Berechnung von Tabellenbreiten ignoriert PowerShell bestimmte VT100-Escapesequenzen für die Formatierung.</span><span class="sxs-lookup"><span data-stu-id="0de73-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="0de73-109">PowerShell bietet nun auch eine neue API, die in Formatierungscode verwendet werden kann, um festzustellen, ob VT100 unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="0de73-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="0de73-110">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0de73-110">For example:</span></span>

```powershell
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

<span data-ttu-id="0de73-111">Es folgt ein vollständiges [Beispiel](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7), das zum Hervorheben von Übereinstimmungen aus `Select-String` verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="0de73-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span>
<span data-ttu-id="0de73-112">Speichern Sie das Beispiel in einer Datei namens `MatchInfo.format.ps1xml`. Verwenden Sie sie in Ihrem Profil oder an anderer Stelle, und führen Sie `Update-FormatData -Prepend MatchInfo.format.ps1xml` aus.</span><span class="sxs-lookup"><span data-stu-id="0de73-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="0de73-113">Beachten Sie, dass VT100-Escapesequenzen erst ab dem Anniversary-Update für Windows 10 unterstützt werden. Von vorherigen Systemen werden sie nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0de73-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="0de73-114">Unterstützung des vi-Modus in PSReadline</span><span class="sxs-lookup"><span data-stu-id="0de73-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="0de73-115">[PSReadline](https://github.com/lzybkr/PSReadLine) bietet nun Unterstützung den für vi-Modus.</span><span class="sxs-lookup"><span data-stu-id="0de73-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="0de73-116">Führen Sie zur Verwendung des vi-Modus `Set-PSReadlineOption -EditMode Vi` aus.</span><span class="sxs-lookup"><span data-stu-id="0de73-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="0de73-117">Umgeleitetes stdin mit interaktiver Eingabe</span><span class="sxs-lookup"><span data-stu-id="0de73-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="0de73-118">In früheren Versionen war das Starten von PowerShell mit `powershell -File -` erforderlich, wenn stdin umgeleitet wurde und Sie Befehle interaktiv eingeben wollten.</span><span class="sxs-lookup"><span data-stu-id="0de73-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="0de73-119">Bei WMF 5.1 ist diese schwer zu findende Option nicht mehr erforderlich.</span><span class="sxs-lookup"><span data-stu-id="0de73-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="0de73-120">Sie können PowerShell ohne Optionen starten, z. B. mit `powershell`.</span><span class="sxs-lookup"><span data-stu-id="0de73-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="0de73-121">Beachten Sie, dass PSReadline derzeit umgeleitetes stdin nicht unterstützt und dass die integrierte Bearbeitungsumgebung für die Befehlszeile mit umgeleitetem stdin sehr eingeschränkt ist. Beispielsweise funktionieren die Pfeiltasten nicht.</span><span class="sxs-lookup"><span data-stu-id="0de73-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="0de73-122">In einer künftigen Version von PSReadline soll dieses Problem behoben werden.</span><span class="sxs-lookup"><span data-stu-id="0de73-122">A future release of PSReadline should address this issue.</span></span>