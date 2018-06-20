---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218381"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frequenzen für „RefreshMode“ und „ConfigurationMode“ müssen keine Vielfache des jeweils anderen sein

In der vorherigen Version von DSC behandelt der LCM `RefreshFrequencyMins` und `ConfigurationModeFrequencyMins` als Vielfaches des jeweils anderen. In WMF 5.0 RTM werden diese Eigenschaften unabhängig voneinander verarbeitet.

Weitere Informationen finden Sie unter [Konfigurieren des lokalen Konfigurations-Managers](https://msdn.microsoft.com/powershell/dsc/metaconfig).
