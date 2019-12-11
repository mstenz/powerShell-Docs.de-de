---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEFileCollection-Objekt
ms.openlocfilehash: 96db51ee921cc0fa34803091d563bc6e118643b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030514"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="b322b-103">Das ISEFileCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="b322b-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="b322b-104">Das **ISEFileCollection**-Objekt ist eine Sammlung von **ISEFile**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="b322b-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="b322b-105">Ein Beispiel ist die $psISE.CurrentPowerShellTab.Files-Sammlung.</span><span class="sxs-lookup"><span data-stu-id="b322b-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="b322b-106">Methoden</span><span class="sxs-lookup"><span data-stu-id="b322b-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="b322b-107">Add\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="b322b-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="b322b-108">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b322b-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b322b-109">Erstellt eine neue unbenannte Datei, gibt diese zurück und fügt sie der Sammlung hinzu.</span><span class="sxs-lookup"><span data-stu-id="b322b-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="b322b-110">Die **IsUntitled**-Eigenschaft der neu erstellten Datei ist **$true**.</span><span class="sxs-lookup"><span data-stu-id="b322b-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="b322b-111">**\[fullPath\]** – Optionale Zeichenfolge – der vollständig angegebene Pfad der Datei</span><span class="sxs-lookup"><span data-stu-id="b322b-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="b322b-112">Eine Ausnahme wird erstellt, falls Sie den **fullPath**-Parameter und den relativen Pfad angeben oder falls Sie einen Dateinamen statt dem vollständigen Pfad verwenden.</span><span class="sxs-lookup"><span data-stu-id="b322b-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="b322b-113">Remove\( File, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="b322b-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="b322b-114">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b322b-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b322b-115">Entfernt eine angegebene Datei aus der aktuellen PowerShell-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="b322b-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="b322b-116">**File** – Zeichenfolge – Die ISEFile-Datei, die Sie aus der Sammlung entfernen möchten</span><span class="sxs-lookup"><span data-stu-id="b322b-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="b322b-117">Falls die Datei nicht gespeichert wurde, löst diese Methode eine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="b322b-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="b322b-118">Verwenden Sie den Schalter **Force**, um das Entfernen einer ungespeicherten Datei zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="b322b-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="b322b-119">**\[Force\]** – Optionaler boolescher Wert: Falls er auf **$true** festgelegt wird, erteilt er die Berechtigung dafür, die Datei zu entfernen, auch wenn sie nach der letzten Verwendung nicht gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="b322b-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="b322b-120">Der Standardwert ist **$false**.</span><span class="sxs-lookup"><span data-stu-id="b322b-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="b322b-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="b322b-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="b322b-122">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b322b-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b322b-123">Wählt die Datei aus, die durch den **selectedFile**-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="b322b-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="b322b-124">**selectedFile** – Microsoft.PowerShell.Host.ISE.ISEFile – Die ISEFile-Datei, die Sie auswählen möchten</span><span class="sxs-lookup"><span data-stu-id="b322b-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="b322b-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b322b-125">See Also</span></span>

- [<span data-ttu-id="b322b-126">Das ISEFile-Objekt</span><span class="sxs-lookup"><span data-stu-id="b322b-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="b322b-127">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="b322b-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b322b-128">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="b322b-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
