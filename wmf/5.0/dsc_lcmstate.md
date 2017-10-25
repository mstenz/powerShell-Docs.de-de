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
# <a name="detailed-information-about-lcm-state"></a>Detaillierte Informationen zum LCM-Status

Wir haben das Verfügbarmachen von Details zum LCM-Status verbessert. Der „LCMState“, der von „Get-DscLocalConfigurationManager“ zurückgegeben wird, kann jetzt die folgenden Werte enthalten:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Wir haben auch die „LCMStateDetail“-Eigenschaft hinzugefügt, die weitere Statusinformationen enthält.

