---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e921a5ead21f52b7e0d9efd9335c44b99d7d6802
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="6dfe9-102">Übermitteln des Konfigurationsdokuments, ohne es anzuwenden</span><span class="sxs-lookup"><span data-stu-id="6dfe9-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="6dfe9-103">Das Cmdlet [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) kopiert eine MOF-Konfigurationsdatei auf einen Zielknoten, ohne die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="6dfe9-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span> <span data-ttu-id="6dfe9-104">Diese Konfiguration wird während des nächsten Konsistenzdurchlaufs oder bei Ausführen des Cmdlets [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) angewendet.</span><span class="sxs-lookup"><span data-stu-id="6dfe9-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>

