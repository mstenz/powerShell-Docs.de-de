---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Schreiben einer Einzelinstanz-DSC-Ressource (empfohlen)
ms.openlocfilehash: 4d9e07c6aaa064f808a03d4252e8d352b82183ec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952817"
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a>Schreiben einer Einzelinstanz-DSC-Ressource (empfohlen)

>**Hinweis:** In diesem Thema wird ein bewährtes Verfahren zum Definieren einer DSC-Ressource beschrieben, die nur eine einzige Instanz in einer Konfiguration zulässt. Derzeit gibt es hierfür keine integrierte DSC-Funktion. Dies kann sich zukünftig ändern.

Es gibt Situationen, in denen Sie für eine Ressource nicht zulassen möchten, dass sie mehrmals in einer Konfiguration verwendet wird. Beispielsweise konnte in einer früheren Implementierung der [xTimeZone](https://github.com/PowerShell/xTimeZone)-Ressource eine Konfiguration die Ressource mehrmals aufrufen, wodurch die Zeitzone in jedem Ressourcenblock auf eine andere Einstellung festgelegt wurde:

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

Ursache hierfür ist die Funktionsweise der DSC-Ressourcenschlüssel. Eine Ressource muss mindestens eine Schlüsseleigenschaft haben. Eine Ressourceninstanz wird als eindeutig angesehen, wenn die Kombination aus allen ihrer Schlüsseleigenschaften eindeutig ist. In ihrer vorherigen Implementierung hat die [xTimeZone](https://github.com/PowerShell/xTimeZone)-Ressource nur eine Eigenschaft, **TimeZone**, die ein Schlüssel sein muss. Aus diesem Grund würde eine Konfiguration wie die hier gezeigte ohne Warnung kompiliert und ausgeführt. Jeder der **xTimeZone**-Ressourcenblöcke wird als eindeutig angesehen. Dies würde dazu führen, dass die Konfiguration wiederholt auf den Knoten angewendet wird, wodurch ständig zwischen den Zeitzonen gewechselt würde.

Um sicherzustellen, dass eine Konfiguration die Zeitzone für einen Zielknoten nur einmal festlegen kann, wurde die Ressource so aktualisiert, dass ihr eine zweite Eigenschaft, **IsSingleInstance**, hinzugefügt wurde, die die Schlüsseleigenschaft geworden ist.
Der **IsSingleInstance**-Schlüssel wurde mit einem **ValueMap** auf einen einzigen Wert eingeschränkt: „Yes“. Das alte MOF-Schema für die Ressource sieht so aus:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Das aktualisierte MOF-Schema für die Ressource sieht so aus:

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

Das Ressourcenskript wurde ebenfalls aktualisiert, damit in ihm der neue Parameter verwendet wird. Das Ressourcenskript wurde folgendermaßen geändert:

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

Beachten Sie, dass die **TimeZone**-Eigenschaft kein Schlüssel mehr ist. Wenn nun eine Konfiguration versucht, die Zeitzone zweimal festzulegen (durch Verwenden von zwei verschiedenen **xTimeZone**-Blöcken mit verschiedenen **TimeZone**-Werten), wird beim Kompilieren ein Fehler verursacht:

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
