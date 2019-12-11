---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Schreiben einer Einzelinstanz-DSC-Ressource (empfohlen)
ms.openlocfilehash: 4d9e07c6aaa064f808a03d4252e8d352b82183ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952817"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="4eced-103">Schreiben einer Einzelinstanz-DSC-Ressource (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="4eced-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="4eced-104">**Hinweis:** In diesem Thema wird ein bewährtes Verfahren zum Definieren einer DSC-Ressource beschrieben, die nur eine einzige Instanz in einer Konfiguration zulässt.</span><span class="sxs-lookup"><span data-stu-id="4eced-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="4eced-105">Derzeit gibt es hierfür keine integrierte DSC-Funktion.</span><span class="sxs-lookup"><span data-stu-id="4eced-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="4eced-106">Dies kann sich zukünftig ändern.</span><span class="sxs-lookup"><span data-stu-id="4eced-106">That might change in the future.</span></span>

<span data-ttu-id="4eced-107">Es gibt Situationen, in denen Sie für eine Ressource nicht zulassen möchten, dass sie mehrmals in einer Konfiguration verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4eced-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="4eced-108">Beispielsweise konnte in einer früheren Implementierung der [xTimeZone](https://github.com/PowerShell/xTimeZone)-Ressource eine Konfiguration die Ressource mehrmals aufrufen, wodurch die Zeitzone in jedem Ressourcenblock auf eine andere Einstellung festgelegt wurde:</span><span class="sxs-lookup"><span data-stu-id="4eced-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone
{
    Param
    (
        [String[]]$NodeName = $env:COMPUTERNAME

    )

    Import-DSCResource -ModuleName xTimeZone


    Node $NodeName
    {
         xTimeZone TimeZoneExample
         {

            TimeZone = 'Eastern Standard Time'
         }

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }

    }
}
```

<span data-ttu-id="4eced-109">Ursache hierfür ist die Funktionsweise der DSC-Ressourcenschlüssel.</span><span class="sxs-lookup"><span data-stu-id="4eced-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="4eced-110">Eine Ressource muss mindestens eine Schlüsseleigenschaft haben.</span><span class="sxs-lookup"><span data-stu-id="4eced-110">A resource must have at least one key property.</span></span> <span data-ttu-id="4eced-111">Eine Ressourceninstanz wird als eindeutig angesehen, wenn die Kombination aus allen ihrer Schlüsseleigenschaften eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="4eced-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="4eced-112">In ihrer vorherigen Implementierung hat die [xTimeZone](https://github.com/PowerShell/xTimeZone)-Ressource nur eine Eigenschaft, **TimeZone**, die ein Schlüssel sein muss.</span><span class="sxs-lookup"><span data-stu-id="4eced-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="4eced-113">Aus diesem Grund würde eine Konfiguration wie die hier gezeigte ohne Warnung kompiliert und ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="4eced-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="4eced-114">Jeder der **xTimeZone**-Ressourcenblöcke wird als eindeutig angesehen.</span><span class="sxs-lookup"><span data-stu-id="4eced-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="4eced-115">Dies würde dazu führen, dass die Konfiguration wiederholt auf den Knoten angewendet wird, wodurch ständig zwischen den Zeitzonen gewechselt würde.</span><span class="sxs-lookup"><span data-stu-id="4eced-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="4eced-116">Um sicherzustellen, dass eine Konfiguration die Zeitzone für einen Zielknoten nur einmal festlegen kann, wurde die Ressource so aktualisiert, dass ihr eine zweite Eigenschaft, **IsSingleInstance**, hinzugefügt wurde, die die Schlüsseleigenschaft geworden ist.</span><span class="sxs-lookup"><span data-stu-id="4eced-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span>
<span data-ttu-id="4eced-117">Der **IsSingleInstance**-Schlüssel wurde mit einem **ValueMap** auf einen einzigen Wert eingeschränkt: „Yes“.</span><span class="sxs-lookup"><span data-stu-id="4eced-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="4eced-118">Das alte MOF-Schema für die Ressource sieht so aus:</span><span class="sxs-lookup"><span data-stu-id="4eced-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="4eced-119">Das aktualisierte MOF-Schema für die Ressource sieht so aus:</span><span class="sxs-lookup"><span data-stu-id="4eced-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="4eced-120">Das Ressourcenskript wurde ebenfalls aktualisiert, damit in ihm der neue Parameter verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4eced-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="4eced-121">Das Ressourcenskript wurde folgendermaßen geändert:</span><span class="sxs-lookup"><span data-stu-id="4eced-121">Here how the resource script was changed:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}

function Set-TargetResource
{
    [CmdletBinding()]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone

    Write-Verbose -Message "Replace the System Time Zone to $TimeZone"
    
    try
    {
        if($CurrentTimeZone -ne $TimeZone)
        {
            Write-Verbose -Verbose "Setting the TimeZone"
            Set-TimeZone -TimeZone $TimeZone
        }
        else
        {
            Write-Verbose -Verbose "TimeZone already set to $TimeZone"
        }
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose -Verbose $ErrorMsg
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="4eced-122">Beachten Sie, dass die **TimeZone**-Eigenschaft kein Schlüssel mehr ist.</span><span class="sxs-lookup"><span data-stu-id="4eced-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="4eced-123">Wenn nun eine Konfiguration versucht, die Zeitzone zweimal festzulegen (durch Verwenden von zwei verschiedenen **xTimeZone**-Blöcken mit verschiedenen **TimeZone**-Werten), wird beim Kompilieren ein Fehler verursacht:</span><span class="sxs-lookup"><span data-stu-id="4eced-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
