---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 18c1dab7412b8e9d31960507b612dd6cc56d31d5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="a5313-102">Das Cmdlet „Test-DscConfiguration“ unterstützt Referenzkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="a5313-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="a5313-103">Das Cmdlet „Test-DscConfiguration“ wurde so aktualisiert, dass es das Testen des gewünschten Konfigurationszustands eines oder mehrerer Zielknoten zulässt, indem zum Vergleich ein Referenzkonfigurationsdokument angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a5313-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="a5313-104">Der folgende neue Parameter verwendet DSC-Konfigurationen in dem Pfad, der angegeben wird, um jede Konfiguration auf den angegebenen Zielknoten zu testen, ohne sie anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="a5313-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="a5313-105">Wie bei „Start-DscConfiguration“ und anderen DSC-Cmdlets dient der Name der jeweiligen MOF-Datei zum Bestimmen des Zielknotens, auf dem die Konfiguration getestet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a5313-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

<span data-ttu-id="a5313-106">Der folgende neue Parameter verwendet eine einzelne DSC-Konfiguration, um die Konfiguration auf den angegebenen Zielknoten zu testen, ohne sie anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="a5313-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```