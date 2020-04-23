---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Verschachteln von Konfigurationen
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75417868"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="58630-103">Verschachteln von DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="58630-103">Nesting DSC configurations</span></span>

<span data-ttu-id="58630-104">Eine geschachtelte Konfiguration (auch zusammengesetzte Konfiguration genannt) ist eine Konfiguration, die in einer anderen Konfiguration aufgerufen wird, als handele es sich um eine Ressource.</span><span class="sxs-lookup"><span data-stu-id="58630-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="58630-105">Beide Konfigurationen müssen in derselben Datei definiert werden.</span><span class="sxs-lookup"><span data-stu-id="58630-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="58630-106">Sehen wir uns ein einfaches Beispiel an:</span><span class="sxs-lookup"><span data-stu-id="58630-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="58630-107">In diesem Beispiel akzeptiert `FileConfig` zwei erforderliche Parameter – **CopyFrom** und **CopyTo**–, die als Werte für die Eigenschaften **SourcePath** und **DestinationPath** im Ressourcenblock `File` verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="58630-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="58630-108">Die Konfiguration `NestedConfig` ruft `FileConfig` auf, als handele es sich um eine Ressource.</span><span class="sxs-lookup"><span data-stu-id="58630-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="58630-109">Die Eigenschaften im Ressourcenblock `NestedConfig` (**CopyFrom** und **CopyTo**) sind die Parameter der Konfiguration `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="58630-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="58630-110">DSC unterstützt aktuell keine geschachtelten Konfigurationen innerhalb von geschachtelten Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="58630-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="58630-111">Sie können eine Konfiguration nur eine Ebene tief schachteln.</span><span class="sxs-lookup"><span data-stu-id="58630-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="58630-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="58630-112">See Also</span></span>

- [<span data-ttu-id="58630-113">Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource</span><span class="sxs-lookup"><span data-stu-id="58630-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)