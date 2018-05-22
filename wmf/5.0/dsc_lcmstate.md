---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a>Detaillierte Informationen zum LCM-Status

Wir haben das Verfügbarmachen von Details zum LCM-Status verbessert. Der „LCMState“, der von „Get-DscLocalConfigurationManager“ zurückgegeben wird, kann jetzt die folgenden Werte enthalten:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Wir haben auch die „LCMStateDetail“-Eigenschaft hinzugefügt, die weitere Statusinformationen enthält.
