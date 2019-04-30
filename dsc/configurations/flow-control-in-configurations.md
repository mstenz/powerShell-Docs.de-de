---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Bedingte Anweisungen und Schleifen in Konfigurationen
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080134"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="f84c0-103">Bedingte Anweisungen und Schleifen in Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="f84c0-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="f84c0-104">Sie können Ihre [Konfigurationen](configurations.md) dynamischer gestalten, indem Sie Ablaufsteuerungs-Schlüsselwörter von PowerShell verwenden.</span><span class="sxs-lookup"><span data-stu-id="f84c0-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="f84c0-105">Dieser Artikel zeigt Ihnen, wie Sie bedingte Anweisungen und Schleifen verwenden können, um Ihre Konfigurationen dynamischer zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="f84c0-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="f84c0-106">Die Kombination von Bedingungen und Schleifen mit [Parametern](add-parameters-to-a-configuration.md) und [Konfigurationsdaten](configData.md) ermöglicht Ihnen mehr Flexibilität und Kontrolle bei der Kompilierung Ihrer Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f84c0-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="f84c0-107">Genau wie eine Funktion oder ein Skriptblock können Sie jede beliebige PowerShell-Sprache innerhalb einer Konfiguration verwenden.</span><span class="sxs-lookup"><span data-stu-id="f84c0-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="f84c0-108">Die von Ihnen verwendeten Anweisungen werden nur ausgewertet, wenn Sie Ihre Konfiguration aufrufen, um eine MOF-Datei zu kompilieren.</span><span class="sxs-lookup"><span data-stu-id="f84c0-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="f84c0-109">Die folgenden Beispiele zeigen einfache Szenarien zur Veranschaulichung der Konzepte.</span><span class="sxs-lookup"><span data-stu-id="f84c0-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="f84c0-110">Bedingte Anweisungen und Schleifen werden häufiger mit Parametern und Konfigurationsdaten verwendet.</span><span class="sxs-lookup"><span data-stu-id="f84c0-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="f84c0-111">In diesem einfachen Beispiel ruft der Ressourcenblock **Service** den aktuellen Zustand eines Diensts zur Kompilierungszeit ab, um eine MOF-Datei zu generieren, die ihren aktuellen Zustand beibehält.</span><span class="sxs-lookup"><span data-stu-id="f84c0-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="f84c0-112">Die Verwendung dynamischer Ressourcenblöcke verhindert die Effektivität von IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f84c0-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="f84c0-113">Der PowerShell-Parser kann nicht bestimmen, ob die angegebenen Werte akzeptabel sind, bis die Konfiguration kompiliert wurde.</span><span class="sxs-lookup"><span data-stu-id="f84c0-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="f84c0-114">Zusätzlich können Sie für jeden Dienst auf dem aktuellen Computer eine **Service**-Blockressource erstellen, indem Sie eine `foreach`-Schleife verwenden.</span><span class="sxs-lookup"><span data-stu-id="f84c0-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
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

<span data-ttu-id="f84c0-115">Sie können auch nur Konfigurationen für Computer erstellen, die online sind, indem Sie eine einfache `if`-Anweisung verwenden.</span><span class="sxs-lookup"><span data-stu-id="f84c0-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="f84c0-116">Die dynamischen Ressourcenblöcke in den oben aufgeführten Beispielen verweisen auf den aktuellen Computer.</span><span class="sxs-lookup"><span data-stu-id="f84c0-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="f84c0-117">In diesem Fall wäre das der Computer, auf dem Sie die Konfiguration erstellen, und nicht der Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="f84c0-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="f84c0-118">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="f84c0-118">Summary</span></span>

<span data-ttu-id="f84c0-119">Zusammenfassend lässt sich sagen, dass Sie jede beliebige PowerShell-Sprache innerhalb einer Konfiguration verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f84c0-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="f84c0-120">Dazu zählen etwa:</span><span class="sxs-lookup"><span data-stu-id="f84c0-120">This includes things like:</span></span>

- <span data-ttu-id="f84c0-121">Benutzerdefinierte Objekte</span><span class="sxs-lookup"><span data-stu-id="f84c0-121">Custom Objects</span></span>
- <span data-ttu-id="f84c0-122">Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="f84c0-122">Hashtables</span></span>
- <span data-ttu-id="f84c0-123">Zeichenfolgenbearbeitung</span><span class="sxs-lookup"><span data-stu-id="f84c0-123">String manipulation</span></span>
- <span data-ttu-id="f84c0-124">Remoting</span><span class="sxs-lookup"><span data-stu-id="f84c0-124">Remoting</span></span>
- <span data-ttu-id="f84c0-125">WMI und CIM</span><span class="sxs-lookup"><span data-stu-id="f84c0-125">WMI and CIM</span></span>
- <span data-ttu-id="f84c0-126">Active Directory-Objekte</span><span class="sxs-lookup"><span data-stu-id="f84c0-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="f84c0-127">und weitere...</span><span class="sxs-lookup"><span data-stu-id="f84c0-127">and more...</span></span>

<span data-ttu-id="f84c0-128">Der gesamte PowerShell-Code, der in einer Konfiguration definiert ist, wird während der Kompilierung ausgewertet, aber Sie können auch Code in das Skript einfügen, das Ihre Konfiguration enthält.</span><span class="sxs-lookup"><span data-stu-id="f84c0-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="f84c0-129">Der Code außerhalb des Konfigurationsblocks wird ausgeführt, wenn Sie Ihre Konfiguration importieren.</span><span class="sxs-lookup"><span data-stu-id="f84c0-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="f84c0-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f84c0-130">See also</span></span>

- [<span data-ttu-id="f84c0-131">Hinzufügen von Parametern zu einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="f84c0-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="f84c0-132">Trennen von Konfigurationsdaten von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="f84c0-132">Separate Configuration data from Configurations</span></span>](configData.md)
