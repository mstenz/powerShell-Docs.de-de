---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="3e48f-102">Detaillierte Informationen zum LCM-Status</span><span class="sxs-lookup"><span data-stu-id="3e48f-102">Detailed information about LCM state</span></span>

<span data-ttu-id="3e48f-103">Wir haben das Verfügbarmachen von Details zum LCM-Status verbessert.</span><span class="sxs-lookup"><span data-stu-id="3e48f-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="3e48f-104">Der „LCMState“, der von „Get-DscLocalConfigurationManager“ zurückgegeben wird, kann jetzt die folgenden Werte enthalten:</span><span class="sxs-lookup"><span data-stu-id="3e48f-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="3e48f-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="3e48f-105">**Idle**</span></span>
* <span data-ttu-id="3e48f-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="3e48f-106">**Busy**</span></span>
* <span data-ttu-id="3e48f-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="3e48f-107">**PendingReboot**</span></span>
* <span data-ttu-id="3e48f-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="3e48f-108">**PendingConfiguration**</span></span>

<span data-ttu-id="3e48f-109">Wir haben auch die „LCMStateDetail“-Eigenschaft hinzugefügt, die weitere Statusinformationen enthält.</span><span class="sxs-lookup"><span data-stu-id="3e48f-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
