---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058742"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="ec23d-102">Das Cmdlet „Test-DscConfiguration“ unterstützt Referenzkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="ec23d-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="ec23d-103">Das Cmdlet „Test-DscConfiguration“ wurde so aktualisiert, dass es das Testen des gewünschten Konfigurationszustands eines oder mehrerer Zielknoten zulässt, indem zum Vergleich ein Referenzkonfigurationsdokument angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="ec23d-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="ec23d-104">Der folgende neue Parameter verwendet DSC-Konfigurationen in dem Pfad, der angegeben wird, um jede Konfiguration auf den angegebenen Zielknoten zu testen, ohne sie anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="ec23d-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="ec23d-105">Wie bei „Start-DscConfiguration“ und anderen DSC-Cmdlets dient der Name der jeweiligen MOF-Datei zum Bestimmen des Zielknotens, auf dem die Konfiguration getestet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ec23d-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="ec23d-106">Der folgende neue Parameter verwendet eine einzelne DSC-Konfiguration, um die Konfiguration auf den angegebenen Zielknoten zu testen, ohne sie anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="ec23d-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
