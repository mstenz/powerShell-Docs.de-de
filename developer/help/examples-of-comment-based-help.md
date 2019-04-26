---
title: Beispiele für die Kommentarbasierte Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: 30e98bfcf06b1720005a73ee8294aeba7e1ae066
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083500"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="cdcec-102">Beispiele für die kommentarbasierte Hilfe</span><span class="sxs-lookup"><span data-stu-id="cdcec-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="cdcec-103">Dieses Thema enthält Beispiel für die kommentarbasierte Hilfe für Skripts und Funktionen veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="cdcec-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="cdcec-104">Beispiel 1: Kommentarbasierte Hilfe für eine Funktion</span><span class="sxs-lookup"><span data-stu-id="cdcec-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="cdcec-105">Die folgende Beispielfunktion enthält kommentarbasierte Hilfe.</span><span class="sxs-lookup"><span data-stu-id="cdcec-105">The following sample function includes comment-based Help.</span></span>

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="cdcec-106">Die folgende Ausgabe zeigt die Ergebnisse eines Get-Help-Befehls, der zeigt die Hilfe für die Erweiterung der hinzufügen-Funktion.</span><span class="sxs-lookup"><span data-stu-id="cdcec-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="cdcec-107">Beispiel 2: Kommentarbasierte Hilfe für ein Skript</span><span class="sxs-lookup"><span data-stu-id="cdcec-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="cdcec-108">Die folgende Beispielfunktion enthält kommentarbasierte Hilfe.</span><span class="sxs-lookup"><span data-stu-id="cdcec-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="cdcec-109">Beachten Sie, dass die Leerzeilen zwischen dem schließenden **#>** und `Param` Anweisung.</span><span class="sxs-lookup"><span data-stu-id="cdcec-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="cdcec-110">In einem Skript, die keinem `Param` -Anweisung, zwischen der letzten Kommentar im Hilfethema und der ersten Deklaration muss über mindestens zwei leere Zeilen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="cdcec-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="cdcec-111">Ohne diese leeren Zeilen wurde die Funktion, statt das Skript Get-Help das Hilfethema zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="cdcec-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="cdcec-112">Der folgende Befehl ruft das Skript Hilfe ab.</span><span class="sxs-lookup"><span data-stu-id="cdcec-112">The following command gets the script Help.</span></span> <span data-ttu-id="cdcec-113">Da das Skript nicht n ist muss ein Verzeichnis, das in der Path-Umgebungsvariablen, die Get-Help-Befehl aufgeführt ist, das die Hilfe-Skript zum Abrufen den Skriptpfad angeben.</span><span class="sxs-lookup"><span data-stu-id="cdcec-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="cdcec-114">Beispiel 3: Beschreibungen der Parameter in einer Parameter-Anweisung</span><span class="sxs-lookup"><span data-stu-id="cdcec-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="cdcec-115">Dieses Beispiel zeigt, wie einzufügende Parameterdescriptions in die `Param` Anweisung einer Funktion oder ein Skript.</span><span class="sxs-lookup"><span data-stu-id="cdcec-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="cdcec-116">Dieses Format ist besonders hilfreich, wenn die parameterbeschreibungen kurz sind.</span><span class="sxs-lookup"><span data-stu-id="cdcec-116">This format is most useful when the parameter descriptions are brief.</span></span>

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

<span data-ttu-id="cdcec-117">Die Ergebnisse sind identisch, wie die Ergebnisse z. B. 1.</span><span class="sxs-lookup"><span data-stu-id="cdcec-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="cdcec-118">Get-Help die parameterbeschreibungen interpretiert, als wären sie zusammen mit wurden die `.Parameter` Schlüsselwort.</span><span class="sxs-lookup"><span data-stu-id="cdcec-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="cdcec-119">Beispiel 4:  Umleitung an eine XML-Datei</span><span class="sxs-lookup"><span data-stu-id="cdcec-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="cdcec-120">Sie können XML-Hilfethemen für Funktionen und Skripts schreiben.</span><span class="sxs-lookup"><span data-stu-id="cdcec-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="cdcec-121">Obwohl kommentarbasierte Hilfe einfacher zu implementieren ist, ist XML-basierte Hilfe erforderlich, ggf. eine genauere Steuerung der Hilfe-Inhalt, oder wenn Sie Hilfethemen in mehrere Sprachen übersetzen. Das folgende Beispiel zeigt die ersten Zeilen des Update-Month.ps1 Skripts.</span><span class="sxs-lookup"><span data-stu-id="cdcec-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="cdcec-122">Das Skript verwendet die `.ExternalHelp` Schlüsselwort, um den Pfad zu einem XML-basierte Hilfethema für das Skript angeben.</span><span class="sxs-lookup"><span data-stu-id="cdcec-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="cdcec-123">Das folgende Beispiel zeigt die Verwendung der `.ExternalHelp` Schlüsselwort in einer Funktion.</span><span class="sxs-lookup"><span data-stu-id="cdcec-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="cdcec-124">Beispiel 5:  Umleitung zu einem anderen Hilfethema</span><span class="sxs-lookup"><span data-stu-id="cdcec-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="cdcec-125">Der folgende Code ist ein Auszug aus den Anfang der integrierten `Help` -Funktion in Windows PowerShell, die jeweils ein Bildschirm mit den Hilfetext zu einem Zeitpunkt anzeigt.</span><span class="sxs-lookup"><span data-stu-id="cdcec-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="cdcec-126">Da das Hilfethema für das Cmdlet "Get-Help" wird, die Help-Funktion beschrieben, die Help-Funktion verwendet die `.ForwardHelpTargetName` und `.ForwardHelpCategory` Schlüsselwörter zum Umleiten des Benutzers mit dem Get-Help Cmdlet-Hilfethema.</span><span class="sxs-lookup"><span data-stu-id="cdcec-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

<span data-ttu-id="cdcec-127">Der folgende Befehl verwendet diese Funktion.</span><span class="sxs-lookup"><span data-stu-id="cdcec-127">The following command uses this feature.</span></span> <span data-ttu-id="cdcec-128">Wenn ein Benutzer einen Get-Help-Befehl für die Hilfe-Funktion eingibt, zeigt Get-Help das Hilfethema für das Cmdlet "Get-Help".</span><span class="sxs-lookup"><span data-stu-id="cdcec-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```