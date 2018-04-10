---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Schreiben von Hilfe für DSC-Konfigurationen
ms.openlocfilehash: c80c5c9007f0094396edf7bd11780495a90950ec
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="b58b6-103">Schreiben von Hilfe für DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="b58b6-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="b58b6-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b58b6-104">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="b58b6-105">Sie können die kommentarbasierte Hilfe in DSC-Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="b58b6-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="b58b6-106">Benutzer können auf die Hilfe zugreifen, entweder durch Aufrufen der Konfigurationsfunktion mit `-?` oder mithilfe des Cmdlets [Get-Help](https://technet.microsoft.com/library/hh849696.aspx).</span><span class="sxs-lookup"><span data-stu-id="b58b6-106">Users can access the help by calling the configuration function with `-?`, or by using the [Get-Help](https://technet.microsoft.com/library/hh849696.aspx) cmdlet.</span></span> <span data-ttu-id="b58b6-107">Weitere Informationen zur kommentarbasierten Hilfe für PowerShell finden Sie unter [about_Comment_Based_Help](https://technet.microsoft.com/library/hh847834.aspx).</span><span class="sxs-lookup"><span data-stu-id="b58b6-107">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](https://technet.microsoft.com/library/hh847834.aspx).</span></span>

<span data-ttu-id="b58b6-108">Das folgende Beispiel zeigt ein Skript, das eine Konfiguration und kommentarbasierte Hilfe dafür enthält:</span><span class="sxs-lookup"><span data-stu-id="b58b6-108">The following example shows a script that contains a configuration and comment-based help for it:</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.PARAMETER FilePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$ComputerName,[string]$FilePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="b58b6-109">Anzeigen von Hilfe zur Konfiguration</span><span class="sxs-lookup"><span data-stu-id="b58b6-109">Viewing configuration help</span></span>

<span data-ttu-id="b58b6-110">Verwenden Sie zum Anzeigen der Hilfe für eine Konfiguration das Cmdlet **Get-Help** mit dem Namen der Funktion, oder geben der Namen der Funktion gefolgt von `-?` ein.</span><span class="sxs-lookup"><span data-stu-id="b58b6-110">To view the help for a configuration, use the **Get-Help** cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="b58b6-111">Folgendes ist die Ausgabe der vorherigen Funktion bei Übergabe an **Get-Help**:</span><span class="sxs-lookup"><span data-stu-id="b58b6-111">The following is the output of the previous function when passed to **Get-Help**:</span></span>

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName]
    <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## <a name="see-also"></a><span data-ttu-id="b58b6-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b58b6-112">See Also</span></span>
* [<span data-ttu-id="b58b6-113">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="b58b6-113">DSC Configurations</span></span>](configurations.md)