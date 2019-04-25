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
# <a name="detailed-information-about-lcm-state"></a>Detaillierte Informationen zum LCM-Status

Wir haben das Verfügbarmachen von Details zum LCM-Status verbessert. Der „LCMState“, der von „Get-DscLocalConfigurationManager“ zurückgegeben wird, kann jetzt die folgenden Werte enthalten:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Wir haben auch die „LCMStateDetail“-Eigenschaft hinzugefügt, die weitere Statusinformationen enthält.
