---
ms.date: 04/28/2020
title: Verwenden experimenteller Features in PowerShell
description: In diesem Artikel wird beschrieben, welche experimentellen Features verfügbar sind und wie sie verwendet werden.
ms.openlocfilehash: 72a4309d6eeede4cd2ff7c38ce8e99ce3ace30eb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809186"
---
# <a name="using-experimental-features-in-powershell"></a>Verwenden experimenteller Features in PowerShell

Die Unterstützung experimenteller Features in PowerShell stellt einen Mechanismus bereit, über den experimentelle Features und vorhandene stabile Features in PowerShell oder PowerShell-Modulen parallel genutzt werden können.

Ein experimentelles Feature ist ein Feature, dessen Design noch nicht finalisiert wurde. Das Feature wird bereitgestellt, damit die Benutzer es testen und Feedback dazu senden können. Sobald ein experimentelles Feature finalisiert wurde, werden die Designänderungen zu Breaking Changes.

> [!CAUTION]
> Experimentelle Features sind nicht für den Einsatz in der Produktion vorgesehen, da Auswirkungen auf die Lauffähigkeit möglich sind. Experimentelle Features werden nicht offiziell unterstützt. Wir freuen uns jedoch über Feedback und Fehlermeldungen. Sie können Probleme im [GitHub-Quellrepository](https://github.com/PowerShell/PowerShell/issues/new/choose) melden.

Weitere Informationen zum Aktivieren oder Deaktivieren dieser Features finden Sie unter [Grundlegendes zu experimentellen Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).

## <a name="available-features"></a>Verfügbare Features

Dieser Artikel beschreibt, welche experimentellen Features verfügbar sind und wie sie verwendet werden.

|                            Name                            |   6.2   |   7.0   | 7.1 (Vorschau) |
| ---------------------------------------------------------- | :-----: | :-----: | :-----------: |
| PSTempDrive (allgemeine Unterstützung in PS 7.0 und höher)                        | &check; |         |               |
| PSUseAbbreviationExpansion (allgemeine Unterstützung in PS 7.0 und höher)         | &check; |         |               |
| PSCommandNotFoundSuggestion                                | &check; | &check; |    &check;    |
| PSImplicitRemotingBatching                                 | &check; | &check; |    &check;    |
| Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace |         | &check; |    &check;    |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; |    &check;    |
| PSNullConditionalOperators                                 |         | &check; |    &check;    |
| PSUnixFileStat (nur Nicht-Windows)                          |         | &check; |    &check;    |
| PSNativePSPathResolution                                   |         |         |    &check;    |
| PSCultureInvariantReplaceOperator                          |         |         |    &check;    |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a>Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace

Aktiviert den Parameter **BreakAll** für die Cmdlets `Debug-Runspace` und `Debug-Job`, damit Benutzer entscheiden können, ob PowerShell an der aktuellen Stelle sofort unterbrechen soll, wenn ein Debugger angefügt wird.

## <a name="pscommandnotfoundsuggestion"></a>PSCommandNotFoundSuggestion

Empfiehlt potenzielle Befehle basierend auf einer Fuzzysuche nach einer **CommandNotFoundException**.

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a>PSCultureInvariantReplaceOperator

Wenn der linke Operand in einer `-replace`-Operatoranweisung keine Zeichenfolge ist, wird dieser Operand in eine Zeichenfolge konvertiert.

Ist dieses Feature deaktiviert, führt der `-replace`-Operator eine Zeichenfolgenkonvertierung mit Kulturerkennung durch.
Wenn Ihre Kultur beispielsweise auf „Französisch (fr)“ festgelegt ist, wird der Wert `1.2` in die Zeichenfolge `1,2` konvertiert.

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

Bei aktiviertem Feature:

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a>PSDesiredStateConfiguration.InvokeDscResource

Aktiviert die Kompilierung in MOF auf Nicht-Windows-Systemen sowie die Verwendung von `Invoke-DSCResource` ohne LCM.

## <a name="psimplicitremotingbatching"></a>PSImplicitRemotingBatching

Dieses Feature untersucht den Befehl, der in die Shell eingegeben wurde. Wenn alle Befehle implizite Remotingproxybefehle sind, die eine einfache Pipeline bilden, werden die Befehle in einem Batch zusammengefasst und als eine einzige Remotepipeline aufgerufen.

Beispiel:

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

Wie oben gezeigt, werden bei Aktivierung des Features für die Batcherstellung alle drei impliziten Remotingproxybefehle (`Get-AllProcesses`, `Select-Custom`, `Group-Stuff`) in der Remotesitzung ausgeführt, und es wird nur das Ergebnis der Pipeline an den Client zurückgegeben. Dies verringert die Datenmenge, die zwischen Client und Remotesitzung gesendet wird und reduziert außerdem den Aufwand für die Objektserialisierung und -deserialisierung.

## <a name="psnativepspathresolution"></a>PSNativePSPathResolution

Bei Übergabe eines PSDrive-Pfads mit Verwendung des FileSystem-Anbieters an einen nativen Befehl wird der aufgelöste Dateipfad an den nativen Pfad Befehl übergeben. Dies bedeutet, dass ein Befehl wie `code temp:/test.txt` jetzt wie erwartet funktioniert.

Darüber hinaus gilt unter Windows Folgendes: Wenn der Pfad mit `~` beginnt, wird dieser in den vollständigen Pfad aufgelöst und an den nativen Befehl übergeben. In beiden Fällen wird der Pfad auf die Verzeichnistrennzeichen für das jeweilige Betriebssystem normalisiert.

- Handelt es sich bei dem Pfad nicht um ein PSDrive oder `~` (unter Windows), erfolgt keine Pfadnormalisierung.
- Wird der Pfad in einfachen Anführungszeichen angegeben, wird er nicht aufgelöst und als Literal betrachtet.

## <a name="psnullconditionaloperators"></a>PSNullConditionalOperators

Hiermit werden neue Operatoren für den NULL-bedingten Memberzugriff eingeführt: `?.` und `?[]`. Operatoren für den NULL-Memberzugriff können für Skalartypen und Arraytypen verwendet werden. Geben Sie den Wert des Members zurück, auf den zugegriffen wurde, wenn die Variable ungleich NULL ist. Lautet der Wert der Variablen NULL, geben Sie NULL zurück.

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

Es wird auf die Eigenschaft `propname` zugegriffen, und ihr Wert wird nur zurückgegeben, wenn `$x` nicht NULL lautet. Ähnlich wird der Indexer nur verwendet, wenn `$x` nicht NULL lautet. Wenn `$x` NULL ist, wird NULL zurückgegeben.

Die Operatoren `?.` und `?[]` sind Memberzugriffsoperatoren und lassen kein Leerzeichen zwischen dem Variablennamen und dem Operator zu.

Da PowerShell `?` als Bestandteil des Variablennamens zulässt, muss Eindeutigkeit gewährleistet werden, wenn Operatoren ohne Leerzeichen zwischen dem Variablennamen und dem Operator verwendet werden. Zur Unterscheidung muss der Name der Variablen in `{}` eingeschlossen werden. Beispiel: `${x?}?.propertyName` oder `${y}?[0]`.

## <a name="pstempdrive"></a>PSTempDrive

Erstellt das PSDrive `TEMP:`, das dem temporären Verzeichnispfad des Benutzers zugeordnet ist.

> [!NOTE]
> Dieses Feature befindet sich nicht mehr in der experimentellen Phase und wird in PowerShell 7 und höher jetzt allgemein unterstützt.

## <a name="psunixfilestat"></a>PSUnixFileStat

Dieses Feature bietet ein neues Verhalten zum Einschließen von Daten aus der **stat**-API unter Unix in die Ausgabe des Dateisystemanbieters, um eine Unix-ähnlichere Dateiliste zu ermöglichen. Es wird im Dateisystemanbieter eine neue NoteProperty namens **UnixStat** hinzugefügt, die einen gemeinsamen Ausdruck der `stat(2)`-API aus dem zugrunde liegenden Unix-Typsystem enthält.

Die Ausgabe von `Get-ChildItem` sollte ungefähr wie folgt aussehen:

```powershell
PS> dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

Dieses Feature aktiviert die Vervollständigung abgekürzter Cmdlets und Funktionen mit der TAB-TASTE:

Beispiel:

- `Import-PowerShellDataFile` gibt `i-psdf<tab>` zurück.
- `u-akvmssdr<tab>` gibt `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval` zurück.

Dies funktioniert nur für die Vervollständigung mit der TAB-TASTE (interaktive Verwendung), deshalb ist `i-psdf` kein gültiger Name eines Cmdlets in einem Skript.

> [!NOTE]
> Dieses Feature befindet sich nicht mehr in der experimentellen Phase und wird in PowerShell 7 und höher jetzt allgemein unterstützt.
