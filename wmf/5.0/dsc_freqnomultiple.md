---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frequenzen für „RefreshMode“ und „ConfigurationMode“ müssen keine Vielfache des jeweils anderen sein

In der vorherigen Version von DSC behandelt der LCM `RefreshFrequencyMins` und `ConfigurationModeFrequencyMins` als Vielfaches des jeweils anderen. In WMF 5.0 RTM werden diese Eigenschaften unabhängig voneinander verarbeitet. 

Weitere Informationen finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](https://msdn.microsoft.com/powershell/dsc/metaconfig).

