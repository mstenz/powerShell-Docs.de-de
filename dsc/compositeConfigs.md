---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Verschachteln von Konfigurationen
ms.openlocfilehash: 7ab58f3c59788be47312c460a626caa8a9922262
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218993"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="155da-103">Verschachteln von DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="155da-103">Nesting DSC configurations</span></span>

<span data-ttu-id="155da-104">Eine geschachtelte Konfiguration (auch zusammengesetzte Konfiguration genannt) ist eine Konfiguration, die in einer anderen Konfiguration aufgerufen wird, als handele es sich um eine Ressource.</span><span class="sxs-lookup"><span data-stu-id="155da-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="155da-105">Beide Konfigurationen müssen in derselben Datei definiert werden.</span><span class="sxs-lookup"><span data-stu-id="155da-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="155da-106">Sehen wir uns ein einfaches Beispiel an:</span><span class="sxs-lookup"><span data-stu-id="155da-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="155da-107">In diesem Beispiel akzeptiert `FileConfig` zwei erforderliche Parameter, **CopyFrom** und **CopyTo**, die als Werte für die Eigenschaften **SourcePath** und **DestinationPath** im Ressourcenblock `File` verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="155da-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span>
<span data-ttu-id="155da-108">Die Konfiguration `NestedConfig` ruft `FileConfig` auf, als handele es sich um eine Ressource.</span><span class="sxs-lookup"><span data-stu-id="155da-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="155da-109">Die Eigenschaften im Ressourcenblock `NestedConfig` (**CopyFrom** und **CopyTo**) sind die Parameter der Konfiguration `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="155da-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="155da-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="155da-110">See Also</span></span>

- [<span data-ttu-id="155da-111">Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource</span><span class="sxs-lookup"><span data-stu-id="155da-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)