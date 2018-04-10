---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Log“
ms.openlocfilehash: f1a528767508d4a0e7f0ea2e58fd27a6a4d7ec75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-log-resource"></a><span data-ttu-id="7d2af-103">DSC-Ressource „Log“</span><span class="sxs-lookup"><span data-stu-id="7d2af-103">DSC Log Resource</span></span>

> <span data-ttu-id="7d2af-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7d2af-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7d2af-105">Die Ressource __Log__ in Windows PowerShell DSC bietet einen Mechanismus zum Schreiben von Meldungen in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“.</span><span class="sxs-lookup"><span data-stu-id="7d2af-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="7d2af-106">HINWEIS: Standardmäßig sind nur die Betriebsprotokolle für DSC aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7d2af-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="7d2af-107">Das analytische Protokoll muss aktiviert werden, um verfügbar zu sein und angezeigt zu werden.</span><span class="sxs-lookup"><span data-stu-id="7d2af-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="7d2af-108">Weitere Informationen finden Sie in folgendem Artikel.</span><span class="sxs-lookup"><span data-stu-id="7d2af-108">See the following article.</span></span>

[<span data-ttu-id="7d2af-109">Wo befinden sich die DSC-Ereignisprotokolle?</span><span class="sxs-lookup"><span data-stu-id="7d2af-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="7d2af-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="7d2af-110">Properties</span></span>
|  <span data-ttu-id="7d2af-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="7d2af-111">Property</span></span>  |  <span data-ttu-id="7d2af-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7d2af-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="7d2af-113">Message</span><span class="sxs-lookup"><span data-stu-id="7d2af-113">Message</span></span>| <span data-ttu-id="7d2af-114">Gibt die Meldung an, die Sie in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ schreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="7d2af-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="7d2af-115">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7d2af-115">DependsOn</span></span> | <span data-ttu-id="7d2af-116">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Protokollmeldung geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="7d2af-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="7d2af-117">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7d2af-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="7d2af-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7d2af-118">Example</span></span>

<span data-ttu-id="7d2af-119">Im folgenden Beispiel wird veranschaulicht, wie Sie eine Meldung in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ einschließen.</span><span class="sxs-lookup"><span data-stu-id="7d2af-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="7d2af-120">**Hinweis**: Wenn Sie [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) mit dieser konfigurierten Ressource ausführen, wird stets **$false** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7d2af-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost

    {
        Log LogExample
        {
            Message = "This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log."
        }
    }
}
```