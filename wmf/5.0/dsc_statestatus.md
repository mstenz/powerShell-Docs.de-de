---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058980"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="b170b-102">Vereinheitlichung und Konsistenz von Zustands- und Statusdarstellung</span><span class="sxs-lookup"><span data-stu-id="b170b-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="b170b-103">Für diese Version sind eine Reihe von Verbesserungen beim automatisch erstellten LCM-Zustand und DSC-Status erfolgt.</span><span class="sxs-lookup"><span data-stu-id="b170b-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="b170b-104">Dazu gehören vereinheitlichte und konsistente Zustands- und Statusdarstellungen, die verwaltbare „datetime“-Eigenschaft von Statusobjekten, die vom Cmdlet `Get-DscConfigurationStatus` zurückgegeben werden, und eine verbesserte LCM-Statusdetaileigenschaft, die vom Cmdlet `Get-DscLocalConfigurationManager` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b170b-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="b170b-105">Die Darstellung des LCM-Zustands und DSC-Betriebsstatus wird gemäß den folgenden Regeln überprüft und vereinheitlicht:</span><span class="sxs-lookup"><span data-stu-id="b170b-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="b170b-106">Die Ressource „NotProcessed“ wirkt sich nicht auf den LCM-Zustand und DSC-Status aus.</span><span class="sxs-lookup"><span data-stu-id="b170b-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="b170b-107">Der LCM beendet die Verarbeitung weiterer Ressourcen, sobald er auf eine Ressource trifft, die einen Neustart anfordert.</span><span class="sxs-lookup"><span data-stu-id="b170b-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="b170b-108">Eine Ressource, die einen Neustart anfordert, ist erst im gewünschten Zustand, nach der Neustart tatsächlich erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="b170b-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="b170b-109">Wenn der LCM auf eine fehlerhafte Ressource trifft, setzt er die Verarbeitung weiterer Ressourcen fort, sofern diese nicht von der fehlerhaften Ressource abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="b170b-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="b170b-110">Der vom Cmdlet `Get-DscConfigurationStatus` zurückgegebene Gesamtstatus ist die Obermenge der Status aller Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="b170b-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="b170b-111">Der Status „PendingReboot“ ist eine Obermenge des Status „PendingConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="b170b-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="b170b-112">Die nachfolgende Tabelle veranschaulicht die resultierenden auf Zustand und Status bezogenen Eigenschaften in einigen gängigen Szenarien.</span><span class="sxs-lookup"><span data-stu-id="b170b-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="b170b-113">Szenario</span><span class="sxs-lookup"><span data-stu-id="b170b-113">Scenario</span></span>                        | <span data-ttu-id="b170b-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="b170b-114">LCMState</span></span>             | <span data-ttu-id="b170b-115">Status</span><span class="sxs-lookup"><span data-stu-id="b170b-115">Status</span></span>     | <span data-ttu-id="b170b-116">Neustart angefordert</span><span class="sxs-lookup"><span data-stu-id="b170b-116">Reboot Requested</span></span> | <span data-ttu-id="b170b-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="b170b-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="b170b-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="b170b-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="b170b-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="b170b-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="b170b-120">Idle</span><span class="sxs-lookup"><span data-stu-id="b170b-120">Idle</span></span>                 | <span data-ttu-id="b170b-121">Erfolg</span><span class="sxs-lookup"><span data-stu-id="b170b-121">Success</span></span>    | <span data-ttu-id="b170b-122">$false</span><span class="sxs-lookup"><span data-stu-id="b170b-122">$false</span></span>        | <span data-ttu-id="b170b-123">E</span><span class="sxs-lookup"><span data-stu-id="b170b-123">S</span></span>                            | <span data-ttu-id="b170b-124">$null</span><span class="sxs-lookup"><span data-stu-id="b170b-124">$null</span></span>                          |
| <span data-ttu-id="b170b-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="b170b-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="b170b-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b170b-126">PendingConfiguration</span></span> | <span data-ttu-id="b170b-127">Fehler</span><span class="sxs-lookup"><span data-stu-id="b170b-127">Failure</span></span>    | <span data-ttu-id="b170b-128">$false</span><span class="sxs-lookup"><span data-stu-id="b170b-128">$false</span></span>        | <span data-ttu-id="b170b-129">$null</span><span class="sxs-lookup"><span data-stu-id="b170b-129">$null</span></span>                        | <span data-ttu-id="b170b-130">F</span><span class="sxs-lookup"><span data-stu-id="b170b-130">F</span></span>                              |
| <span data-ttu-id="b170b-131">E,F</span><span class="sxs-lookup"><span data-stu-id="b170b-131">S,F</span></span>                             | <span data-ttu-id="b170b-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b170b-132">PendingConfiguration</span></span> | <span data-ttu-id="b170b-133">Fehler</span><span class="sxs-lookup"><span data-stu-id="b170b-133">Failure</span></span>    | <span data-ttu-id="b170b-134">$false</span><span class="sxs-lookup"><span data-stu-id="b170b-134">$false</span></span>        | <span data-ttu-id="b170b-135">E</span><span class="sxs-lookup"><span data-stu-id="b170b-135">S</span></span>                            | <span data-ttu-id="b170b-136">F</span><span class="sxs-lookup"><span data-stu-id="b170b-136">F</span></span>                              |
| <span data-ttu-id="b170b-137">E, S</span><span class="sxs-lookup"><span data-stu-id="b170b-137">F,S</span></span>                             | <span data-ttu-id="b170b-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b170b-138">PendingConfiguration</span></span> | <span data-ttu-id="b170b-139">Fehler</span><span class="sxs-lookup"><span data-stu-id="b170b-139">Failure</span></span>    | <span data-ttu-id="b170b-140">$false</span><span class="sxs-lookup"><span data-stu-id="b170b-140">$false</span></span>        | <span data-ttu-id="b170b-141">E</span><span class="sxs-lookup"><span data-stu-id="b170b-141">S</span></span>                            | <span data-ttu-id="b170b-142">F</span><span class="sxs-lookup"><span data-stu-id="b170b-142">F</span></span>                              |
| <span data-ttu-id="b170b-143">E<sub>1</sub>, F, E<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b170b-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="b170b-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b170b-144">PendingConfiguration</span></span> | <span data-ttu-id="b170b-145">Fehler</span><span class="sxs-lookup"><span data-stu-id="b170b-145">Failure</span></span>    | <span data-ttu-id="b170b-146">$false</span><span class="sxs-lookup"><span data-stu-id="b170b-146">$false</span></span>        | <span data-ttu-id="b170b-147">E<sub>1</sub>, E<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b170b-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="b170b-148">F</span><span class="sxs-lookup"><span data-stu-id="b170b-148">F</span></span>                              |
| <span data-ttu-id="b170b-149">F<sub>1</sub>, E, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b170b-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="b170b-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b170b-150">PendingConfiguration</span></span> | <span data-ttu-id="b170b-151">Fehler</span><span class="sxs-lookup"><span data-stu-id="b170b-151">Failure</span></span>    | <span data-ttu-id="b170b-152">$false</span><span class="sxs-lookup"><span data-stu-id="b170b-152">$false</span></span>        | <span data-ttu-id="b170b-153">E</span><span class="sxs-lookup"><span data-stu-id="b170b-153">S</span></span>                            | <span data-ttu-id="b170b-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b170b-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="b170b-155">E, N</span><span class="sxs-lookup"><span data-stu-id="b170b-155">S, r</span></span>                            | <span data-ttu-id="b170b-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b170b-156">PendingReboot</span></span>        | <span data-ttu-id="b170b-157">Erfolg</span><span class="sxs-lookup"><span data-stu-id="b170b-157">Success</span></span>    | <span data-ttu-id="b170b-158">$True</span><span class="sxs-lookup"><span data-stu-id="b170b-158">$true</span></span>         | <span data-ttu-id="b170b-159">E</span><span class="sxs-lookup"><span data-stu-id="b170b-159">S</span></span>                            | <span data-ttu-id="b170b-160">N</span><span class="sxs-lookup"><span data-stu-id="b170b-160">r</span></span>                              |
| <span data-ttu-id="b170b-161">F, N</span><span class="sxs-lookup"><span data-stu-id="b170b-161">F, r</span></span>                            | <span data-ttu-id="b170b-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b170b-162">PendingReboot</span></span>        | <span data-ttu-id="b170b-163">Fehler</span><span class="sxs-lookup"><span data-stu-id="b170b-163">Failure</span></span>    | <span data-ttu-id="b170b-164">$True</span><span class="sxs-lookup"><span data-stu-id="b170b-164">$true</span></span>         | <span data-ttu-id="b170b-165">$null</span><span class="sxs-lookup"><span data-stu-id="b170b-165">$null</span></span>                        | <span data-ttu-id="b170b-166">F, N</span><span class="sxs-lookup"><span data-stu-id="b170b-166">F, r</span></span>                           |
| <span data-ttu-id="b170b-167">R, E</span><span class="sxs-lookup"><span data-stu-id="b170b-167">r, S</span></span>                            | <span data-ttu-id="b170b-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b170b-168">PendingReboot</span></span>        | <span data-ttu-id="b170b-169">Erfolg</span><span class="sxs-lookup"><span data-stu-id="b170b-169">Success</span></span>    | <span data-ttu-id="b170b-170">$True</span><span class="sxs-lookup"><span data-stu-id="b170b-170">$true</span></span>         | <span data-ttu-id="b170b-171">$null</span><span class="sxs-lookup"><span data-stu-id="b170b-171">$null</span></span>                        | <span data-ttu-id="b170b-172">r</span><span class="sxs-lookup"><span data-stu-id="b170b-172">r</span></span>                              |
| <span data-ttu-id="b170b-173">N, F</span><span class="sxs-lookup"><span data-stu-id="b170b-173">r, F</span></span>                            | <span data-ttu-id="b170b-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b170b-174">PendingReboot</span></span>        | <span data-ttu-id="b170b-175">Erfolg</span><span class="sxs-lookup"><span data-stu-id="b170b-175">Success</span></span>    | <span data-ttu-id="b170b-176">$True</span><span class="sxs-lookup"><span data-stu-id="b170b-176">$true</span></span>         | <span data-ttu-id="b170b-177">$null</span><span class="sxs-lookup"><span data-stu-id="b170b-177">$null</span></span>                        | <span data-ttu-id="b170b-178">r</span><span class="sxs-lookup"><span data-stu-id="b170b-178">r</span></span>                              |

- <span data-ttu-id="b170b-179">E<sub>i</sub>: Eine Reihe von Ressourcen, die erfolgreich angewendet wurden</span><span class="sxs-lookup"><span data-stu-id="b170b-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="b170b-180">F<sub>i</sub>: Eine Reihe von Ressourcen, die nicht erfolgreich angewendet wurden</span><span class="sxs-lookup"><span data-stu-id="b170b-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="b170b-181">N: Eine Ressource, die einen Neustart anfordert</span><span class="sxs-lookup"><span data-stu-id="b170b-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="b170b-182">Verbesserungen beim Cmdlet „Get-DscConfigurationStatus“</span><span class="sxs-lookup"><span data-stu-id="b170b-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="b170b-183">In diesem Release wurden einige Verbesserungen am Cmdlet `Get-DscConfigurationStatus` vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="b170b-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="b170b-184">Zuvor hatte die „StartDate“-Eigenschaft von Objekten, die vom Cmdlet zurückgegeben wurden, den Typ „String“.</span><span class="sxs-lookup"><span data-stu-id="b170b-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="b170b-185">Jetzt hat sie den Typ „Datetime“, der komplexe Auswahl- und Filtervorgänge basierend auf den inhärenten Eigenschaften eines „Datetime“-Objekts erleichtert.</span><span class="sxs-lookup"><span data-stu-id="b170b-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="b170b-186">Im folgenden Beispiel werden alle Datensätze von DSC-Vorgängen zurückgegeben, die am selben Tag der Woche wie dem heutigen Tag erfolgt sind.</span><span class="sxs-lookup"><span data-stu-id="b170b-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="b170b-187">Datensätze von Vorgängen, die keine Änderungen an der Konfiguration des Knotens vornehmen (z. B. Lesevorgänge), werden entfernt.</span><span class="sxs-lookup"><span data-stu-id="b170b-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="b170b-188">Aus diesem Grund werden die Vorgänge `Test-DscConfiguration` und `Get-DscConfiguration` nicht mehr in zurückgegebenen Objekten vom Cmdlet `Get-DscConfigurationStatus` verfälscht.</span><span class="sxs-lookup"><span data-stu-id="b170b-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="b170b-189">Der Rückgabe des Cmdlets `Get-DscConfigurationStatus` werden Datensätze zum Vorgang der Metakonfigurationseinstellung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="b170b-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="b170b-190">Im Folgenden wird ein Beispiel für ein Ergebnis gezeigt, das vom Cmdlet `Get-DscConfigurationStatus –All` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b170b-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="b170b-191">Verbesserungen beim Cmdlet „Get-DscLocalConfigurationManager“</span><span class="sxs-lookup"><span data-stu-id="b170b-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="b170b-192">Das neue Feld „LCMStateDetail“ wird dem Objekt hinzugefügt, das vom Cmdlet `Get-DscLocalConfigurationManager` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b170b-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="b170b-193">Dieses Feld wird aufgefüllt, wenn „LCMState = Busy".</span><span class="sxs-lookup"><span data-stu-id="b170b-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="b170b-194">Es kann mit dem folgenden Cmdlet abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="b170b-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="b170b-195">Es folgt eine Beispielausgabe einer kontinuierlichen Überwachung einer Konfiguration, die zwei Neustarts auf einem Remoteknoten erfordert.</span><span class="sxs-lookup"><span data-stu-id="b170b-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
