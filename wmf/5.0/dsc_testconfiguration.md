---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2d629d98b59c455011f4a5d955ef666218ae2f3f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="test-dscconfiguration-cmdlet-supports-reference-configurations" class="xliff"></a>
# Das Cmdlet „Test-DscConfiguration“ unterstützt Referenzkonfigurationen

Das Cmdlet „Test-DscConfiguration“ wurde so aktualisiert, dass es das Testen des gewünschten Konfigurationszustands eines oder mehrerer Zielknoten zulässt, indem zum Vergleich ein Referenzkonfigurationsdokument angegeben wird.

Der folgende neue Parameter verwendet DSC-Konfigurationen in dem Pfad, der angegeben wird, um jede Konfiguration auf den angegebenen Zielknoten zu testen, ohne sie anzuwenden. Wie bei „Start-DscConfiguration“ und anderen DSC-Cmdlets dient der Name der jeweiligen MOF-Datei zum Bestimmen des Zielknotens, auf dem die Konfiguration getestet werden soll. 

```PowerShell
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

```PowerShell
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

