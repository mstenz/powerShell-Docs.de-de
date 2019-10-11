---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Schreiben von Hilfe für DSC-Konfigurationen
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954137"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="58e74-103">Schreiben von Hilfe für DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="58e74-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="58e74-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="58e74-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="58e74-105">Sie können die kommentarbasierte Hilfe in DSC-Konfigurationen verwenden.</span><span class="sxs-lookup"><span data-stu-id="58e74-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="58e74-106">Benutzer können auf die Hilfe zugreifen, entweder durch Aufrufen der **Konfiguration** mit `-?` oder mithilfe des Cmdlets [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="58e74-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="58e74-107">Platzieren Sie Ihre kommentarbasierte Hilfe direkt oberhalb des `Configuration`-Schlüsselworts.</span><span class="sxs-lookup"><span data-stu-id="58e74-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="58e74-108">Sie können die Parameterhilfe parallel zu Ihrem Kommentarblock, direkt über der Parameterdeklaration oder an beiden Positionen wie im folgenden Beispiel gezeigt platzieren.</span><span class="sxs-lookup"><span data-stu-id="58e74-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="58e74-109">Weitere Informationen zur kommentarbasierten Hilfe für PowerShell finden Sie unter [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="58e74-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="58e74-110">PowerShell-Entwicklungsumgebungen wie VSCode und die ISE verfügen auch über Codeausschnitte, mit denen Sie automatisch Kommentarblockvorlagen einfügen können.</span><span class="sxs-lookup"><span data-stu-id="58e74-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="58e74-111">Das folgende Beispiel zeigt ein Skript, das eine Konfiguration und kommentarbasierte Hilfe dafür enthält.</span><span class="sxs-lookup"><span data-stu-id="58e74-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="58e74-112">Dieses Beispiel zeigt eine Konfiguration mit Parametern.</span><span class="sxs-lookup"><span data-stu-id="58e74-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="58e74-113">Weitere Informationen zum Verwenden von Parametern in Ihrer Konfigurationen finden Sie unter [Hinzufügen von Parametern zu Ihren Konfigurationen](add-parameters-to-a-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="58e74-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

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

## <a name="viewing-configuration-help"></a><span data-ttu-id="58e74-114">Anzeigen von Hilfe zur Konfiguration</span><span class="sxs-lookup"><span data-stu-id="58e74-114">Viewing configuration help</span></span>

<span data-ttu-id="58e74-115">Verwenden Sie zum Anzeigen der Hilfe für eine Konfiguration das Cmdlet `Get-Help` mit dem Namen der Funktion, oder geben der Namen der Funktion gefolgt von `-?` ein.</span><span class="sxs-lookup"><span data-stu-id="58e74-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="58e74-116">Im Folgenden sehen Sie die Ausgabe der vorherigen Konfiguration, die an `Get-Help` übergeben wurde.</span><span class="sxs-lookup"><span data-stu-id="58e74-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

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
> <span data-ttu-id="58e74-117">Syntaxfelder und Parameterattribute werden von PowerShell automatisch für Sie generiert.</span><span class="sxs-lookup"><span data-stu-id="58e74-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="58e74-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="58e74-118">See Also</span></span>

- [<span data-ttu-id="58e74-119">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="58e74-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="58e74-120">Schreiben, Kompilieren und Anwenden einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="58e74-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="58e74-121">Hinzufügen von Parametern zu einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="58e74-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
