---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Verschachteln von Konfigurationen
ms.openlocfilehash: e74c0fe1d7f7b198c2d6f796c0bf120eb0ec21d9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564016"
---
# <a name="nesting-dsc-configurations"></a>Verschachteln von DSC-Konfigurationen

Eine geschachtelte Konfiguration (auch zusammengesetzte Konfiguration genannt) ist eine Konfiguration, die in einer anderen Konfiguration aufgerufen wird, als handele es sich um eine Ressource. Beide Konfigurationen müssen in derselben Datei definiert werden.

Sehen wir uns ein einfaches Beispiel an:

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
    {
        SourcePath = $CopyFrom
        DestinationPath = $CopyTo
        Ensure = 'Present'
    }
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

In diesem Beispiel akzeptiert `FileConfig` zwei erforderliche Parameter – **CopyFrom** und **CopyTo**–, die als Werte für die Eigenschaften **SourcePath** und **DestinationPath** im Ressourcenblock `File` verwendet werden. Die Konfiguration `NestedConfig` ruft `FileConfig` auf, als handele es sich um eine Ressource. Die Eigenschaften im Ressourcenblock `NestedConfig` (**CopyFrom** und **CopyTo**) sind die Parameter der Konfiguration `FileConfig`.

DSC unterstützt aktuell keine geschachtelten Konfigurationen innerhalb von geschachtelten Konfigurationen. Sie können eine Konfiguration nur eine Ebene tief schachteln.

## <a name="see-also"></a>Weitere Informationen

- [Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource](../resources/authoringResourceComposite.md)
