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
# <a name="whats-new-in-powershell-core-62"></a>Neuerungen in PowerShell Core 6.2

Im Folgenden finden Sie eine Auswahl der wichtigsten Funktionen und Änderungen, die in PowerShell Core 6.2 eingeführt wurden.

Außerdem wurden viele Fehler behoben und **unzählige Verbesserungen** vorgenommen, die PowerShell schneller und stabiler machen, aber vielleicht weniger aufregend klingen.
Eine vollständige Liste der Änderungen finden Sie unter [Changelog (Änderungsprotokoll)](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md) auf GitHub.

Ein großer Dank geht an alle [Mitwirkende aus der Community](https://github.com/PowerShell/PowerShell/graphs/contributors), die dieses Release überhaupt möglich gemacht haben, und von denen weiter unten nur eine kleine Auswahl genannt wird.

## <a name="engine-updates-and-fixes"></a>Engineupdates und Fixes

- Hinzufügen von Warnmeldungen für das PowerShell-Cmdlet zum Aktivieren/Deaktivieren des Remotings ([9203][])
- Korrektur für `FormatTable` Remotedeserialisierungsregression ([9116][])
- Aktualisieren der aufgabenbasierten `async`-APIs, die PowerShell hinzugefügt werden, um ein Aufgabenobjekt direkt zurückzugeben ([9079][])
- Hinzufügen von 5 `InvokeAsync`-Überladungen und `StopAsync` zum `PowerShell`-Typ ([8056][]) (Vielen Dank @KirkMunro!)

## <a name="general-cmdlet-updates-and-fixes"></a>Allgemeine Cmdletupdates und Korrekturen

- Aktivieren von `SecureString`-Cmdlets für Nicht-Windows durch Speichern von Nur-Text ([9199][])
- Hinzufügen der „Veraltet“-Nachricht zu `Send-MailMessage` ([9178][])
- Beheben von `Restart-Computer` zum Funktionieren auf `localhost`, wenn WinRM nicht vorhanden ist ([9160][])
- Veranlassen, dass `Start-Job` einen Fehler mit Abbruch auslöst, wenn PowerShell gehostet wird ([9128][])
- Updateversion für `PowerShell.Native` und Hostingtests ([8983][])

## <a name="breaking-changes"></a>Wichtige Änderungen

Beheben des -NoEnumerate-Verhaltens in Write-Output zur Konsistenz mit Windows PowerShell ([9069][]) (Vielen Dank @vexx32!)

<!-- Link references -->
[8056]: https://github.com/PowerShell/PowerShell/pull/8056
[8983]: https://github.com/PowerShell/PowerShell/pull/8983
[9069]: https://github.com/PowerShell/PowerShell/pull/9069
[9079]: https://github.com/PowerShell/PowerShell/pull/9079
[9116]: https://github.com/PowerShell/PowerShell/pull/9116
[9128]: https://github.com/PowerShell/PowerShell/pull/9128
[9160]: https://github.com/PowerShell/PowerShell/pull/9160
[9178]: https://github.com/PowerShell/PowerShell/pull/9178
[9199]: https://github.com/PowerShell/PowerShell/pull/9199
[9203]: https://github.com/PowerShell/PowerShell/pull/9203
