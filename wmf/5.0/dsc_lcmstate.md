---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="3cc3b-102">Detaillierte Informationen zum LCM-Status</span><span class="sxs-lookup"><span data-stu-id="3cc3b-102">Detailed information about LCM state</span></span>

<span data-ttu-id="3cc3b-103">Wir haben das Verfügbarmachen von Details zum LCM-Status verbessert.</span><span class="sxs-lookup"><span data-stu-id="3cc3b-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="3cc3b-104">Der „LCMState“, der von „Get-DscLocalConfigurationManager“ zurückgegeben wird, kann jetzt die folgenden Werte enthalten:</span><span class="sxs-lookup"><span data-stu-id="3cc3b-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="3cc3b-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="3cc3b-105">**Idle**</span></span>
* <span data-ttu-id="3cc3b-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="3cc3b-106">**Busy**</span></span>
* <span data-ttu-id="3cc3b-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="3cc3b-107">**PendingReboot**</span></span>
* <span data-ttu-id="3cc3b-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="3cc3b-108">**PendingConfiguration**</span></span>

<span data-ttu-id="3cc3b-109">Wir haben auch die „LCMStateDetail“-Eigenschaft hinzugefügt, die weitere Statusinformationen enthält.</span><span class="sxs-lookup"><span data-stu-id="3cc3b-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>