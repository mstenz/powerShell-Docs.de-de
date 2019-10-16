---
title: Schreiben eines PowerShell-Skript Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360689"
---
# <a name="how-to-write-a-powershell-script-module"></a>Schreiben eines PowerShell-Skriptmoduls

Ein Skript Modul ist im Grunde ein beliebiges gültiges PowerShell-Skript, das in einer Erweiterung. psm1 gespeichert ist. Mit dieser Erweiterung kann die PowerShell-Engine eine Reihe von Regeln und Cmdlets für Ihre Datei verwenden. Die meisten dieser Funktionen sind verfügbar, damit Sie Ihren Code auf anderen Systemen installieren und die Bereichs Definition verwalten können. Sie können auch eine Modul Manifest-Datei verwenden, die noch komplexere Installationen und Lösungen beschreiben kann.

## <a name="writing-a-powershell-script-module"></a>Schreiben eines PowerShell-Skript Moduls

Sie erstellen ein Skript Modul, indem Sie ein gültiges PowerShell-Skript in einer psm1-Datei speichern und diese Datei dann in einem Verzeichnis speichern, in dem PowerShell Sie finden kann. In diesem Ordner können Sie auch alle Ressourcen platzieren, die Sie zum Ausführen des Skripts benötigen, sowie eine Manifest-Datei, die die Funktionsweise des Moduls in PowerShell beschreibt.

#### <a name="to-create-a-basic-powershell-module"></a>So erstellen Sie ein einfaches PowerShell-Modul

1. Erstellen Sie ein vorhandenes PowerShell-Skript, und speichern Sie das Skript mit der Erweiterung. psm1.

   Das Speichern eines Skripts mit der Erweiterung. psm1 bedeutet, dass Sie die Module-Cmdlets (z. b. [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)) darauf anwenden können. Diese Cmdlets sind hauptsächlich vorhanden, damit Sie Ihren Code problemlos auf die Systeme anderer Benutzer importieren und exportieren können. (Die alternative Lösung besteht darin, den Code auf anderen Systemen zu laden und dann in den aktiven Speicher zu stellen, was keine besonders skalierbare Lösung ist.) Weitere Informationen finden Sie im Abschnitt **Module-Cmdlets und Variablen** in [Windows PowerShell-Modulen](./understanding-a-windows-powershell-module.md) . Beachten Sie, dass standardmäßig alle Funktionen in Ihrem Skript für Benutzer zugänglich sind, die ihre psm1-Datei importieren, die Eigenschaften jedoch nicht.

   Ein PowerShell-Beispielskript mit dem Titel "`Show-Calendar`" ist am Ende dieses Themas verfügbar.

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

2. Um den Benutzer Zugriff auf bestimmte Funktionen oder Eigenschaften zu steuern, nennen Sie [Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) am Ende des Skripts.

   Der Beispielcode unten auf der Seite verfügt nur über eine Funktion, die standardmäßig verfügbar gemacht wird. Es wird jedoch empfohlen, explizit die Funktionen aufzurufen, die Sie verfügbar machen möchten, wie im folgenden Code beschrieben:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Sie können auch einschränken, was mithilfe eines Modul Manifests importiert wird. Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md) und Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](./how-to-write-a-powershell-module-manifest.md).

3. Wenn Sie über Module verfügen, die von Ihrem eigenen Modul geladen werden müssen, können Sie Sie mit einem `Import-Module`-aufzurufenden Befehl am oberen Rand Ihres eigenen Moduls verwenden.

   `Import-Module` ist ein Cmdlet, das ein Ziel Modul auf ein System importiert. Daher wird Sie auch zu einem späteren Zeitpunkt in der Prozedur verwendet, um auch ein eigenes Modul zu installieren. Im Beispielcode unten auf dieser Seite werden keine Import Module verwendet. Wenn dies der Fall ist, werden Sie jedoch am Anfang der Datei aufgelistet, wie im folgenden Code beschrieben:

   ```powershell
   Import-Module GenericModule
   ```

4. Um das Modul im PowerShell-Hilfesystem zu beschreiben, können Sie in der Datei entweder Standard Hilfe Kommentare verwenden oder eine zusätzliche Hilfedatei erstellen.

   Das Codebeispiel am Ende dieses Themas enthält die Hilfe Informationen in den Kommentaren. Sie können auch erweiterte XML-Dateien schreiben, die zusätzlichen Hilfe Inhalt enthalten. Weitere Informationen finden Sie unter [Schreiben der Hilfe für Windows PowerShell-Module](./writing-help-for-windows-powershell-modules.md).

5. Wenn Sie über zusätzliche Module, XML-Dateien oder andere Inhalte verfügen, die Sie mit Ihrem Modul verpacken möchten, können Sie dies mit einem Modul Manifest tun.

   Ein Modul Manifest ist eine Datei, die die Namen anderer Module, Verzeichnis Layouts, Versionsnummern, Autoren Daten und andere Informationen enthält. PowerShell verwendet die Modul Manifest-Datei, um die Projekt Mappe zu organisieren und bereitzustellen. Aufgrund der relativ einfachen Natur dieses Beispiels war eine Manifest-Datei jedoch nicht erforderlich. Weitere Informationen finden Sie unter [Modul Manifeste](./how-to-write-a-powershell-module-manifest.md).

6. Um das Modul zu installieren und auszuführen, speichern Sie das Modul in einem der entsprechenden PowerShell-Pfade, und führen Sie `Import-Module` aus.

   Die Pfade, in denen Sie das Modul installieren können, befinden sich in der globalen Variable `$env:PSModulePath`. Ein allgemeiner Pfad zum Speichern eines Moduls auf einem System wäre beispielsweise `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Stellen Sie sicher, dass Sie einen Ordner erstellen, in dem das Modul vorhanden ist, selbst wenn es sich nur um eine psm1-Datei handelt. Wenn Sie das Modul nicht in einem dieser Pfade gespeichert haben, müssen Sie den Speicherort des Moduls im `Import-Module`-aufrufswert übergeben. (Andernfalls ist PowerShell nicht in der Lage, Sie zu finden.) Ab PowerShell 3,0 müssen Sie das Modul nicht explizit importieren, wenn Sie es in einem der PowerShell-Modul Pfade abgelegt haben. Das Modul wird automatisch geladen, wenn ein Benutzer die Funktion aufruft.
   Weitere Informationen zum Modulpfad finden Sie unter [Importieren eines PowerShell-Moduls und einer](./importing-a-powershell-module.md) [psmodulepath-Umgebungsvariablen](./modifying-the-psmodulepath-installation-path.md).

7. Wenn Sie ein Modul aus dem aktiven Dienst entfernen möchten, führen Sie den Befehl [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module)aus.

   Beachten Sie, dass [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) das Modul aus dem aktiven Speicher entfernt. es löscht es nicht tatsächlich aus dem Speicherort, an dem Sie die Moduldateien gespeichert haben.

### <a name="show-calendar-code-example"></a>Codebeispiel für Anzeige Kalender

Das folgende Beispiel ist ein einfaches Skript Modul, das eine einzelne Funktion mit dem Namen "`Show-Calendar`" enthält.
Diese Funktion zeigt eine visuelle Darstellung eines Kalenders an. Außerdem enthält das Beispiel die PowerShell-Hilfe Zeichenfolgen für Syntax, Beschreibung, Parameterwerte und Beispiel. Beachten Sie, dass die letzte Codezeile sicherstellt, dass die `Show-Calendar`-Funktion als Modulmember exportiert wird, wenn das Modul importiert wird.

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
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
