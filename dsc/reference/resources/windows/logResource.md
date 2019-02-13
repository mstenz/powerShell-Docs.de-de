---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Log“
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677765"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="b60b4-103">DSC-Ressource „Log“</span><span class="sxs-lookup"><span data-stu-id="b60b4-103">DSC Log Resource</span></span>

> <span data-ttu-id="b60b4-104">_Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="b60b4-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="b60b4-105">Die Ressource __Log__ in Windows PowerShell DSC bietet einen Mechanismus zum Schreiben von Meldungen in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“.</span><span class="sxs-lookup"><span data-stu-id="b60b4-105">The __Log__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> <span data-ttu-id="b60b4-106">Standardmäßig sind nur die Betriebsprotokolle für DSC aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b60b4-106">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="b60b4-107">Das analytische Protokoll muss aktiviert werden, um verfügbar zu sein und angezeigt zu werden.</span><span class="sxs-lookup"><span data-stu-id="b60b4-107">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="b60b4-108">Weitere Informationen finden Sie im Abschnitt „Wo befinden sich die DSC-Ereignisprotokolle?“ im Artikel [Problembehandlung bei DSC](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="b60b4-108">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="b60b4-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="b60b4-109">Properties</span></span>

| <span data-ttu-id="b60b4-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b60b4-110">Property</span></span> | <span data-ttu-id="b60b4-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b60b4-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b60b4-112">Message</span><span class="sxs-lookup"><span data-stu-id="b60b4-112">Message</span></span>| <span data-ttu-id="b60b4-113">Gibt die Meldung an, die Sie in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ schreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="b60b4-113">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>|
| <span data-ttu-id="b60b4-114">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b60b4-114">DependsOn</span></span> | <span data-ttu-id="b60b4-115">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Protokollmeldung geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="b60b4-115">Indicates that the configuration of another resource must run before this log message gets written.</span></span> <span data-ttu-id="b60b4-116">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = '[ResourceType]ResourceName'`.</span><span class="sxs-lookup"><span data-stu-id="b60b4-116">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = '[ResourceType]ResourceName'`.</span></span>|

## <a name="example"></a><span data-ttu-id="b60b4-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b60b4-117">Example</span></span>

<span data-ttu-id="b60b4-118">Im folgenden Beispiel wird veranschaulicht, wie Sie eine Meldung in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ einschließen.</span><span class="sxs-lookup"><span data-stu-id="b60b4-118">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="b60b4-119">Wenn Sie [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) mit dieser konfigurierten Ressource ausführen, wird stets **$false** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b60b4-119">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
