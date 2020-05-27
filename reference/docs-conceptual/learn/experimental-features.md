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
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="83163-103">Verwenden experimenteller Features in PowerShell</span><span class="sxs-lookup"><span data-stu-id="83163-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="83163-104">Die Unterstützung experimenteller Features in PowerShell stellt einen Mechanismus bereit, über den experimentelle Features und vorhandene stabile Features in PowerShell oder PowerShell-Modulen parallel genutzt werden können.</span><span class="sxs-lookup"><span data-stu-id="83163-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="83163-105">Ein experimentelles Feature ist ein Feature, dessen Design noch nicht finalisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="83163-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="83163-106">Das Feature wird bereitgestellt, damit die Benutzer es testen und Feedback dazu senden können.</span><span class="sxs-lookup"><span data-stu-id="83163-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="83163-107">Sobald ein experimentelles Feature finalisiert wurde, werden die Designänderungen zu Breaking Changes.</span><span class="sxs-lookup"><span data-stu-id="83163-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="83163-108">Experimentelle Features sind nicht für den Einsatz in der Produktion vorgesehen, da Auswirkungen auf die Lauffähigkeit möglich sind.</span><span class="sxs-lookup"><span data-stu-id="83163-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="83163-109">Experimentelle Features werden nicht offiziell unterstützt.</span><span class="sxs-lookup"><span data-stu-id="83163-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="83163-110">Wir freuen uns jedoch über Feedback und Fehlermeldungen.</span><span class="sxs-lookup"><span data-stu-id="83163-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="83163-111">Sie können Probleme im [GitHub-Quellrepository](https://github.com/PowerShell/PowerShell/issues/new/choose) melden.</span><span class="sxs-lookup"><span data-stu-id="83163-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="83163-112">Weitere Informationen zum Aktivieren oder Deaktivieren dieser Features finden Sie unter [Grundlegendes zu experimentellen Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span><span class="sxs-lookup"><span data-stu-id="83163-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="83163-113">Verfügbare Features</span><span class="sxs-lookup"><span data-stu-id="83163-113">Available features</span></span>

<span data-ttu-id="83163-114">Dieser Artikel beschreibt, welche experimentellen Features verfügbar sind und wie sie verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="83163-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="83163-115">Name</span><span class="sxs-lookup"><span data-stu-id="83163-115">Name</span></span>                            |   <span data-ttu-id="83163-116">6.2</span><span class="sxs-lookup"><span data-stu-id="83163-116">6.2</span></span>   |   <span data-ttu-id="83163-117">7.0</span><span class="sxs-lookup"><span data-stu-id="83163-117">7.0</span></span>   | <span data-ttu-id="83163-118">7.1 (Vorschau)</span><span class="sxs-lookup"><span data-stu-id="83163-118">7.1 (preview)</span></span> |
| ---------------------------------------------------------- | :-----: | :-----: | :-----------: |
| <span data-ttu-id="83163-119">PSTempDrive (allgemeine Unterstützung in PS 7.0 und höher)</span><span class="sxs-lookup"><span data-stu-id="83163-119">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |               |
| <span data-ttu-id="83163-120">PSUseAbbreviationExpansion (allgemeine Unterstützung in PS 7.0 und höher)</span><span class="sxs-lookup"><span data-stu-id="83163-120">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |               |
| <span data-ttu-id="83163-121">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="83163-121">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; |    &check;    |
| <span data-ttu-id="83163-122">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="83163-122">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; |    &check;    |
| <span data-ttu-id="83163-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="83163-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; |    &check;    |
| <span data-ttu-id="83163-124">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="83163-124">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; |    &check;    |
| <span data-ttu-id="83163-125">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="83163-125">PSNullConditionalOperators</span></span>                                 |         | &check; |    &check;    |
| <span data-ttu-id="83163-126">PSUnixFileStat (nur Nicht-Windows)</span><span class="sxs-lookup"><span data-stu-id="83163-126">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; |    &check;    |
| <span data-ttu-id="83163-127">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="83163-127">PSNativePSPathResolution</span></span>                                   |         |         |    &check;    |
| <span data-ttu-id="83163-128">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="83163-128">PSCultureInvariantReplaceOperator</span></span>                          |         |         |    &check;    |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="83163-129">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="83163-129">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="83163-130">Aktiviert den Parameter **BreakAll** für die Cmdlets `Debug-Runspace` und `Debug-Job`, damit Benutzer entscheiden können, ob PowerShell an der aktuellen Stelle sofort unterbrechen soll, wenn ein Debugger angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="83163-130">Enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="83163-131">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="83163-131">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="83163-132">Empfiehlt potenzielle Befehle basierend auf einer Fuzzysuche nach einer **CommandNotFoundException**.</span><span class="sxs-lookup"><span data-stu-id="83163-132">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

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

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="83163-133">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="83163-133">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="83163-134">Wenn der linke Operand in einer `-replace`-Operatoranweisung keine Zeichenfolge ist, wird dieser Operand in eine Zeichenfolge konvertiert.</span><span class="sxs-lookup"><span data-stu-id="83163-134">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="83163-135">Ist dieses Feature deaktiviert, führt der `-replace`-Operator eine Zeichenfolgenkonvertierung mit Kulturerkennung durch.</span><span class="sxs-lookup"><span data-stu-id="83163-135">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="83163-136">Wenn Ihre Kultur beispielsweise auf „Französisch (fr)“ festgelegt ist, wird der Wert `1.2` in die Zeichenfolge `1,2` konvertiert.</span><span class="sxs-lookup"><span data-stu-id="83163-136">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="83163-137">Bei aktiviertem Feature:</span><span class="sxs-lookup"><span data-stu-id="83163-137">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="83163-138">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="83163-138">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="83163-139">Aktiviert die Kompilierung in MOF auf Nicht-Windows-Systemen sowie die Verwendung von `Invoke-DSCResource` ohne LCM.</span><span class="sxs-lookup"><span data-stu-id="83163-139">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="83163-140">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="83163-140">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="83163-141">Dieses Feature untersucht den Befehl, der in die Shell eingegeben wurde. Wenn alle Befehle implizite Remotingproxybefehle sind, die eine einfache Pipeline bilden, werden die Befehle in einem Batch zusammengefasst und als eine einzige Remotepipeline aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="83163-141">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="83163-142">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="83163-142">Example:</span></span>

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

<span data-ttu-id="83163-143">Wie oben gezeigt, werden bei Aktivierung des Features für die Batcherstellung alle drei impliziten Remotingproxybefehle (`Get-AllProcesses`, `Select-Custom`, `Group-Stuff`) in der Remotesitzung ausgeführt, und es wird nur das Ergebnis der Pipeline an den Client zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="83163-143">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="83163-144">Dies verringert die Datenmenge, die zwischen Client und Remotesitzung gesendet wird und reduziert außerdem den Aufwand für die Objektserialisierung und -deserialisierung.</span><span class="sxs-lookup"><span data-stu-id="83163-144">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="83163-145">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="83163-145">PSNativePSPathResolution</span></span>

<span data-ttu-id="83163-146">Bei Übergabe eines PSDrive-Pfads mit Verwendung des FileSystem-Anbieters an einen nativen Befehl wird der aufgelöste Dateipfad an den nativen Pfad Befehl übergeben.</span><span class="sxs-lookup"><span data-stu-id="83163-146">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="83163-147">Dies bedeutet, dass ein Befehl wie `code temp:/test.txt` jetzt wie erwartet funktioniert.</span><span class="sxs-lookup"><span data-stu-id="83163-147">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="83163-148">Darüber hinaus gilt unter Windows Folgendes: Wenn der Pfad mit `~` beginnt, wird dieser in den vollständigen Pfad aufgelöst und an den nativen Befehl übergeben.</span><span class="sxs-lookup"><span data-stu-id="83163-148">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="83163-149">In beiden Fällen wird der Pfad auf die Verzeichnistrennzeichen für das jeweilige Betriebssystem normalisiert.</span><span class="sxs-lookup"><span data-stu-id="83163-149">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="83163-150">Handelt es sich bei dem Pfad nicht um ein PSDrive oder `~` (unter Windows), erfolgt keine Pfadnormalisierung.</span><span class="sxs-lookup"><span data-stu-id="83163-150">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="83163-151">Wird der Pfad in einfachen Anführungszeichen angegeben, wird er nicht aufgelöst und als Literal betrachtet.</span><span class="sxs-lookup"><span data-stu-id="83163-151">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="83163-152">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="83163-152">PSNullConditionalOperators</span></span>

<span data-ttu-id="83163-153">Hiermit werden neue Operatoren für den NULL-bedingten Memberzugriff eingeführt: `?.` und `?[]`.</span><span class="sxs-lookup"><span data-stu-id="83163-153">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="83163-154">Operatoren für den NULL-Memberzugriff können für Skalartypen und Arraytypen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="83163-154">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="83163-155">Geben Sie den Wert des Members zurück, auf den zugegriffen wurde, wenn die Variable ungleich NULL ist.</span><span class="sxs-lookup"><span data-stu-id="83163-155">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="83163-156">Lautet der Wert der Variablen NULL, geben Sie NULL zurück.</span><span class="sxs-lookup"><span data-stu-id="83163-156">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="83163-157">Es wird auf die Eigenschaft `propname` zugegriffen, und ihr Wert wird nur zurückgegeben, wenn `$x` nicht NULL lautet.</span><span class="sxs-lookup"><span data-stu-id="83163-157">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="83163-158">Ähnlich wird der Indexer nur verwendet, wenn `$x` nicht NULL lautet.</span><span class="sxs-lookup"><span data-stu-id="83163-158">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="83163-159">Wenn `$x` NULL ist, wird NULL zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="83163-159">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="83163-160">Die Operatoren `?.` und `?[]` sind Memberzugriffsoperatoren und lassen kein Leerzeichen zwischen dem Variablennamen und dem Operator zu.</span><span class="sxs-lookup"><span data-stu-id="83163-160">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="83163-161">Da PowerShell `?` als Bestandteil des Variablennamens zulässt, muss Eindeutigkeit gewährleistet werden, wenn Operatoren ohne Leerzeichen zwischen dem Variablennamen und dem Operator verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="83163-161">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="83163-162">Zur Unterscheidung muss der Name der Variablen in `{}` eingeschlossen werden. Beispiel: `${x?}?.propertyName` oder `${y}?[0]`.</span><span class="sxs-lookup"><span data-stu-id="83163-162">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="83163-163">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="83163-163">PSTempDrive</span></span>

<span data-ttu-id="83163-164">Erstellt das PSDrive `TEMP:`, das dem temporären Verzeichnispfad des Benutzers zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="83163-164">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="83163-165">Dieses Feature befindet sich nicht mehr in der experimentellen Phase und wird in PowerShell 7 und höher jetzt allgemein unterstützt.</span><span class="sxs-lookup"><span data-stu-id="83163-165">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="83163-166">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="83163-166">PSUnixFileStat</span></span>

<span data-ttu-id="83163-167">Dieses Feature bietet ein neues Verhalten zum Einschließen von Daten aus der **stat**-API unter Unix in die Ausgabe des Dateisystemanbieters, um eine Unix-ähnlichere Dateiliste zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="83163-167">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="83163-168">Es wird im Dateisystemanbieter eine neue NoteProperty namens **UnixStat** hinzugefügt, die einen gemeinsamen Ausdruck der `stat(2)`-API aus dem zugrunde liegenden Unix-Typsystem enthält.</span><span class="sxs-lookup"><span data-stu-id="83163-168">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="83163-169">Die Ausgabe von `Get-ChildItem` sollte ungefähr wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="83163-169">The output from `Get-ChildItem` should look something like this:</span></span>

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

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="83163-170">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="83163-170">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="83163-171">Dieses Feature aktiviert die Vervollständigung abgekürzter Cmdlets und Funktionen mit der TAB-TASTE:</span><span class="sxs-lookup"><span data-stu-id="83163-171">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="83163-172">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="83163-172">For example:</span></span>

- <span data-ttu-id="83163-173">`Import-PowerShellDataFile` gibt `i-psdf<tab>` zurück.</span><span class="sxs-lookup"><span data-stu-id="83163-173">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="83163-174">`u-akvmssdr<tab>` gibt `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval` zurück.</span><span class="sxs-lookup"><span data-stu-id="83163-174">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="83163-175">Dies funktioniert nur für die Vervollständigung mit der TAB-TASTE (interaktive Verwendung), deshalb ist `i-psdf` kein gültiger Name eines Cmdlets in einem Skript.</span><span class="sxs-lookup"><span data-stu-id="83163-175">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="83163-176">Dieses Feature befindet sich nicht mehr in der experimentellen Phase und wird in PowerShell 7 und höher jetzt allgemein unterstützt.</span><span class="sxs-lookup"><span data-stu-id="83163-176">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>
