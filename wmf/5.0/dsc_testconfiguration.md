---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Das Cmdlet „Test-DscConfiguration“ unterstützt Referenzkonfigurationen

Das Cmdlet „Test-DscConfiguration“ wurde so aktualisiert, dass es das Testen des gewünschten Konfigurationszustands eines oder mehrerer Zielknoten zulässt, indem zum Vergleich ein Referenzkonfigurationsdokument angegeben wird.

Der folgende neue Parameter verwendet DSC-Konfigurationen in dem Pfad, der angegeben wird, um jede Konfiguration auf den angegebenen Zielknoten zu testen, ohne sie anzuwenden. Wie bei „Start-DscConfiguration“ und anderen DSC-Cmdlets dient der Name der jeweiligen MOF-Datei zum Bestimmen des Zielknotens, auf dem die Konfiguration getestet werden soll.

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

Der folgende neue Parameter verwendet eine einzelne DSC-Konfiguration, um die Konfiguration auf den angegebenen Zielknoten zu testen, ohne sie anzuwenden.

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```
