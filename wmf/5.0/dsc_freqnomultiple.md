---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="9b399-102">Frequenzen für „RefreshMode“ und „ConfigurationMode“ müssen keine Vielfache des jeweils anderen sein</span><span class="sxs-lookup"><span data-stu-id="9b399-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="9b399-103">In der vorherigen Version von DSC behandelt der LCM `RefreshFrequencyMins` und `ConfigurationModeFrequencyMins` als Vielfaches des jeweils anderen.</span><span class="sxs-lookup"><span data-stu-id="9b399-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="9b399-104">In WMF 5.0 RTM werden diese Eigenschaften unabhängig voneinander verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="9b399-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="9b399-105">Weitere Informationen finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="9b399-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>