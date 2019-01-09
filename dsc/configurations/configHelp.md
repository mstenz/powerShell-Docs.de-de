---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Schreiben von Hilfe für DSC-Konfigurationen
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401682"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="33a02-103">Schreiben von Hilfe für DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="33a02-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="33a02-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="33a02-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="33a02-105">Sie können die kommentarbasierte Hilfe in DSC-Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="33a02-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="33a02-106">Benutzer können auf die Hilfe zugreifen, durch den Aufruf der **Konfiguration** mit `-?`, oder mithilfe der [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="33a02-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="33a02-107">Platzieren Sie Ihre kommentarbasierte Hilfe direkt oberhalb der `Configuration` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="33a02-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="33a02-108">Sie können Parameter Hilfe inline mit Ihrem Kommentarblock, direkt über die Parameterdeklaration oder beides wie im folgenden Beispiel platzieren.</span><span class="sxs-lookup"><span data-stu-id="33a02-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="33a02-109">Weitere Informationen zur kommentarbasierten Hilfe für PowerShell finden Sie unter [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="33a02-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="33a02-110">PowerShell-entwicklungsumgebungen, wie VSCode und der ISE haben auch die Ausschnitte, sodass Sie automatisch Vorlagen von Kommentar-Block einfügen können.</span><span class="sxs-lookup"><span data-stu-id="33a02-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="33a02-111">Das folgende Beispiel zeigt ein Skript, das eine Konfiguration und kommentarbasierte Hilfe dafür enthält.</span><span class="sxs-lookup"><span data-stu-id="33a02-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="33a02-112">Dieses Beispiel zeigt eine Konfiguration mit Parametern.</span><span class="sxs-lookup"><span data-stu-id="33a02-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="33a02-113">Weitere Informationen zum Verwenden von Parametern in Ihrer Konfigurationen finden Sie unter [Parameter hinzufügen, um Ihre Konfigurationen](add-parameters-to-a-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="33a02-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

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

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="33a02-114">Anzeigen von Hilfe zur Konfiguration</span><span class="sxs-lookup"><span data-stu-id="33a02-114">Viewing configuration help</span></span>

<span data-ttu-id="33a02-115">Verwenden Sie zum Anzeigen der Hilfe für die Konfiguration der `Get-Help` Cmdlet mit dem Namen der Funktion, oder geben den Namen der Funktion folgt `-?`.</span><span class="sxs-lookup"><span data-stu-id="33a02-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="33a02-116">Im folgenden wird die Ausgabe der vorherigen Konfiguration, die an `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="33a02-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="33a02-117">Felder von Syntax und Parameterattribute werden von PowerShell automatisch für Sie generiert.</span><span class="sxs-lookup"><span data-stu-id="33a02-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="33a02-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="33a02-118">See Also</span></span>

- [<span data-ttu-id="33a02-119">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="33a02-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="33a02-120">Schreiben, Kompilieren und Anwenden einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="33a02-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="33a02-121">Hinzufügen von Parametern zu einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="33a02-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
