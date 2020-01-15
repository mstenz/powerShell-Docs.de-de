---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Bedingte Anweisungen und Schleifen in Konfigurationen
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736895"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="92d60-103">Bedingte Anweisungen und Schleifen in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="92d60-103">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="92d60-104">Sie können Ihre [Konfiguration](configurations.md) dynamischer gestalten, indem Sie PowerShell-Schlüsselwörter für die Ablaufsteuerung verwenden.</span><span class="sxs-lookup"><span data-stu-id="92d60-104">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="92d60-105">Dieser Artikel zeigt Ihnen, wie Sie bedingte Anweisungen und Schleifen verwenden können, um Ihre `Configuration` dynamischer zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="92d60-105">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="92d60-106">Die Kombination von Bedingungen und Schleifen mit [Parametern](add-parameters-to-a-configuration.md) und [Konfigurationsdaten](configData.md) ermöglicht Ihnen mehr Flexibilität und Kontrolle bei der Kompilierung Ihrer `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="92d60-106">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="92d60-107">Genau wie eine Funktion oder ein Skriptblock können Sie jedes beliebige PowerShell-Sprachfeature innerhalb einer `Configuration` verwenden.</span><span class="sxs-lookup"><span data-stu-id="92d60-107">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span>
<span data-ttu-id="92d60-108">Die von Ihnen verwendeten Anweisungen werden nur ausgewertet, wenn Sie Ihre `Configuration` aufrufen, um eine `.mof`-Datei zu kompilieren.</span><span class="sxs-lookup"><span data-stu-id="92d60-108">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="92d60-109">Die folgenden Beispiele zeigen Szenarien zur Veranschaulichung der Konzepte.</span><span class="sxs-lookup"><span data-stu-id="92d60-109">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="92d60-110">Bedingte Anweisungen und Schleifen werden häufiger mit Parametern und Konfigurationsdaten verwendet.</span><span class="sxs-lookup"><span data-stu-id="92d60-110">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="92d60-111">In diesem Beispiel ruft der Ressourcenblock **Service** den aktuellen Zustand eines Diensts zur Kompilierungszeit ab, um eine `.mof`-Datei zu generieren, die ihren aktuellen Zustand beibehält.</span><span class="sxs-lookup"><span data-stu-id="92d60-111">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="92d60-112">Die Verwendung dynamischer Ressourcenblöcke verhindert die Effektivität von IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="92d60-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="92d60-113">Der PowerShell-Parser kann nicht bestimmen, ob die angegebenen Werte akzeptabel sind, bis die `Configuration` kompiliert wurde.</span><span class="sxs-lookup"><span data-stu-id="92d60-113">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="92d60-114">Zusätzlich können Sie für jeden Dienst auf dem aktuellen Computer einen **Service**-Ressourcenblock erstellen, indem Sie eine `foreach`-Schleife verwenden.</span><span class="sxs-lookup"><span data-stu-id="92d60-114">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="92d60-115">Sie können mithilfe einer `if`-Anweisung auch eine `Configuration` nur für Computer erstellen, die online sind.</span><span class="sxs-lookup"><span data-stu-id="92d60-115">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="92d60-116">Die dynamischen Ressourcenblöcke in den oben aufgeführten Beispielen verweisen auf den aktuellen Computer.</span><span class="sxs-lookup"><span data-stu-id="92d60-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="92d60-117">In diesem Fall wäre das der Computer, auf dem Sie die `Configuration` erstellen, nicht der Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="92d60-117">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="92d60-118">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="92d60-118">Summary</span></span>

<span data-ttu-id="92d60-119">Zusammenfassend lässt sich sagen, dass Sie jedes beliebige PowerShell-Sprachfeature innerhalb einer `Configuration` verwenden können.</span><span class="sxs-lookup"><span data-stu-id="92d60-119">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="92d60-120">Dazu zählen etwa:</span><span class="sxs-lookup"><span data-stu-id="92d60-120">This includes things like:</span></span>

- <span data-ttu-id="92d60-121">Benutzerdefinierte Objekte</span><span class="sxs-lookup"><span data-stu-id="92d60-121">Custom Objects</span></span>
- <span data-ttu-id="92d60-122">Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="92d60-122">Hashtables</span></span>
- <span data-ttu-id="92d60-123">Zeichenfolgenbearbeitung</span><span class="sxs-lookup"><span data-stu-id="92d60-123">String manipulation</span></span>
- <span data-ttu-id="92d60-124">Remoting</span><span class="sxs-lookup"><span data-stu-id="92d60-124">Remoting</span></span>
- <span data-ttu-id="92d60-125">WMI und CIM</span><span class="sxs-lookup"><span data-stu-id="92d60-125">WMI and CIM</span></span>
- <span data-ttu-id="92d60-126">Active Directory-Objekte</span><span class="sxs-lookup"><span data-stu-id="92d60-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="92d60-127">und weitere...</span><span class="sxs-lookup"><span data-stu-id="92d60-127">and more...</span></span>

<span data-ttu-id="92d60-128">Der gesamte PowerShell-Code, der in einer `Configuration` definiert ist, wird während der Kompilierung ausgewertet, aber Sie können auch Code in das Skript einfügen, das Ihre `Configuration` enthält.</span><span class="sxs-lookup"><span data-stu-id="92d60-128">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="92d60-129">Sämtlicher Code, der sich außerhalb des `Configuration`-Blocks befindet, wird beim Import Ihrer `Configuration` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="92d60-129">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="92d60-130">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="92d60-130">See also</span></span>

- [<span data-ttu-id="92d60-131">Hinzufügen von Parametern zu einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="92d60-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="92d60-132">Trennen von Konfigurationsdaten von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="92d60-132">Separate Configuration data from Configurations</span></span>](configData.md)
