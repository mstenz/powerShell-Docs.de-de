---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="a1951-102">Detaillierte Informationen zum LCM-Status</span><span class="sxs-lookup"><span data-stu-id="a1951-102">Detailed information about LCM state</span></span>

<span data-ttu-id="a1951-103">Wir haben das Verfügbarmachen von Details zum LCM-Status verbessert.</span><span class="sxs-lookup"><span data-stu-id="a1951-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="a1951-104">Der „LCMState“, der von „Get-DscLocalConfigurationManager“ zurückgegeben wird, kann jetzt die folgenden Werte enthalten:</span><span class="sxs-lookup"><span data-stu-id="a1951-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="a1951-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="a1951-105">**Idle**</span></span>
* <span data-ttu-id="a1951-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="a1951-106">**Busy**</span></span>
* <span data-ttu-id="a1951-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="a1951-107">**PendingReboot**</span></span>
* <span data-ttu-id="a1951-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="a1951-108">**PendingConfiguration**</span></span>

<span data-ttu-id="a1951-109">Wir haben auch die „LCMStateDetail“-Eigenschaft hinzugefügt, die weitere Statusinformationen enthält.</span><span class="sxs-lookup"><span data-stu-id="a1951-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

