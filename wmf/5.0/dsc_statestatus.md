---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339870"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="157be-102">Vereinheitlichung und Konsistenz von Zustands- und Statusdarstellung</span><span class="sxs-lookup"><span data-stu-id="157be-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="157be-103">Für diese Version sind eine Reihe von Verbesserungen beim automatisch erstellten LCM-Zustand und DSC-Status erfolgt.</span><span class="sxs-lookup"><span data-stu-id="157be-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="157be-104">Dazu gehören vereinheitlichte und konsistente Zustands- und Statusdarstellungen, die verwaltbare „datetime“-Eigenschaft von Statusobjekten, die vom Cmdlet `Get-DscConfigurationStatus` zurückgegeben werden, und eine verbesserte LCM-Statusdetaileigenschaft, die vom Cmdlet `Get-DscLocalConfigurationManager` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="157be-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="157be-105">Die Darstellung des LCM-Zustands und DSC-Betriebsstatus wird gemäß den folgenden Regeln überprüft und vereinheitlicht:</span><span class="sxs-lookup"><span data-stu-id="157be-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="157be-106">Die Ressource „NotProcessed“ wirkt sich nicht auf den LCM-Zustand und DSC-Status aus.</span><span class="sxs-lookup"><span data-stu-id="157be-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="157be-107">Der LCM beendet die Verarbeitung weiterer Ressourcen, sobald er auf eine Ressource trifft, die einen Neustart anfordert.</span><span class="sxs-lookup"><span data-stu-id="157be-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="157be-108">Eine Ressource, die einen Neustart anfordert, ist erst im gewünschten Zustand, nach der Neustart tatsächlich erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="157be-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="157be-109">Wenn der LCM auf eine fehlerhafte Ressource trifft, setzt er die Verarbeitung weiterer Ressourcen fort, sofern diese nicht von der fehlerhaften Ressource abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="157be-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="157be-110">Der vom Cmdlet `Get-DscConfigurationStatus` zurückgegebene Gesamtstatus ist die Obermenge der Status aller Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="157be-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="157be-111">Der Status „PendingReboot“ ist eine Obermenge des Status „PendingConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="157be-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="157be-112">Die nachfolgende Tabelle veranschaulicht die resultierenden auf Zustand und Status bezogenen Eigenschaften in einigen gängigen Szenarien.</span><span class="sxs-lookup"><span data-stu-id="157be-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="157be-113">Szenario</span><span class="sxs-lookup"><span data-stu-id="157be-113">Scenario</span></span>                        | <span data-ttu-id="157be-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="157be-114">LCMState</span></span>             | <span data-ttu-id="157be-115">Status</span><span class="sxs-lookup"><span data-stu-id="157be-115">Status</span></span>     | <span data-ttu-id="157be-116">Neustart angefordert</span><span class="sxs-lookup"><span data-stu-id="157be-116">Reboot Requested</span></span> | <span data-ttu-id="157be-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="157be-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="157be-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="157be-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="157be-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="157be-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="157be-120">Idle</span><span class="sxs-lookup"><span data-stu-id="157be-120">Idle</span></span>                 | <span data-ttu-id="157be-121">Erfolg</span><span class="sxs-lookup"><span data-stu-id="157be-121">Success</span></span>    | <span data-ttu-id="157be-122">$false</span><span class="sxs-lookup"><span data-stu-id="157be-122">$false</span></span>        | <span data-ttu-id="157be-123">E</span><span class="sxs-lookup"><span data-stu-id="157be-123">S</span></span>                            | <span data-ttu-id="157be-124">$null</span><span class="sxs-lookup"><span data-stu-id="157be-124">$null</span></span>                          |
| <span data-ttu-id="157be-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="157be-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="157be-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="157be-126">PendingConfiguration</span></span> | <span data-ttu-id="157be-127">Fehler</span><span class="sxs-lookup"><span data-stu-id="157be-127">Failure</span></span>    | <span data-ttu-id="157be-128">$false</span><span class="sxs-lookup"><span data-stu-id="157be-128">$false</span></span>        | <span data-ttu-id="157be-129">$null</span><span class="sxs-lookup"><span data-stu-id="157be-129">$null</span></span>                        | <span data-ttu-id="157be-130">F</span><span class="sxs-lookup"><span data-stu-id="157be-130">F</span></span>                              |
| <span data-ttu-id="157be-131">E,F</span><span class="sxs-lookup"><span data-stu-id="157be-131">S,F</span></span>                             | <span data-ttu-id="157be-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="157be-132">PendingConfiguration</span></span> | <span data-ttu-id="157be-133">Fehler</span><span class="sxs-lookup"><span data-stu-id="157be-133">Failure</span></span>    | <span data-ttu-id="157be-134">$false</span><span class="sxs-lookup"><span data-stu-id="157be-134">$false</span></span>        | <span data-ttu-id="157be-135">E</span><span class="sxs-lookup"><span data-stu-id="157be-135">S</span></span>                            | <span data-ttu-id="157be-136">F</span><span class="sxs-lookup"><span data-stu-id="157be-136">F</span></span>                              |
| <span data-ttu-id="157be-137">E, S</span><span class="sxs-lookup"><span data-stu-id="157be-137">F,S</span></span>                             | <span data-ttu-id="157be-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="157be-138">PendingConfiguration</span></span> | <span data-ttu-id="157be-139">Fehler</span><span class="sxs-lookup"><span data-stu-id="157be-139">Failure</span></span>    | <span data-ttu-id="157be-140">$false</span><span class="sxs-lookup"><span data-stu-id="157be-140">$false</span></span>        | <span data-ttu-id="157be-141">E</span><span class="sxs-lookup"><span data-stu-id="157be-141">S</span></span>                            | <span data-ttu-id="157be-142">F</span><span class="sxs-lookup"><span data-stu-id="157be-142">F</span></span>                              |
| <span data-ttu-id="157be-143">E<sub>1</sub>, F, E<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="157be-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="157be-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="157be-144">PendingConfiguration</span></span> | <span data-ttu-id="157be-145">Fehler</span><span class="sxs-lookup"><span data-stu-id="157be-145">Failure</span></span>    | <span data-ttu-id="157be-146">$false</span><span class="sxs-lookup"><span data-stu-id="157be-146">$false</span></span>        | <span data-ttu-id="157be-147">E<sub>1</sub>, E<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="157be-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="157be-148">F</span><span class="sxs-lookup"><span data-stu-id="157be-148">F</span></span>                              |
| <span data-ttu-id="157be-149">F<sub>1</sub>, E, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="157be-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="157be-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="157be-150">PendingConfiguration</span></span> | <span data-ttu-id="157be-151">Fehler</span><span class="sxs-lookup"><span data-stu-id="157be-151">Failure</span></span>    | <span data-ttu-id="157be-152">$false</span><span class="sxs-lookup"><span data-stu-id="157be-152">$false</span></span>        | <span data-ttu-id="157be-153">E</span><span class="sxs-lookup"><span data-stu-id="157be-153">S</span></span>                            | <span data-ttu-id="157be-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="157be-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="157be-155">E, N</span><span class="sxs-lookup"><span data-stu-id="157be-155">S, r</span></span>                            | <span data-ttu-id="157be-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="157be-156">PendingReboot</span></span>        | <span data-ttu-id="157be-157">Erfolg</span><span class="sxs-lookup"><span data-stu-id="157be-157">Success</span></span>    | <span data-ttu-id="157be-158">$True</span><span class="sxs-lookup"><span data-stu-id="157be-158">$true</span></span>         | <span data-ttu-id="157be-159">E</span><span class="sxs-lookup"><span data-stu-id="157be-159">S</span></span>                            | <span data-ttu-id="157be-160">N</span><span class="sxs-lookup"><span data-stu-id="157be-160">r</span></span>                              |
| <span data-ttu-id="157be-161">F, N</span><span class="sxs-lookup"><span data-stu-id="157be-161">F, r</span></span>                            | <span data-ttu-id="157be-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="157be-162">PendingReboot</span></span>        | <span data-ttu-id="157be-163">Fehler</span><span class="sxs-lookup"><span data-stu-id="157be-163">Failure</span></span>    | <span data-ttu-id="157be-164">$True</span><span class="sxs-lookup"><span data-stu-id="157be-164">$true</span></span>         | <span data-ttu-id="157be-165">$null</span><span class="sxs-lookup"><span data-stu-id="157be-165">$null</span></span>                        | <span data-ttu-id="157be-166">F, N</span><span class="sxs-lookup"><span data-stu-id="157be-166">F, r</span></span>                           |
| <span data-ttu-id="157be-167">R, E</span><span class="sxs-lookup"><span data-stu-id="157be-167">r, S</span></span>                            | <span data-ttu-id="157be-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="157be-168">PendingReboot</span></span>        | <span data-ttu-id="157be-169">Erfolg</span><span class="sxs-lookup"><span data-stu-id="157be-169">Success</span></span>    | <span data-ttu-id="157be-170">$True</span><span class="sxs-lookup"><span data-stu-id="157be-170">$true</span></span>         | <span data-ttu-id="157be-171">$null</span><span class="sxs-lookup"><span data-stu-id="157be-171">$null</span></span>                        | <span data-ttu-id="157be-172">r</span><span class="sxs-lookup"><span data-stu-id="157be-172">r</span></span>                              |
| <span data-ttu-id="157be-173">N, F</span><span class="sxs-lookup"><span data-stu-id="157be-173">r, F</span></span>                            | <span data-ttu-id="157be-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="157be-174">PendingReboot</span></span>        | <span data-ttu-id="157be-175">Erfolg</span><span class="sxs-lookup"><span data-stu-id="157be-175">Success</span></span>    | <span data-ttu-id="157be-176">$True</span><span class="sxs-lookup"><span data-stu-id="157be-176">$true</span></span>         | <span data-ttu-id="157be-177">$null</span><span class="sxs-lookup"><span data-stu-id="157be-177">$null</span></span>                        | <span data-ttu-id="157be-178">N</span><span class="sxs-lookup"><span data-stu-id="157be-178">r</span></span>                              |

- <span data-ttu-id="157be-179">E<sub>i</sub>: Eine Reihe von Ressourcen, die erfolgreich angewendet wurden</span><span class="sxs-lookup"><span data-stu-id="157be-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="157be-180">F<sub>i</sub>: Eine Reihe von Ressourcen, die nicht erfolgreich angewendet wurden</span><span class="sxs-lookup"><span data-stu-id="157be-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="157be-181">N: Eine Ressource, die einen Neustart anfordert</span><span class="sxs-lookup"><span data-stu-id="157be-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="157be-182">Verbesserungen beim Cmdlet „Get-DscConfigurationStatus“</span><span class="sxs-lookup"><span data-stu-id="157be-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="157be-183">In diesem Release wurden einige Verbesserungen am Cmdlet `Get-DscConfigurationStatus` vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="157be-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="157be-184">Zuvor hatte die „StartDate“-Eigenschaft von Objekten, die vom Cmdlet zurückgegeben wurden, den Typ „String“.</span><span class="sxs-lookup"><span data-stu-id="157be-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="157be-185">Jetzt hat sie den Typ „Datetime“, der komplexe Auswahl- und Filtervorgänge basierend auf den inhärenten Eigenschaften eines „Datetime“-Objekts erleichtert.</span><span class="sxs-lookup"><span data-stu-id="157be-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

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

<span data-ttu-id="157be-186">Im folgenden Beispiel werden alle Datensätze von DSC-Vorgängen zurückgegeben, die am selben Tag der Woche wie dem heutigen Tag erfolgt sind.</span><span class="sxs-lookup"><span data-stu-id="157be-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="157be-187">Datensätze von Vorgängen, die keine Änderungen an der Konfiguration des Knotens vornehmen (z. B. Lesevorgänge), werden entfernt.</span><span class="sxs-lookup"><span data-stu-id="157be-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="157be-188">Aus diesem Grund werden die Vorgänge `Test-DscConfiguration` und `Get-DscConfiguration` nicht mehr in zurückgegebenen Objekten vom Cmdlet `Get-DscConfigurationStatus` verfälscht.</span><span class="sxs-lookup"><span data-stu-id="157be-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="157be-189">Der Rückgabe des Cmdlets `Get-DscConfigurationStatus` werden Datensätze zum Vorgang der Metakonfigurationseinstellung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="157be-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="157be-190">Im Folgenden wird ein Beispiel für ein Ergebnis gezeigt, das vom Cmdlet `Get-DscConfigurationStatus –All` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="157be-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="157be-191">Verbesserungen beim Cmdlet „Get-DscLocalConfigurationManager“</span><span class="sxs-lookup"><span data-stu-id="157be-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="157be-192">Das neue Feld „LCMStateDetail“ wird dem Objekt hinzugefügt, das vom Cmdlet `Get-DscLocalConfigurationManager` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="157be-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="157be-193">Dieses Feld wird aufgefüllt, wenn „LCMState = Busy".</span><span class="sxs-lookup"><span data-stu-id="157be-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="157be-194">Es kann mit dem folgenden Cmdlet abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="157be-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="157be-195">Es folgt eine Beispielausgabe einer kontinuierlichen Überwachung einer Konfiguration, die zwei Neustarts auf einem Remoteknoten erfordert.</span><span class="sxs-lookup"><span data-stu-id="157be-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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
