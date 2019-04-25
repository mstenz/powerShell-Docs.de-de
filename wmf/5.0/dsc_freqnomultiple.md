---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058402"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="43842-102">Frequenzen für „RefreshMode“ und „ConfigurationMode“ müssen keine Vielfache des jeweils anderen sein</span><span class="sxs-lookup"><span data-stu-id="43842-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="43842-103">In der vorherigen Version von DSC behandelt der LCM `RefreshFrequencyMins` und `ConfigurationModeFrequencyMins` als Vielfaches des jeweils anderen.</span><span class="sxs-lookup"><span data-stu-id="43842-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="43842-104">In WMF 5.0 RTM werden diese Eigenschaften unabhängig voneinander verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="43842-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="43842-105">Weitere Informationen finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="43842-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
