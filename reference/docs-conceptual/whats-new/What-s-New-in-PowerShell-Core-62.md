---
title: Neuerungen in PowerShell Core 6.2
description: Neue Funktionen und Änderungen in PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750051"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="dde22-103">Neuerungen in PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="dde22-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="dde22-104">Im Folgenden finden Sie eine Auswahl der wichtigsten Funktionen und Änderungen, die in PowerShell Core 6.2 eingeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="dde22-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="dde22-105">Außerdem wurden viele Fehler behoben und **unzählige Verbesserungen** vorgenommen, die PowerShell schneller und stabiler machen, aber vielleicht weniger aufregend klingen.</span><span class="sxs-lookup"><span data-stu-id="dde22-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="dde22-106">Eine vollständige Liste der Änderungen finden Sie unter [Changelog (Änderungsprotokoll)](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="dde22-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="dde22-107">Ein großer Dank geht an alle [Mitwirkende aus der Community](https://github.com/PowerShell/PowerShell/graphs/contributors), die dieses Release überhaupt möglich gemacht haben, und von denen weiter unten nur eine kleine Auswahl genannt wird.</span><span class="sxs-lookup"><span data-stu-id="dde22-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="dde22-108">Engineupdates und Fixes</span><span class="sxs-lookup"><span data-stu-id="dde22-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="dde22-109">Hinzufügen von Warnmeldungen für das PowerShell-Cmdlet zum Aktivieren/Deaktivieren des Remotings ([9203][])</span><span class="sxs-lookup"><span data-stu-id="dde22-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="dde22-110">Korrektur für `FormatTable` Remotedeserialisierungsregression ([9116][])</span><span class="sxs-lookup"><span data-stu-id="dde22-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="dde22-111">Aktualisieren der aufgabenbasierten `async`-APIs, die PowerShell hinzugefügt werden, um ein Aufgabenobjekt direkt zurückzugeben ([9079][])</span><span class="sxs-lookup"><span data-stu-id="dde22-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="dde22-112">Hinzufügen von 5 `InvokeAsync`-Überladungen und `StopAsync` zum `PowerShell`-Typ ([8056][]) (Vielen Dank @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="dde22-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="dde22-113">Allgemeine Cmdletupdates und Korrekturen</span><span class="sxs-lookup"><span data-stu-id="dde22-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="dde22-114">Aktivieren von `SecureString`-Cmdlets für Nicht-Windows durch Speichern von Nur-Text ([9199][])</span><span class="sxs-lookup"><span data-stu-id="dde22-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="dde22-115">Hinzufügen der „Veraltet“-Nachricht zu `Send-MailMessage` ([9178][])</span><span class="sxs-lookup"><span data-stu-id="dde22-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="dde22-116">Beheben von `Restart-Computer` zum Funktionieren auf `localhost`, wenn WinRM nicht vorhanden ist ([9160][])</span><span class="sxs-lookup"><span data-stu-id="dde22-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="dde22-117">Veranlassen, dass `Start-Job` einen Fehler mit Abbruch auslöst, wenn PowerShell gehostet wird ([9128][])</span><span class="sxs-lookup"><span data-stu-id="dde22-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="dde22-118">Updateversion für `PowerShell.Native` und Hostingtests ([8983][])</span><span class="sxs-lookup"><span data-stu-id="dde22-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="dde22-119">Wichtige Änderungen</span><span class="sxs-lookup"><span data-stu-id="dde22-119">Breaking Changes</span></span>

<span data-ttu-id="dde22-120">Beheben des -NoEnumerate-Verhaltens in Write-Output zur Konsistenz mit Windows PowerShell ([9069][]) (Vielen Dank @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="dde22-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

<!-- Link references -->
[8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[9203]: https://github.com/PowerShell/PowerShell/pull/9203
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
