---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Verschachteln von Konfigurationen
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080236"
---
# <a name="nesting-dsc-configurations"></a>Verschachteln von DSC-Konfigurationen

Eine geschachtelte Konfiguration (auch zusammengesetzte Konfiguration genannt) ist eine Konfiguration, die in einer anderen Konfiguration aufgerufen wird, als handele es sich um eine Ressource.
Beide Konfigurationen müssen in derselben Datei definiert werden.

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

In diesem Beispiel akzeptiert `FileConfig` zwei erforderliche Parameter, **CopyFrom** und **CopyTo**, die als Werte für die Eigenschaften **SourcePath** und **DestinationPath** im Ressourcenblock `File` verwendet werden.
Die Konfiguration `NestedConfig` ruft `FileConfig` auf, als handele es sich um eine Ressource.
Die Eigenschaften im Ressourcenblock `NestedConfig` (**CopyFrom** und **CopyTo**) sind die Parameter der Konfiguration `FileConfig`.

## <a name="see-also"></a>Weitere Informationen

- [Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource](../resources/authoringResourceComposite.md)