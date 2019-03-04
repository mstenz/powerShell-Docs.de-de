---
title: 'Gewusst wie: Schreiben Sie ein PowerShell-Skriptmodul | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859006"
---
# <a name="how-to-write-a-powershell-script-module"></a>Schreiben eines PowerShell-Skriptmoduls

Ein Skriptmodul ist im Wesentlichen alle gültigen PowerShell-Skript in einer psm1-Erweiterung gespeichert. Diese Erweiterung ermöglicht die PowerShell-Engine eine Reihe von Regeln und -Cmdlets auf die Datei zu verwenden. Die meisten dieser Funktionen gibt es können Sie Ihren Code sowie das Verwalten der Bereichsdefinition auf anderen Systemen zu installieren. Sie können auch eine modulmanifestdatei, die noch komplexer Installationen und -Lösungen beschreiben können.

## <a name="writing-a-powershell-script-module"></a>Erstellen eines PowerShell-Skript-Moduls

Sie erstellen ein Skriptmodul ein gültigen PowerShell-Skripts in einer psm1-Datei speichern, und klicken Sie dann die Datei speichern, in einem Verzeichnis befinden, in dem Sie PowerShell gefunden werden kann. In diesem Ordner, den Sie auch alle Ressourcen platzieren können, die Sie das Skript ausführen müssen, sowie eine Manifestdatei, die an PowerShell Ihres Moduls wird die Funktionsweise beschrieben.

#### <a name="to-create-a-basic-powershell-module"></a>Erstellen eines grundlegenden PowerShell-Moduls

1. Nehmen Sie ein vorhandenes PowerShell-Skript, und speichern Sie das Skript mit der Erweiterung. psm1.

   Speichern eines Skripts mit den. psm1 Erweiterung bedeutet, dass Sie die Modul-Cmdlets, z. B. können [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), darauf. Diese Cmdlets sind in erster Linie, damit Sie leicht importieren und Exportieren von Ihrem Code auch auf anderen Systemen anderer Benutzer vorhanden. (Die alternative Lösung wäre Sie Ihren Code auf anderen Systemen und klicken Sie dann die Punkt-Quelle in den aktiven Arbeitsspeicher laden, die eine besonders skalierbare Lösung ist.) Weitere Informationen finden Sie unter den **-Modul-Cmdlets und Variablen** im Abschnitt [Windows PowerShell-Module](./understanding-a-windows-powershell-module.md) Beachten Sie, dass standardmäßig alle Funktionen in Ihrem Skript für Benutzer zugegriffen werden können, die Ihre. psm1 importieren Datei, aber die Eigenschaften nicht der Fall ist.

   Ein Beispiel-PowerShell-Skript, Show-Calendar, berechtigt ist am Ende dieses Themas verfügbar.

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. Wenn Sie Benutzerzugriff auf bestimmte Funktionen oder Eigenschaften steuern möchten, rufen Sie [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) am Ende des Skripts.

   Der Beispielcode am unteren Rand der Seite verfügt über nur eine Funktion, die standardmäßig verfügbar gemacht werden sollen. Allerdings empfiehlt es sich, dass Sie explizit die Funktionen, die Sie verfügbar zu machen aufrufen,, wie im folgenden Code beschrieben möchten:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Sie können auch einschränken, was importiert wurde, verwenden ein modulmanifest. Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md) und [Gewusst wie: Schreiben eines Modulmanifests PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Wenn Sie Module, die Ihr eigenes Modul geladen haben haben, können sie mit einem Aufruf von `Import-Module`, am oberen Rand Ihres eigenen Moduls.

   `Import-Module` ist ein Cmdlet, mit denen eine gezielte Modul auf einem System importiert. Daher ist es auch zu einem späteren Zeitpunkt im Verfahren zur auch Ihr eigenes Modul zu installieren. Der Beispielcode am unteren Rand dieser Seite verwendet keine Module importieren. Wenn, jedoch hat würden sie am Anfang der Datei aufgelistet werden, wie im folgenden Code beschrieben:

   ```powershell
   Import-Module GenericModule
   ```

4. Wenn Sie Ihr Modul an das PowerShell-Hilfesystem beschreiben möchten, können Sie entweder die Standardhilfe Kommentare in der Datei oder mit einer zusätzlichen Hilfedatei dafür.

   Das Codebeispiel am Ende dieses Themas enthält die Hilfeinformationen in den Kommentaren. Wenn Sie möchten, könnten Sie auch erweiterte XML-Dateien schreiben, die zusätzliche Hilfe-Inhalt enthalten. Weitere Informationen finden Sie unter [Schreiben von Hilfe für Windows PowerShell-Module](./writing-help-for-windows-powershell-modules.md).

5. Wenn Sie haben zusätzliche Module, XML-Dateien oder andere Inhalte, die Sie mit Ihrem Modul verpacken möchten, können mit einem modulmanifest möchten.

   Ein modulmanifest ist eine Datei, die Namen von anderen Modulen, verzeichnislayouts, versionsverwaltung Zahlen, Autor-Daten und andere Arten von Informationen enthält. PowerShell verwendet der modulmanifestdatei zu organisieren und Ihre Lösung bereitstellen. Aufgrund der relativ einfache Art der in diesem Beispiel werden soll, wurde eine Manifestdatei jedoch nicht erforderlich. Weitere Informationen finden Sie unter [Modul Manifeste](./how-to-write-a-powershell-module-manifest.md).

6. Klicken Sie zum Installieren und Ausführen des Moduls, speichern Sie das Modul auf eine der entsprechenden PowerShell-Pfaden, und rufen Sie `Import-Module`.

   Die Pfade, in dem Sie Ihr Modul installieren können, befinden sich in der `$env:PSModulePath` globale Variable. Z. B. ein gemeinsamen Pfad um ein Modul auf einem System zu speichern wäre `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Achten Sie darauf, dass Sie einen Ordner für Ihr Modul vorhanden, zu erstellen, selbst wenn es nur eine einzelne. psm1-Datei handelt. Wenn Sie Ihr Modul nicht auf einen der folgenden Pfade gespeichert haben, müssen in den Speicherort Ihres Moduls im Aufruf übergeben, um `Import-Module`. (Andernfalls PowerShell nicht finden, es wäre.) Starten mit PowerShell 3.0, wenn Sie Ihr Modul auf einem der Pfade PowerShell-Modul platziert haben, Sie müssen nicht explizit importieren: einfach dadurch, dass einen Benutzer, die Ihre Funktion aufrufen, wird Sie automatisch geladen. Weitere Informationen zu den Modulpfad, finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md) und [PSModulePath-Umgebungsvariable](./modifying-the-psmodulepath-installation-path.md).

7. Stellen Sie zum Entfernen eines Moduls aus dem aktiven Dienst einen Aufruf von [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

Beachten Sie, dass [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) entfernt Ihres Moduls von aktivem Speicher – es werden nicht tatsächlich gelöscht es aus, in dem Sie die Moduldateien gespeichert.

### <a name="show-calendar-code-example"></a>Show-Calendar-Codebeispiel

Im folgende Beispiel wird ein einfaches Skript-Modul, das eine einzelne Funktion, die mit dem Namen Show-Calendar enthält. Diese Funktion zeigt eine visuelle Darstellung eines Kalenders. Darüber hinaus enthält das Beispiel die PowerShell-Hilfe-Zeichenfolgen für die Zusammenfassung, Beschreibung, Parameterwerte und Beispiel. Beachten Sie, dass die letzte Zeile des Codes gibt an, dass die Show-Calendar-Funktion als Mitglied Modul exportiert werden, wenn das Modul importiert wird.

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
