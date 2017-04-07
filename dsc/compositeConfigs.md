---
title: Verschachteln von Konfigurationen
ms.date: 2017-03-27
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: carmonm
ms.prod: powershell
ms.openlocfilehash: 3afc4c87b1bc54e5f251a3a54eab5f448900f124
ms.sourcegitcommit: 65250232157bb1c742d7d385933b8abc24a570fb
translationtype: HT
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

In diesem Beispiel akzeptiert `FileConfig` zwei erforderliche Parameter, **CopyFrom** und **CopyTo**, die als Werte für die Eigenschaften **SourcePath** und **DestinationPath** im Ressourcenblock `File` verwendet werden. Die Konfiguration `NestedConfig` ruft `FileConfig` auf, als handele es sich um eine Ressource.
Die Eigenschaften im Ressourcenblock `NestedConfig` (**CopyFrom** und **CopyTo**) sind die Parameter der Konfiguration `FileConfig`.

## <a name="see-also"></a>Weitere Informationen

- [Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource](authoringResourceComposite.md)
