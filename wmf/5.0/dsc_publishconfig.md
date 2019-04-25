---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085812"
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="832fc-102">Übermitteln des Konfigurationsdokuments, ohne es anzuwenden</span><span class="sxs-lookup"><span data-stu-id="832fc-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="832fc-103">Das Cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) kopiert eine MOF-Konfigurationsdatei auf einen Zielknoten, ohne die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="832fc-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="832fc-104">Diese Konfiguration wird während des nächsten Konsistenzdurchlaufs oder bei Ausführen des Cmdlets [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) angewendet.</span><span class="sxs-lookup"><span data-stu-id="832fc-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>
