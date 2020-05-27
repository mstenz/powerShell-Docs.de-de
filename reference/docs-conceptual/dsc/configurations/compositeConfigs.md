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
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="d0043-103">Verschachteln von DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="d0043-103">Nesting DSC configurations</span></span>

<span data-ttu-id="d0043-104">Eine geschachtelte Konfiguration (auch zusammengesetzte Konfiguration genannt) ist eine Konfiguration, die in einer anderen Konfiguration aufgerufen wird, als handele es sich um eine Ressource.</span><span class="sxs-lookup"><span data-stu-id="d0043-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="d0043-105">Beide Konfigurationen müssen in derselben Datei definiert werden.</span><span class="sxs-lookup"><span data-stu-id="d0043-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="d0043-106">Sehen wir uns ein einfaches Beispiel an:</span><span class="sxs-lookup"><span data-stu-id="d0043-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="d0043-107">In diesem Beispiel akzeptiert `FileConfig` zwei erforderliche Parameter – **CopyFrom** und **CopyTo**–, die als Werte für die Eigenschaften **SourcePath** und **DestinationPath** im Ressourcenblock `File` verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d0043-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="d0043-108">Die Konfiguration `NestedConfig` ruft `FileConfig` auf, als handele es sich um eine Ressource.</span><span class="sxs-lookup"><span data-stu-id="d0043-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="d0043-109">Die Eigenschaften im Ressourcenblock `NestedConfig` (**CopyFrom** und **CopyTo**) sind die Parameter der Konfiguration `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="d0043-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="d0043-110">DSC unterstützt aktuell keine geschachtelten Konfigurationen innerhalb von geschachtelten Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d0043-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="d0043-111">Sie können eine Konfiguration nur eine Ebene tief schachteln.</span><span class="sxs-lookup"><span data-stu-id="d0043-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0043-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d0043-112">See Also</span></span>

- [<span data-ttu-id="d0043-113">Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource</span><span class="sxs-lookup"><span data-stu-id="d0043-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)
