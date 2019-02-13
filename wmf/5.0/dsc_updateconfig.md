---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679342"
---
# <a name="on-demand-pull-of-dsc-configurations"></a>Bedarfsgesteuerter PULL-Abruf von DSC-Konfigurationen

Das neue Cmdlet „Update-DscConfiguration“ löst auf den Pullservern, die in der Metakonfiguration definiert sind, einen Pullvorgang aus. Das Verhalten wird häufig als „Jetzt per Pull abrufen“ bezeichnet.


Nach seinem Auslösen erfolgt der Pullvorgang genau so, wie er bei Auslösen gemäß dem herkömmlichen Zeitplan erfolgt wäre:

1. Die Prüfsumme für die aktuelle Konfiguration wird mit der Prüfsumme für die Konfiguration auf dem Pullserver verglichen.
2. Falls identisch, wird der Vorgang erfolgreich abgeschlossen, ohne die Konfiguration anzuwenden.
3. Falls verschieden, wird die Konfiguration vom Pullserver abgerufen und angewendet.

**Hinweis:** Wenn die Metakonfiguration „RefreshMode = Push“ lautet, wird von diesem Cmdlet ein Fehler zurückgegeben, weshalb dieses Cmdlet nichts unternimmt, wenn sich ein Zielknoten im Pushmodus befindet.

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
