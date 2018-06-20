---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34220341"
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="4bff5-102">Bedarfsgesteuerter PULL-Abruf von DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4bff5-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="4bff5-103">Das neue Cmdlet „Update-DscConfiguration“ löst auf den Pullservern, die in der Metakonfiguration definiert sind, einen Pullvorgang aus.</span><span class="sxs-lookup"><span data-stu-id="4bff5-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="4bff5-104">Das Verhalten wird häufig als „Jetzt per Pull abrufen“ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="4bff5-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="4bff5-105">Nach seinem Auslösen erfolgt der Pullvorgang genau so, wie er bei Auslösen gemäß dem herkömmlichen Zeitplan erfolgt wäre:</span><span class="sxs-lookup"><span data-stu-id="4bff5-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="4bff5-106">Die Prüfsumme für die aktuelle Konfiguration wird mit der Prüfsumme für die Konfiguration auf dem Pullserver verglichen.</span><span class="sxs-lookup"><span data-stu-id="4bff5-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="4bff5-107">Falls identisch, wird der Vorgang erfolgreich abgeschlossen, ohne die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="4bff5-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="4bff5-108">Falls verschieden, wird die Konfiguration vom Pullserver abgerufen und angewendet.</span><span class="sxs-lookup"><span data-stu-id="4bff5-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="4bff5-109">**Hinweis:** Wenn die Metakonfiguration „RefreshMode = Push“ lautet, wird von diesem Cmdlet ein Fehler zurückgegeben, weshalb dieses Cmdlet nichts unternimmt, wenn sich ein Zielknoten im Pushmodus befindet.</span><span class="sxs-lookup"><span data-stu-id="4bff5-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
