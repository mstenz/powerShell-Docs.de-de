---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Log“
ms.openlocfilehash: a1b7bf44fbaf36a3adaf0666e9f0a754fa3f6ee1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954667"
---
# <a name="dsc-log-resource"></a><span data-ttu-id="4755c-103">DSC-Ressource „Log“</span><span class="sxs-lookup"><span data-stu-id="4755c-103">DSC Log Resource</span></span>

> <span data-ttu-id="4755c-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="4755c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="4755c-105">Die Ressource **Log** in Windows PowerShell DSC bietet einen Mechanismus zum Schreiben von Meldungen in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“.</span><span class="sxs-lookup"><span data-stu-id="4755c-105">The **Log** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to write messages to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

## <a name="syntax"></a><span data-ttu-id="4755c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4755c-106">Syntax</span></span>

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="4755c-107">Standardmäßig sind nur die Betriebsprotokolle für DSC aktiviert.</span><span class="sxs-lookup"><span data-stu-id="4755c-107">By default only the Operational logs for DSC are enabled.</span></span> <span data-ttu-id="4755c-108">Das analytische Protokoll muss aktiviert werden, um verfügbar zu sein und angezeigt zu werden.</span><span class="sxs-lookup"><span data-stu-id="4755c-108">Before the Analytic log will be available or visible, it must be enabled.</span></span> <span data-ttu-id="4755c-109">Weitere Informationen finden Sie im Abschnitt „Wo befinden sich die DSC-Ereignisprotokolle?“ im Artikel [Problembehandlung bei DSC](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="4755c-109">For more information, see [Where are DSC Event Logs?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs).</span></span>

## <a name="properties"></a><span data-ttu-id="4755c-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="4755c-110">Properties</span></span>

|<span data-ttu-id="4755c-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="4755c-111">Property</span></span> |<span data-ttu-id="4755c-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4755c-112">Description</span></span> |
|---|---|
|<span data-ttu-id="4755c-113">Message</span><span class="sxs-lookup"><span data-stu-id="4755c-113">Message</span></span> |<span data-ttu-id="4755c-114">Gibt die Meldung an, die Sie in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ schreiben möchten.</span><span class="sxs-lookup"><span data-stu-id="4755c-114">Indicates the message you want to write to the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4755c-115">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="4755c-115">Common properties</span></span>

|<span data-ttu-id="4755c-116">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="4755c-116">Property</span></span> |<span data-ttu-id="4755c-117">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4755c-117">Description</span></span> |
|---|---|
|<span data-ttu-id="4755c-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4755c-118">DependsOn</span></span> |<span data-ttu-id="4755c-119">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="4755c-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4755c-120">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4755c-120">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4755c-121">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4755c-121">PsDscRunAsCredential</span></span> |<span data-ttu-id="4755c-122">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="4755c-122">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4755c-123">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4755c-123">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4755c-124">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="4755c-124">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="4755c-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4755c-125">Example</span></span>

<span data-ttu-id="4755c-126">Im folgenden Beispiel wird veranschaulicht, wie Sie eine Meldung in das Ereignisprotokoll „Microsoft Windows Desired State Configuration/Analyse“ einschließen.</span><span class="sxs-lookup"><span data-stu-id="4755c-126">The following example shows how to include a message in the Microsoft-Windows-Desired State Configuration/Analytic event log.</span></span>

> [!NOTE]
> <span data-ttu-id="4755c-127">Wenn Sie [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) mit dieser konfigurierten Ressource ausführen, wird stets **$false** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="4755c-127">If you run [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) with this resource configured, it will always return **$false**.</span></span>

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