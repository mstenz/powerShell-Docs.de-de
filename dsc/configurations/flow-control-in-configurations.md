---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Bedingte Anweisungen und Schleifen in Konfigurationen
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401250"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="36e28-103">Bedingte Anweisungen und Schleifen in Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="36e28-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="36e28-104">Möglich Ihre [Konfigurationen](configurations.md) dynamischer PowerShell flusssteuerung Schlüsselwörter verwenden.</span><span class="sxs-lookup"><span data-stu-id="36e28-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="36e28-105">In diesem Artikel zeigt Ihnen, wie Sie bedingungsanweisungen und Schleifen verwenden können, um Ihre Konfigurationen dynamischer gestalten.</span><span class="sxs-lookup"><span data-stu-id="36e28-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="36e28-106">Kombinieren von bedingten und Schleifen mit [Parameter](add-parameters-to-a-configuration.md) und [Konfigurationsdaten](configData.md) ermöglicht Ihnen mehr Flexibilität und Kontrolle beim Kompilieren von Konfigurationen Ihrer.</span><span class="sxs-lookup"><span data-stu-id="36e28-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="36e28-107">Genau wie eine Funktion oder ein Skriptblock können Sie alle PowerShell-Sprache in einer Konfiguration verwenden.</span><span class="sxs-lookup"><span data-stu-id="36e28-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="36e28-108">Die Anweisungen, die Sie verwenden, werden nur ausgewertet, wenn Sie Ihre Konfiguration, um eine "MOF"-Datei kompilieren aufrufen.</span><span class="sxs-lookup"><span data-stu-id="36e28-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="36e28-109">Die folgenden Beispiele zeigen die einfache Szenarios zur Veranschaulichung der Konzepte.</span><span class="sxs-lookup"><span data-stu-id="36e28-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="36e28-110">Konditionelle Abschnitte bereit sind, Schleifen mit Parametern und Konfigurationsdaten, die häufiger verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="36e28-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="36e28-111">In diesem einfachen Beispiel der **Service** Ressourcenblock Ruft den aktuellen Zustand eines Diensts, zum Zeitpunkt der Kompilierung zu eine "MOF"-Datei generiert, die den aktuellen Zustand beibehält.</span><span class="sxs-lookup"><span data-stu-id="36e28-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="36e28-112">Mithilfe von dynamischen ressourcenblöcke, wird die Effektivität von Intellisense verdrängen.</span><span class="sxs-lookup"><span data-stu-id="36e28-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="36e28-113">Der PowerShell-Parser kann nicht bestimmen, wenn die angegebenen Werte zulässig sind, bis die Konfiguration kompiliert wird.</span><span class="sxs-lookup"><span data-stu-id="36e28-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="36e28-114">Darüber hinaus können Sie erstellen eine **Service** blockieren Ressource für jeden Dienst auf dem aktuellen Computer mit einer `foreach` Schleife.</span><span class="sxs-lookup"><span data-stu-id="36e28-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

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

<span data-ttu-id="36e28-115">Sie können auch nur Konfigurationen für Computer, die online sind, mithilfe einer einfaches erstellen `if` Anweisung.</span><span class="sxs-lookup"><span data-stu-id="36e28-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

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
> <span data-ttu-id="36e28-116">Die dynamische Ressource, die in den obigen Beispielen Verweis den aktuellen Computer blockiert.</span><span class="sxs-lookup"><span data-stu-id="36e28-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="36e28-117">In dieser Instanz, die dem Computer erstellen Sie die Konfiguration auf, nicht das Ziel-Knoten.</span><span class="sxs-lookup"><span data-stu-id="36e28-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="36e28-118">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="36e28-118">Summary</span></span>

<span data-ttu-id="36e28-119">Zusammengefasst können Sie alle PowerShell-Sprache in einer Konfiguration verwenden.</span><span class="sxs-lookup"><span data-stu-id="36e28-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="36e28-120">Dazu zählen z. B.:</span><span class="sxs-lookup"><span data-stu-id="36e28-120">This includes things like:</span></span>

- <span data-ttu-id="36e28-121">Benutzerdefinierte Objekte</span><span class="sxs-lookup"><span data-stu-id="36e28-121">Custom Objects</span></span>
- <span data-ttu-id="36e28-122">Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="36e28-122">Hashtables</span></span>
- <span data-ttu-id="36e28-123">Zeichenfolgenbearbeitung</span><span class="sxs-lookup"><span data-stu-id="36e28-123">String manipulation</span></span>
- <span data-ttu-id="36e28-124">Remoting</span><span class="sxs-lookup"><span data-stu-id="36e28-124">Remoting</span></span>
- <span data-ttu-id="36e28-125">WMI- und CIM</span><span class="sxs-lookup"><span data-stu-id="36e28-125">WMI and CIM</span></span>
- <span data-ttu-id="36e28-126">Active Directory-Objekten</span><span class="sxs-lookup"><span data-stu-id="36e28-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="36e28-127">und weitere...</span><span class="sxs-lookup"><span data-stu-id="36e28-127">and more...</span></span>

<span data-ttu-id="36e28-128">Alle PowerShell-Code in einer Konfiguration definierten Zeitpunkt der Kompilierung ausgewertet werden, aber Sie können auch Code in das Skript mit der Konfiguration platzieren.</span><span class="sxs-lookup"><span data-stu-id="36e28-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="36e28-129">Code außerhalb des Blocks für die Konfiguration wird ausgeführt werden, wenn Sie Ihre Konfiguration importieren.</span><span class="sxs-lookup"><span data-stu-id="36e28-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="36e28-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="36e28-130">See also</span></span>

- [<span data-ttu-id="36e28-131">Hinzufügen von Parametern zu einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="36e28-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="36e28-132">Trennen von Konfigurationsdaten von Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="36e28-132">Separate Configuration data from Configurations</span></span>](configData.md)
