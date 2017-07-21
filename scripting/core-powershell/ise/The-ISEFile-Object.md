---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Das ISEFile-Objekt
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 0e1c09c4a92868448d76cc7b4954d250773ce2f2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="f3656-103">Das ISEFile-Objekt</span><span class="sxs-lookup"><span data-stu-id="f3656-103">The ISEFile Object</span></span>
  <span data-ttu-id="f3656-104">Ein **ISEFile**-Objekt stellt eine Datei in Windows-PowerShell® Integrated Scripting Environment (ISE) dar</span><span class="sxs-lookup"><span data-stu-id="f3656-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="f3656-105">Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEFile-Klasse.</span><span class="sxs-lookup"><span data-stu-id="f3656-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="f3656-106">In diesem Thema werden die Elementmethoden und -eigenschaften aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="f3656-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="f3656-107">**$psISE.CurrentFile** und die Dateien in der DateiSammlung auf einer PowerShell-Registerkarte sind Instanzen der Microsoft.PowerShell.Host.ISE.ISEFile-Klasse.</span><span class="sxs-lookup"><span data-stu-id="f3656-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="f3656-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="f3656-108">Methods</span></span>

###  <span data-ttu-id="f3656-109"><a name="save-override"></a> Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="f3656-109"><a name="save-override"></a> Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="f3656-110">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3656-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f3656-111">Speichert die Datei auf dem Datenträger.</span><span class="sxs-lookup"><span data-stu-id="f3656-111">Saves the file to disk.</span></span>

 <span data-ttu-id="f3656-112">**\[saveEncoding\]** – Optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 – Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll</span><span class="sxs-lookup"><span data-stu-id="f3656-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="f3656-113">Der Standardwert lautet **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="f3656-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="f3656-114">**Ausnahmen**</span><span class="sxs-lookup"><span data-stu-id="f3656-114">**Exceptions**</span></span>
 -   <span data-ttu-id="f3656-115">**System.IO.IOException**: Die Datei konnte nicht gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="f3656-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

###  <span data-ttu-id="f3656-116"><a name="saveas"></a> SaveAs\(Dateiname, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="f3656-116"><a name="saveas"></a> SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="f3656-117">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3656-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f3656-118">Speichert die Datei mit dem angegebenen Namen und der angegebenen Codierung.</span><span class="sxs-lookup"><span data-stu-id="f3656-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="f3656-119">**Dateiname**: Zeichenfolge – der Name, der zum Speichern der Datei verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="f3656-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="f3656-120">**\[saveEncoding\]** – Optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 – Ein optionaler Zeichencodierungsparameter, der für die gespeicherte Datei verwendet werden soll</span><span class="sxs-lookup"><span data-stu-id="f3656-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx)
 An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="f3656-121">Der Standardwert lautet **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="f3656-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="f3656-122">**Ausnahmen**</span><span class="sxs-lookup"><span data-stu-id="f3656-122">**Exceptions**</span></span>
 -   <span data-ttu-id="f3656-123">**System.ArgumentNullException**: Der **filename**-Parameter ist NULL.</span><span class="sxs-lookup"><span data-stu-id="f3656-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

-   <span data-ttu-id="f3656-124">**System.ArgumentException**: Der **filename**-Parameter ist leer.</span><span class="sxs-lookup"><span data-stu-id="f3656-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

-   <span data-ttu-id="f3656-125">**System.IO.IOException**: Die Datei konnte nicht gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="f3656-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="f3656-126">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="f3656-126">Properties</span></span>

###  <span data-ttu-id="f3656-127"><a name="Displayname"></a> DisplayName</span><span class="sxs-lookup"><span data-stu-id="f3656-127"><a name="Displayname"></a> DisplayName</span></span>
  <span data-ttu-id="f3656-128">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3656-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f3656-129">Die schreibgeschützte Eigenschaft, die die Zeichenfolge mit dem Anzeigenamen dieser Datei abruft.</span><span class="sxs-lookup"><span data-stu-id="f3656-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="f3656-130">Der Name wird auf der Registerkarte **Datei** oben im Editor angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f3656-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="f3656-131">Ein Sternchen \(\*\) am Ende des Namens zeigt an, dass die Datei nicht gespeicherte Änderungen enthält.</span><span class="sxs-lookup"><span data-stu-id="f3656-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

###  <span data-ttu-id="f3656-132"><a name="Editor"></a> Editor</span><span class="sxs-lookup"><span data-stu-id="f3656-132"><a name="Editor"></a> Editor</span></span>
  <span data-ttu-id="f3656-133">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3656-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f3656-134">Die schreibgeschützte Eigenschaft, die das für die angegebene Datei verwendete [Editor-Objekt](The-ISEEditor-Object.md) abruft.</span><span class="sxs-lookup"><span data-stu-id="f3656-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

###  <span data-ttu-id="f3656-135"><a name="Encoding"></a> Encoding</span><span class="sxs-lookup"><span data-stu-id="f3656-135"><a name="Encoding"></a> Encoding</span></span>
  <span data-ttu-id="f3656-136">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3656-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f3656-137">Die schreibgeschützte Eigenschaft, die die ursprüngliche Dateicodierung abruft.</span><span class="sxs-lookup"><span data-stu-id="f3656-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="f3656-138">Dies ist ein **System.Text.Encoding**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="f3656-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

###  <span data-ttu-id="f3656-139"><a name="FullPath"></a> FullPath</span><span class="sxs-lookup"><span data-stu-id="f3656-139"><a name="FullPath"></a> FullPath</span></span>
  <span data-ttu-id="f3656-140">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3656-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f3656-141">Die schreibgeschützte Eigenschaft, die die Zeichenfolge abruft, die den vollständigen Pfad der geöffneten Datei angibt.</span><span class="sxs-lookup"><span data-stu-id="f3656-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

###  <span data-ttu-id="f3656-142"><a name="IsSaved"></a> IsSaved</span><span class="sxs-lookup"><span data-stu-id="f3656-142"><a name="IsSaved"></a> IsSaved</span></span>
  <span data-ttu-id="f3656-143">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3656-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f3656-144">Die schreibgeschützte boolesche Eigenschaft, die **$true** zurückgibt, wenn die Datei nach der letzten Änderung gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="f3656-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

###  <span data-ttu-id="f3656-145"><a name="IsUntitled"></a> IsUntitled</span><span class="sxs-lookup"><span data-stu-id="f3656-145"><a name="IsUntitled"></a> IsUntitled</span></span>
  <span data-ttu-id="f3656-146">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3656-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f3656-147">Die schreibgeschützte Eigenschaft, die **$true** zurückgibt, wenn für die Datei nie ein Titel festgelegt wurde.</span><span class="sxs-lookup"><span data-stu-id="f3656-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="f3656-148">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f3656-148">See Also</span></span>
- [<span data-ttu-id="f3656-149">Das ISEFileCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="f3656-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="f3656-150">Das Windows PowerShell ISE-Skriptobjektmodell</span><span class="sxs-lookup"><span data-stu-id="f3656-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="f3656-151">Referenz zum Windows PowerShell ISE-Objektmodell</span><span class="sxs-lookup"><span data-stu-id="f3656-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="f3656-152">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="f3656-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
