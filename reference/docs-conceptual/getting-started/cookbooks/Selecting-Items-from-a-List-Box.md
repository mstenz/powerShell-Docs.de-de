---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Auswählen von Elementen aus einem Listenfeld
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: 6ff6bff8f6ce4e9236d7877c4cca24a10932cbe0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951680"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="ef9bf-103">Auswählen von Elementen aus einem Listenfeld</span><span class="sxs-lookup"><span data-stu-id="ef9bf-103">Selecting Items from a List Box</span></span>

<span data-ttu-id="ef9bf-104">Verwenden Sie Windows PowerShell 3.0 und spätere Versionen zur Erstellung eines Dialogfelds, in dem Benutzer Elemente aus einem Listenfeld-Steuerelement auswählen können.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="ef9bf-105">Erstellen Sie ein Listenfeld-Steuerelement, und wählen Sie Elemente daraus aus</span><span class="sxs-lookup"><span data-stu-id="ef9bf-105">Create a list box control, and select items from it</span></span>

<span data-ttu-id="ef9bf-106">Kopieren und fügen Sie Folgendes in Windows PowerShell ISE ein, und speichern Sie es als Windows PowerShell-Skript (.ps1).</span><span class="sxs-lookup"><span data-stu-id="ef9bf-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="ef9bf-107">Das Skript beginnt mit dem Laden von zwei .NET Framework-Klassen: **System.Drawing** und **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="ef9bf-108">Sie starten daraufhin eine neue Instanz der .NET Framework-Klasse **System.Windows.Forms.Form**, die ein leeres Formular oder Fenster bereitstellt, zu dem Sie Steuerelemente hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="ef9bf-109">Nachdem Sie eine Instanz der Formularklasse erstellt haben, ordnen Sie drei Eigenschaften dieser Klasse Werte zu.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="ef9bf-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="ef9bf-110">**Text.**</span></span> <span data-ttu-id="ef9bf-111">Dies wird der Titel des Fensters.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="ef9bf-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="ef9bf-112">**Size.**</span></span> <span data-ttu-id="ef9bf-113">Dies ist die Größe des Formulars, in Pixeln.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="ef9bf-114">Das vorhergehende Skript erstellt ein Formular, das 300 Pixel breit und 200 Pixel hoch ist.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="ef9bf-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="ef9bf-115">**StartingPosition.**</span></span> <span data-ttu-id="ef9bf-116">Für diese optionale Eigenschaft ist im Skript oben **CenterScreen** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="ef9bf-117">Wenn Sie diese Eigenschaft nicht hinzufügen, wählt Windows eine Stelle aus, wenn das Formular geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="ef9bf-118">Durch Festlegen der **StartingPosition** auf **CenterScreen** wird das Formular automatisch bei jedem Laden in der Mitte des Bildschirms angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="ef9bf-119">Als Nächstes erstellen Sie eine Schaltfläche **OK** für Ihr Formular.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="ef9bf-120">Legen Sie die Größe und das Verhalten der Schaltfläche **OK** fest.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="ef9bf-121">In diesem Beispiel befindet sich die Schaltfläche 120 Pixel vom oberen Formularrand und 75 Pixel vom linken Rand entfernt.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="ef9bf-122">Die Schaltflächenhöhe beträgt 23 Pixel und die Schaltflächenlänge 75 Pixel.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="ef9bf-123">Das Skript verwendet vordefinierte Windows-Formulartypen zur Bestimmung des Schaltflächenverhaltens.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="ef9bf-124">In entsprechender Weise erstellen Sie eine Schaltfläche **Abbrechen**.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="ef9bf-125">Die **Abbrechen**-Schaltfläche ist 120 Pixel vom oberen und 150 Pixel vom linken Rand des Fensters entfernt.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="ef9bf-126">Als nächstes stellen Sie einen Beschriftungstext in Ihrem Fenster bereit, der die Information beschreibt, die Benutzer verwenden sollen.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="ef9bf-127">In diesem Fall sollen die Benutzer einen Computer auswählen.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-127">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="ef9bf-128">Fügen Sie das Steuerelement (in diesem Fall ein Listenfeld) hinzu, mit dem Benutzer die Informationen bereitstellen, die Sie in Ihrem Beschriftungstext beschrieben haben.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="ef9bf-129">Es gibt viele weitere Steuerelemente, die Sie neben Listenfeldern anwenden können. Weitere Steuerelemente finden Sie unter [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) auf MSDN.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="ef9bf-130">Im nächsten Abschnitt legen Sie die Werte fest, die im Listenfeld für Benutzer angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="ef9bf-131">Das von diesem Skript erstellte Listenfeld erlaubt nur eine Auswahl.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="ef9bf-132">Zur Erstellung eines Listenfeld-Steuerelements für eine Mehrfachauswahl legen Sie einen Wert für die **SelectionMode**-Eigenschaft fest, wie hier beschrieben: `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="ef9bf-133">Weitere Informationen finden Sie unter [Mehrfachauswahl-Listenfelder](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="ef9bf-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="ef9bf-134">Fügen Sie das Listenfeld-Steuerelement zu Ihrem Formular hinzu, um Windows anzuweisen, das Formular beim Öffnen über anderen Fenstern und Dialogfeldern zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="ef9bf-135">Fügen Sie die folgende Codezeile hinzu, um das Formular in Windows anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-135">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="ef9bf-136">Abschließend weist der Code im Block **If** Windows an, was mit dem Formular geschehen soll, wenn Benutzer eine Option aus dem Listenfeld auswählen und anschließend auf die Schaltfläche **OK** klicken oder die **EINGABETASTE** drücken.</span><span class="sxs-lookup"><span data-stu-id="ef9bf-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="ef9bf-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ef9bf-137">See Also</span></span>

- [<span data-ttu-id="ef9bf-138">Hey Scripting Guy: Warum funktionieren diese PowerShell GUI-Beispiele nicht?</span><span class="sxs-lookup"><span data-stu-id="ef9bf-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="ef9bf-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="ef9bf-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="ef9bf-140">Windows PowerShell-Tipp der Woche: Auswählen von Elementen aus einem Listenfeld</span><span class="sxs-lookup"><span data-stu-id="ef9bf-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](http://technet.microsoft.com/library/ff730949.aspx)