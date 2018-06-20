---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEFile-Objekt
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 276e8f04a827e18999b5b3ecb08f47de4f4b23b1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951391"
---
# <a name="the-isefile-object"></a><span data-ttu-id="b0df2-103">Das ISEFile-Objekt</span><span class="sxs-lookup"><span data-stu-id="b0df2-103">The ISEFile Object</span></span>

<span data-ttu-id="b0df2-104">Ein **ISEFile**-Objekt stellt eine Datei in Windows-PowerShell® Integrated Scripting Environment (ISE) dar</span><span class="sxs-lookup"><span data-stu-id="b0df2-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="b0df2-105">Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEFile-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b0df2-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="b0df2-106">In diesem Thema werden die Elementmethoden und -eigenschaften aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="b0df2-107">**$psISE.CurrentFile** und die Dateien in der DateiSammlung auf einer PowerShell-Registerkarte sind Instanzen der Microsoft.PowerShell.Host.ISE.ISEFile-Klasse.</span><span class="sxs-lookup"><span data-stu-id="b0df2-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="b0df2-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="b0df2-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="b0df2-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="b0df2-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="b0df2-110">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0df2-111">Speichert die Datei auf dem Datenträger.</span><span class="sxs-lookup"><span data-stu-id="b0df2-111">Saves the file to disk.</span></span>

<span data-ttu-id="b0df2-112">**\[saveEncoding\]** – Optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b0df2-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="b0df2-113">Der Standardwert lautet **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="b0df2-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="b0df2-114">Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="b0df2-114">Exceptions</span></span>

- <span data-ttu-id="b0df2-115">**System.IO.IOException**: Die Datei konnte nicht gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b0df2-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="b0df2-116">SaveAs\(Dateiname, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="b0df2-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="b0df2-117">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0df2-118">Speichert die Datei mit dem angegebenen Namen und der angegebenen Codierung.</span><span class="sxs-lookup"><span data-stu-id="b0df2-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="b0df2-119">**Dateiname**: Zeichenfolge – der Name, der zum Speichern der Datei verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b0df2-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="b0df2-120">**\[saveEncoding\]** – Optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b0df2-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="b0df2-121">Der Standardwert lautet **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="b0df2-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="b0df2-122">Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="b0df2-122">Exceptions</span></span>

- <span data-ttu-id="b0df2-123">**System.ArgumentNullException**: Der **filename**-Parameter ist NULL.</span><span class="sxs-lookup"><span data-stu-id="b0df2-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="b0df2-124">**System.ArgumentException**: Der **filename**-Parameter ist leer.</span><span class="sxs-lookup"><span data-stu-id="b0df2-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="b0df2-125">**System.IO.IOException**: Die Datei konnte nicht gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b0df2-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="b0df2-126">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="b0df2-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="b0df2-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b0df2-127">DisplayName</span></span>

<span data-ttu-id="b0df2-128">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0df2-129">Die schreibgeschützte Eigenschaft, die die Zeichenfolge mit dem Anzeigenamen dieser Datei abruft.</span><span class="sxs-lookup"><span data-stu-id="b0df2-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="b0df2-130">Der Name wird auf der Registerkarte **Datei** oben im Editor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="b0df2-131">Ein Sternchen \(\*\) am Ende des Namens zeigt an, dass die Datei nicht gespeicherte Änderungen enthält.</span><span class="sxs-lookup"><span data-stu-id="b0df2-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="b0df2-132">Editor</span><span class="sxs-lookup"><span data-stu-id="b0df2-132">Editor</span></span>

<span data-ttu-id="b0df2-133">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0df2-134">Die schreibgeschützte Eigenschaft, die das für die angegebene Datei verwendete [Editor-Objekt](The-ISEEditor-Object.md) abruft.</span><span class="sxs-lookup"><span data-stu-id="b0df2-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="b0df2-135">Codierung</span><span class="sxs-lookup"><span data-stu-id="b0df2-135">Encoding</span></span>

<span data-ttu-id="b0df2-136">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0df2-137">Die schreibgeschützte Eigenschaft, die die ursprüngliche Dateicodierung abruft.</span><span class="sxs-lookup"><span data-stu-id="b0df2-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="b0df2-138">Dies ist ein **System.Text.Encoding**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="b0df2-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="b0df2-139">FullPath</span></span>

<span data-ttu-id="b0df2-140">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0df2-141">Die schreibgeschützte Eigenschaft, die die Zeichenfolge abruft, die den vollständigen Pfad der geöffneten Datei angibt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="b0df2-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="b0df2-142">IsSaved</span></span>

<span data-ttu-id="b0df2-143">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0df2-144">Die schreibgeschützte boolesche Eigenschaft, die **$true** zurückgibt, wenn die Datei nach der letzten Änderung gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="b0df2-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="b0df2-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="b0df2-145">IsUntitled</span></span>

<span data-ttu-id="b0df2-146">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0df2-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b0df2-147">Die schreibgeschützte Eigenschaft, die **$true** zurückgibt, wenn für die Datei nie ein Titel festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="b0df2-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="b0df2-148">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b0df2-148">See Also</span></span>

- [<span data-ttu-id="b0df2-149">Das ISEFileCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="b0df2-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="b0df2-150">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="b0df2-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b0df2-151">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="b0df2-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)