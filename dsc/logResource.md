---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „Log“"
ms.openlocfilehash: 3bc4bf38b376cc62e42107eee1024eaabc93485a
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-log-resource"></a><span data-ttu-id="a50c3-103">DSC-Ressource „Log“</span><span class="sxs-lookup"><span data-stu-id="a50c3-103">DSC Log Resource</span></span> 

> <span data-ttu-id="a50c3-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a50c3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a50c3-105">Die Ressource __Log__ in Windows PowerShell DSC bietet einen Mechanismus zum Schreiben von Meldungen in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“.</span><span class="sxs-lookup"><span data-stu-id="a50c3-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

<span data-ttu-id="a50c3-106">HINWEIS: Standardmäßig sind nur die Betriebsprotokolle für DSC aktiviert.</span><span class="sxs-lookup"><span data-stu-id="a50c3-106">NOTE: By default only the Operational logs for DSC are enabled.</span></span>
<span data-ttu-id="a50c3-107">Das analytische Protokoll muss aktiviert werden, um verfügbar zu sein und angezeigt zu werden.</span><span class="sxs-lookup"><span data-stu-id="a50c3-107">Before the Analytic log will be available or visible, it must be enabled.</span></span>
<span data-ttu-id="a50c3-108">Weitere Informationen finden Sie in folgendem Artikel.</span><span class="sxs-lookup"><span data-stu-id="a50c3-108">See the following article.</span></span>

[<span data-ttu-id="a50c3-109">Wo befinden sich die DSC-Ereignisprotokolle?</span><span class="sxs-lookup"><span data-stu-id="a50c3-109">Where are DSC Event Logs?</span></span>](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a><span data-ttu-id="a50c3-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a50c3-110">Properties</span></span>
|  <span data-ttu-id="a50c3-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a50c3-111">Property</span></span>  |  <span data-ttu-id="a50c3-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a50c3-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="a50c3-113">Message</span><span class="sxs-lookup"><span data-stu-id="a50c3-113">Message</span></span>| <span data-ttu-id="a50c3-114">Gibt die Meldung an, die Sie in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ schreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="a50c3-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>| 
| <span data-ttu-id="a50c3-115">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a50c3-115">DependsOn</span></span> | <span data-ttu-id="a50c3-116">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Protokollmeldung geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="a50c3-116">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="a50c3-117">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a50c3-117">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="a50c3-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a50c3-118">Example</span></span>

<span data-ttu-id="a50c3-119">Im folgenden Beispiel wird veranschaulicht, wie Sie eine Meldung in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ einschließen.</span><span class="sxs-lookup"><span data-stu-id="a50c3-119">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> <span data-ttu-id="a50c3-120">**Hinweis**: Wenn Sie [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) mit dieser konfigurierten Ressource ausführen, wird stets **$false** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="a50c3-120">**Note**: if you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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

