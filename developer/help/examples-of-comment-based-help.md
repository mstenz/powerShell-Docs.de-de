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
ms.openlocfilehash: dbccaf5b8e48a1c4d924bc0ec4ea09b25e10adf0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857966"
---
# <a name="examples-of-comment-based-help"></a>Beispiele für die kommentarbasierte Hilfe

Dieses Thema enthält Beispiel für die kommentarbasierte Hilfe für Skripts und Funktionen veranschaulichen.

## <a name="example-1-comment-based-help-for-a-function"></a>Beispiel 1: Kommentarbasierte Hilfe für eine Funktion

 Die folgende Beispielfunktion enthält kommentarbasierte Hilfe.

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

Die folgende Ausgabe zeigt die Ergebnisse eines Get-Help-Befehls, der zeigt die Hilfe für die Erweiterung der hinzufügen-Funktion.

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

## <a name="example-2-comment-based-help-for-a-script"></a>Beispiel 2: Kommentarbasierte Hilfe für ein Skript

Die folgende Beispielfunktion enthält kommentarbasierte Hilfe.

Beachten Sie, dass die Leerzeilen zwischen dem schließenden **#>** und `Param` Anweisung. In einem Skript, die keinem `Param` -Anweisung, zwischen der letzten Kommentar im Hilfethema und der ersten Deklaration muss über mindestens zwei leere Zeilen vorhanden sein. Ohne diese leeren Zeilen wurde die Funktion, statt das Skript Get-Help das Hilfethema zugeordnet.

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

Der folgende Befehl ruft das Skript Hilfe ab. Da das Skript nicht n ist muss ein Verzeichnis, das in der Path-Umgebungsvariablen, die Get-Help-Befehl aufgeführt ist, das die Hilfe-Skript zum Abrufen den Skriptpfad angeben.

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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a>Beispiel 3: Beschreibungen der Parameter in einer Parameter-Anweisung

Dieses Beispiel zeigt, wie einzufügende Parameterdescriptions in die `Param` Anweisung einer Funktion oder ein Skript. Dieses Format ist besonders hilfreich, wenn die parameterbeschreibungen kurz sind.

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

Die Ergebnisse sind identisch, wie die Ergebnisse z. B. 1. Get-Help die parameterbeschreibungen interpretiert, als wären sie zusammen mit wurden die `.Parameter` Schlüsselwort.

## <a name="example-4--redirecting-to-an-xml-file"></a>Beispiel 4:  Umleitung an eine XML-Datei

Sie können XML-Hilfethemen für Funktionen und Skripts schreiben. Obwohl kommentarbasierte Hilfe einfacher zu implementieren ist, ist XML-basierte Hilfe erforderlich, ggf. eine genauere Steuerung der Hilfe-Inhalt, oder wenn Sie Hilfethemen in mehrere Sprachen übersetzen. Das folgende Beispiel zeigt die ersten Zeilen des Update-Month.ps1 Skripts. Das Skript verwendet die `.ExternalHelp` Schlüsselwort, um den Pfad zu einem XML-basierte Hilfethema für das Skript angeben.

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

Das folgende Beispiel zeigt die Verwendung der `.ExternalHelp` Schlüsselwort in einer Funktion.

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a>Beispiel 5:  Umleitung zu einem anderen Hilfethema

Der folgende Code ist ein Auszug aus den Anfang der integrierten `Help` -Funktion in Windows PowerShell, die jeweils ein Bildschirm mit den Hilfetext zu einem Zeitpunkt anzeigt. Da das Hilfethema für das Cmdlet "Get-Help" wird, die Help-Funktion beschrieben, die Help-Funktion verwendet die `.ForwardHelpTargetName` und `.ForwardHelpCategory` Schlüsselwörter zum Umleiten des Benutzers mit dem Get-Help Cmdlet-Hilfethema.

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

Der folgende Befehl verwendet diese Funktion. Wenn ein Benutzer einen Get-Help-Befehl für die Hilfe-Funktion eingibt, zeigt Get-Help das Hilfethema für das Cmdlet "Get-Help".

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