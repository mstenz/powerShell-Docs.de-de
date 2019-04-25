---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085795"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="1f06c-102">Detaillierte Informationen zum LCM-Status</span><span class="sxs-lookup"><span data-stu-id="1f06c-102">Detailed information about LCM state</span></span>

<span data-ttu-id="1f06c-103">Wir haben das Verfügbarmachen von Details zum LCM-Status verbessert.</span><span class="sxs-lookup"><span data-stu-id="1f06c-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="1f06c-104">Der „LCMState“, der von „Get-DscLocalConfigurationManager“ zurückgegeben wird, kann jetzt die folgenden Werte enthalten:</span><span class="sxs-lookup"><span data-stu-id="1f06c-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="1f06c-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="1f06c-105">**Idle**</span></span>
* <span data-ttu-id="1f06c-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="1f06c-106">**Busy**</span></span>
* <span data-ttu-id="1f06c-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="1f06c-107">**PendingReboot**</span></span>
* <span data-ttu-id="1f06c-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="1f06c-108">**PendingConfiguration**</span></span>

<span data-ttu-id="1f06c-109">Wir haben auch die „LCMStateDetail“-Eigenschaft hinzugefügt, die weitere Statusinformationen enthält.</span><span class="sxs-lookup"><span data-stu-id="1f06c-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
