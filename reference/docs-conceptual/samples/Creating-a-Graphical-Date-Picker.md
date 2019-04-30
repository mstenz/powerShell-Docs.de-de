---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Erstellen einer grafischen Datumsauswahl
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058606"
---
# <a name="creating-a-graphical-date-picker"></a>Erstellen einer grafischen Datumsauswahl

Verwenden Sie Windows PowerShell 3.0 und neuere Versionen, um ein Formular mit einem grafischen Kalendersteuerelement zu erstellen, mit dem Benutzer einen Tag des Monats auswählen können.

## <a name="create-a-graphical-date-picker-control"></a>Erstellen eines grafischen Steuerelements für die Datumsauswahl

Kopieren und fügen Sie Folgendes in Windows PowerShell ISE ein, und speichern Sie es als Windows PowerShell-Skript (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Das Skript beginnt mit dem Laden von zwei .NET Framework-Klassen: **System.Drawing** und **System.Windows.Forms.**
Sie starten dann eine neue Instanz der .NET Framework-Klasse **Windows.Forms.Form**. Diese stellt ein leeres Formular oder Fenster bereit, in das Sie Steuerelemente einfügen können.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

Dieses Beispiel weist vier Eigenschaften dieser Klasse Werte zu, indem es die Eigenschaft **Property** und die Hashtabelle verwendet.

1. **StartPosition**: Wenn Sie diese Eigenschaft nicht hinzufügen, wählt Windows eine Stelle aus, wenn das Formular geöffnet wird.
   Durch Festlegen dieser Eigenschaft auf **CenterScreen** wird das Formular automatisch bei jedem Laden in der Mitte des Bildschirms angezeigt.

2. **Size**: Dies ist die Größe des Formulars, in Pixeln.
   Dieses Skript erstellt ein Formular, das 243 Pixel breit und 230 Pixel hoch ist.

3. **Text**: Dies wird der Titel des Fensters.

4. **Topmost**: Durch das Festlegen dieser Eigenschaft auf `$true` können Sie erzwingen, dass das Fenster über anderen geöffneten Fenstern und Dialogfeldern geöffnet wird.

Als Nächstes erstellen Sie in Ihrem Formular ein Kalendersteuerelement.
In diesem Beispiel wird der aktuelle Tag nicht hervorgehoben oder markiert.
Benutzer können immer nur einen Tag im Kalender auswählen.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

Als Nächstes erstellen Sie eine Schaltfläche **OK** für Ihr Formular.
Legen Sie die Größe und das Verhalten der Schaltfläche **OK** fest.
In diesem Beispiel wird als Position der Schaltfläche 165 Pixel vom oberen Rand des Formulars und 38 Pixel vom linken Rand entfernt festgelegt.
Die Schaltflächenhöhe beträgt 23 Pixel und die Schaltflächenlänge 75 Pixel.
Das Skript verwendet vordefinierte Windows-Formulartypen zur Bestimmung des Schaltflächenverhaltens.

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

In entsprechender Weise erstellen Sie eine Schaltfläche **Abbrechen**.
Die Position der Schaltfläche **Abbrechen** ist 165 Pixel vom oberen Rand und 113 Pixel vom linken Rand des Fensters entfernt.

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Fügen Sie die folgende Codezeile hinzu, um das Formular in Windows anzuzeigen.

```powershell
$result = $form.ShowDialog()
```

Abschließend weist der Code im Block `if` Windows an, was mit dem Formular geschehen soll, wenn Benutzer einen Tag im Kalender auswählen und anschließend auf die Schaltfläche **OK** klicken oder die **EINGABETASTE** drücken.
Windows PowerShell zeigt den Benutzern das ausgewählte Datum an.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Weitere Informationen

- [Hey Scripting Guy:  Warum funktionieren diese PowerShell GUI-Beispiele nicht?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt's WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell – Tipp der Woche:  Erstellen einer grafischen Datumsauswahl](https://technet.microsoft.com/library/ff730942.aspx)