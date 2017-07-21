---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 32f8e20889ddc526def4b925e8d0761a2e851e19
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="f60d8-102">Vereinheitlichung und Konsistenz von Zustands- und Statusdarstellung</span><span class="sxs-lookup"><span data-stu-id="f60d8-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="f60d8-103">Für diese Version sind eine Reihe von Verbesserungen beim automatisch erstellten LCM-Zustand und DSC-Status erfolgt.</span><span class="sxs-lookup"><span data-stu-id="f60d8-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="f60d8-104">Dazu gehören vereinheitlichte und konsistente Zustands- und Statusdarstellungen, verwaltbare „datetime“-Eigenschaft von Statusobjekten, die vom Cmdlet „Get-DscConfigurationStatus“ zurückgegeben werden, und eine verbesserte LCM-Statusdetaileigenschaft, die vom Cmdlet „Get-DscLocalConfigurationManager“ zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="f60d8-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by Get-DscConfigurationStatus cmdlet and enhanced LCM state details property returned by Get-DscLocalConfigurationManager cmdlet.</span></span>

<span data-ttu-id="f60d8-105">Die Darstellung des LCM-Zustands und DSC-Betriebsstatus wird gemäß den folgenden Regeln überprüft und vereinheitlicht:</span><span class="sxs-lookup"><span data-stu-id="f60d8-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>
1.  <span data-ttu-id="f60d8-106">Die Ressource „NotProcessed“ wirkt sich nicht auf den LCM-Zustand und DSC-Status aus.</span><span class="sxs-lookup"><span data-stu-id="f60d8-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2.  <span data-ttu-id="f60d8-107">Der LCM beendet die Verarbeitung weiterer Ressourcen, sobald er auf eine Ressource trifft, die einen Neustart anfordert.</span><span class="sxs-lookup"><span data-stu-id="f60d8-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3.  <span data-ttu-id="f60d8-108">Eine Ressource, die einen Neustart anfordert, ist erst im gewünschten Zustand, nach der Neustart tatsächlich erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="f60d8-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4.  <span data-ttu-id="f60d8-109">Wenn der LCM auf eine fehlerhafte Ressource trifft, setzt er die Verarbeitung weiterer Ressourcen fort, sofern diese nicht von der fehlerhaften Ressource abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="f60d8-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5.  <span data-ttu-id="f60d8-110">Der vom Cmdlet „Get-DscConfigurationStatus“ zurückgegebene Gesamtstatus ist die Obermenge der Status aller Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="f60d8-110">The overall status returned by Get-DscConfigurationStatus cmdlet is the super set of all resources’ status.</span></span>
6.  <span data-ttu-id="f60d8-111">Der Status „PendingReboot“ ist eine Obermenge des Status „PendingConfiguration“.</span><span class="sxs-lookup"><span data-stu-id="f60d8-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="f60d8-112">Die nachfolgende Tabelle veranschaulicht die resultierenden auf Zustand und Status bezogenen Eigenschaften in einigen gängigen Szenarien.</span><span class="sxs-lookup"><span data-stu-id="f60d8-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="f60d8-113">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="f60d8-113">**Scenario**</span></span>                    | <span data-ttu-id="f60d8-114">**LCMState\***</span><span class="sxs-lookup"><span data-stu-id="f60d8-114">**LCMState\***</span></span>       | <span data-ttu-id="f60d8-115">**Status**</span><span class="sxs-lookup"><span data-stu-id="f60d8-115">**Status**</span></span> | <span data-ttu-id="f60d8-116">**Neustart angefordert**</span><span class="sxs-lookup"><span data-stu-id="f60d8-116">**Reboot Requested**</span></span>  | <span data-ttu-id="f60d8-117">**ResourcesInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="f60d8-117">**ResourcesInDesiredState**</span></span>  | <span data-ttu-id="f60d8-118">**ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="f60d8-118">**ResourcesNotInDesiredState**</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="f60d8-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="f60d8-119">S**^**</span></span>                          | <span data-ttu-id="f60d8-120">Idle</span><span class="sxs-lookup"><span data-stu-id="f60d8-120">Idle</span></span>                 | <span data-ttu-id="f60d8-121">Erfolg</span><span class="sxs-lookup"><span data-stu-id="f60d8-121">Success</span></span>    | <span data-ttu-id="f60d8-122">$false</span><span class="sxs-lookup"><span data-stu-id="f60d8-122">$false</span></span>        | <span data-ttu-id="f60d8-123">E</span><span class="sxs-lookup"><span data-stu-id="f60d8-123">S</span></span>                            | <span data-ttu-id="f60d8-124">$null</span><span class="sxs-lookup"><span data-stu-id="f60d8-124">$null</span></span>                          |
| <span data-ttu-id="f60d8-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="f60d8-125">F**^**</span></span>                          | <span data-ttu-id="f60d8-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="f60d8-126">PendingConfiguration</span></span> | <span data-ttu-id="f60d8-127">Fehler</span><span class="sxs-lookup"><span data-stu-id="f60d8-127">Failure</span></span>    | <span data-ttu-id="f60d8-128">$false</span><span class="sxs-lookup"><span data-stu-id="f60d8-128">$false</span></span>        | <span data-ttu-id="f60d8-129">$null</span><span class="sxs-lookup"><span data-stu-id="f60d8-129">$null</span></span>                        | <span data-ttu-id="f60d8-130">F</span><span class="sxs-lookup"><span data-stu-id="f60d8-130">F</span></span>                              |
| <span data-ttu-id="f60d8-131">E,F</span><span class="sxs-lookup"><span data-stu-id="f60d8-131">S,F</span></span>                             | <span data-ttu-id="f60d8-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="f60d8-132">PendingConfiguration</span></span> | <span data-ttu-id="f60d8-133">Fehler</span><span class="sxs-lookup"><span data-stu-id="f60d8-133">Failure</span></span>    | <span data-ttu-id="f60d8-134">$false</span><span class="sxs-lookup"><span data-stu-id="f60d8-134">$false</span></span>        | <span data-ttu-id="f60d8-135">E</span><span class="sxs-lookup"><span data-stu-id="f60d8-135">S</span></span>                            | <span data-ttu-id="f60d8-136">F</span><span class="sxs-lookup"><span data-stu-id="f60d8-136">F</span></span>                              |
| <span data-ttu-id="f60d8-137">E, S</span><span class="sxs-lookup"><span data-stu-id="f60d8-137">F,S</span></span>                             | <span data-ttu-id="f60d8-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="f60d8-138">PendingConfiguration</span></span> | <span data-ttu-id="f60d8-139">Fehler</span><span class="sxs-lookup"><span data-stu-id="f60d8-139">Failure</span></span>    | <span data-ttu-id="f60d8-140">$false</span><span class="sxs-lookup"><span data-stu-id="f60d8-140">$false</span></span>        | <span data-ttu-id="f60d8-141">E</span><span class="sxs-lookup"><span data-stu-id="f60d8-141">S</span></span>                            | <span data-ttu-id="f60d8-142">F</span><span class="sxs-lookup"><span data-stu-id="f60d8-142">F</span></span>                              |
| <span data-ttu-id="f60d8-143">E<sub>1</sub>, F, E<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="f60d8-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="f60d8-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="f60d8-144">PendingConfiguration</span></span> | <span data-ttu-id="f60d8-145">Fehler</span><span class="sxs-lookup"><span data-stu-id="f60d8-145">Failure</span></span>    | <span data-ttu-id="f60d8-146">$false</span><span class="sxs-lookup"><span data-stu-id="f60d8-146">$false</span></span>        | <span data-ttu-id="f60d8-147">E<sub>1</sub>, E<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="f60d8-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="f60d8-148">F</span><span class="sxs-lookup"><span data-stu-id="f60d8-148">F</span></span>                              |
| <span data-ttu-id="f60d8-149">F<sub>1</sub>, E, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="f60d8-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="f60d8-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="f60d8-150">PendingConfiguration</span></span> | <span data-ttu-id="f60d8-151">Fehler</span><span class="sxs-lookup"><span data-stu-id="f60d8-151">Failure</span></span>    | <span data-ttu-id="f60d8-152">$false</span><span class="sxs-lookup"><span data-stu-id="f60d8-152">$false</span></span>        | <span data-ttu-id="f60d8-153">E</span><span class="sxs-lookup"><span data-stu-id="f60d8-153">S</span></span>                            | <span data-ttu-id="f60d8-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="f60d8-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="f60d8-155">E, N</span><span class="sxs-lookup"><span data-stu-id="f60d8-155">S, r</span></span>                            | <span data-ttu-id="f60d8-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="f60d8-156">PendingReboot</span></span>        | <span data-ttu-id="f60d8-157">Erfolg</span><span class="sxs-lookup"><span data-stu-id="f60d8-157">Success</span></span>    | <span data-ttu-id="f60d8-158">$True</span><span class="sxs-lookup"><span data-stu-id="f60d8-158">$true</span></span>         | <span data-ttu-id="f60d8-159">E</span><span class="sxs-lookup"><span data-stu-id="f60d8-159">S</span></span>                            | <span data-ttu-id="f60d8-160">N</span><span class="sxs-lookup"><span data-stu-id="f60d8-160">r</span></span>                              |
| <span data-ttu-id="f60d8-161">F, N</span><span class="sxs-lookup"><span data-stu-id="f60d8-161">F, r</span></span>                            | <span data-ttu-id="f60d8-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="f60d8-162">PendingReboot</span></span>        | <span data-ttu-id="f60d8-163">Fehler</span><span class="sxs-lookup"><span data-stu-id="f60d8-163">Failure</span></span>    | <span data-ttu-id="f60d8-164">$True</span><span class="sxs-lookup"><span data-stu-id="f60d8-164">$true</span></span>         | <span data-ttu-id="f60d8-165">$null</span><span class="sxs-lookup"><span data-stu-id="f60d8-165">$null</span></span>                        | <span data-ttu-id="f60d8-166">F, N</span><span class="sxs-lookup"><span data-stu-id="f60d8-166">F, r</span></span>                           |
| <span data-ttu-id="f60d8-167">R, E</span><span class="sxs-lookup"><span data-stu-id="f60d8-167">r, S</span></span>                            | <span data-ttu-id="f60d8-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="f60d8-168">PendingReboot</span></span>        | <span data-ttu-id="f60d8-169">Erfolg</span><span class="sxs-lookup"><span data-stu-id="f60d8-169">Success</span></span>    | <span data-ttu-id="f60d8-170">$True</span><span class="sxs-lookup"><span data-stu-id="f60d8-170">$true</span></span>         | <span data-ttu-id="f60d8-171">$null</span><span class="sxs-lookup"><span data-stu-id="f60d8-171">$null</span></span>                        | <span data-ttu-id="f60d8-172">r</span><span class="sxs-lookup"><span data-stu-id="f60d8-172">r</span></span>                              |
| <span data-ttu-id="f60d8-173">N, F</span><span class="sxs-lookup"><span data-stu-id="f60d8-173">r, F</span></span>                            | <span data-ttu-id="f60d8-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="f60d8-174">PendingReboot</span></span>        | <span data-ttu-id="f60d8-175">Erfolg</span><span class="sxs-lookup"><span data-stu-id="f60d8-175">Success</span></span>    | <span data-ttu-id="f60d8-176">$True</span><span class="sxs-lookup"><span data-stu-id="f60d8-176">$true</span></span>         | <span data-ttu-id="f60d8-177">$null</span><span class="sxs-lookup"><span data-stu-id="f60d8-177">$null</span></span>                        | <span data-ttu-id="f60d8-178">r</span><span class="sxs-lookup"><span data-stu-id="f60d8-178">r</span></span>                              |

<span data-ttu-id="f60d8-179">^ S<sub>i</sub>: eine Reihe von Ressourcen, die erfolgreich angewendet wurden F<sub>i</sub>: eine Reihe von Ressourcen, die nicht erfolgreich angewendet wurden r: eine Ressource, die einen Neustart erfordert \*</span><span class="sxs-lookup"><span data-stu-id="f60d8-179">^ S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```
## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="f60d8-180">Verbesserungen beim Cmdlet „Get-DscConfigurationStatus“</span><span class="sxs-lookup"><span data-stu-id="f60d8-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="f60d8-181">Für diese Version wurden einige Verbesserungen am Cmdlet „Get-DscConfigurationStatus“ vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="f60d8-181">A few enhancements have been made to Get-DscConfigurationStatus cmdlet in this release.</span></span> <span data-ttu-id="f60d8-182">Zuvor hatte die „StartDate“-Eigenschaft von Objekten, die vom Cmdlet zurückgegeben wurden, den Typ „String“.</span><span class="sxs-lookup"><span data-stu-id="f60d8-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="f60d8-183">Jetzt hat sie den Typ „Datetime“, der komplexe Auswahl- und Filtervorgänge basierend auf den inhärenten Eigenschaften eines „Datetime“-Objekts erleichtert.</span><span class="sxs-lookup"><span data-stu-id="f60d8-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>
```powershell
(Get-DscConfigurationStatus).StartDate | fl \*
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="f60d8-184">Es folgt ein Beispiel, das alle Datensätze von DSC-Vorgängen zurückgibt, die am selben Tag der Woche wie heute erfolgt sind.</span><span class="sxs-lookup"><span data-stu-id="f60d8-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>
```powershell
(Get-DscConfigurationStatus –All) | where { $\_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="f60d8-185">Datensätze von Vorgängen, die keine Änderungen an der Konfiguration des Knotens vornehmen (z. B. Lesevorgänge), werden entfernt.</span><span class="sxs-lookup"><span data-stu-id="f60d8-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="f60d8-186">Deshalb werden die Vorgänge „Test-DscConfiguration“ und „Get-DscConfiguration“ nicht mehr mit Objekten verfälscht, die vom Cmdlet „Get-DscConfigurationStatus“ zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f60d8-186">Therefore, Test-DscConfiguration, Get-DscConfiguration operations are no longer adulterated in returned objects from Get-DscConfigurationStatus cmdlet.</span></span>
<span data-ttu-id="f60d8-187">Der Rückgabe des Cmdlets „Get-DscConfigurationStatus“ werden Datensätze zum Vorgang der Einstellung der Metakonfiguration hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="f60d8-187">Records of meta configuration setting operation is added to the return of Get-DscConfigurationStatus cmdlet.</span></span>

<span data-ttu-id="f60d8-188">Es folgt ein Beispiel der Rückgabe des Cmdlets „Get-DscConfigurationStatus –All“.</span><span class="sxs-lookup"><span data-stu-id="f60d8-188">Following is an example of result returned from Get-DscConfigurationStatus –All cmdlet.</span></span>
```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="f60d8-189">Verbesserungen beim Cmdlet „Get-DscLocalConfigurationManager“</span><span class="sxs-lookup"><span data-stu-id="f60d8-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>
<span data-ttu-id="f60d8-190">Das neue Feld „LCMStateDetail“ wird dem Objekt hinzugefügt, das vom Cmdlet „Get-DscLocalConfigurationManager“ zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="f60d8-190">A new field of LCMStateDetail is added to the object returned from Get-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="f60d8-191">Dieses Feld wird aufgefüllt, wenn „LCMState = Busy".</span><span class="sxs-lookup"><span data-stu-id="f60d8-191">This field is populated when LCMState is “Busy”.</span></span> <span data-ttu-id="f60d8-192">Es kann mit dem folgenden Cmdlet abgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="f60d8-192">It can be retrieved by following cmdlet:</span></span>
```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="f60d8-193">Es folgt eine Beispielausgabe einer kontinuierlichen Überwachung einer Konfiguration, die zwei Neustarts auf einem Remoteknoten erfordert.</span><span class="sxs-lookup"><span data-stu-id="f60d8-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>
```powershell
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

