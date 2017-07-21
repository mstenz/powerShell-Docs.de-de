---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Zweck des Windows PowerShell ISE-Skriptobjektmodells
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 65535948d681ec63c6cc36583c6d145cfa19b937
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="ddf7f-103">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="ddf7f-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="ddf7f-104">Objekte sind der Form und Funktion von Windows PowerShell Integrated Scripting Environment (ISE) zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="ddf7f-105">Die Modellreferenz bietet Details zu den Elementeigenschaften und Methoden, die diese Objekte verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="ddf7f-106">Die Beispiele zeigen Ihnen, wie Sie mithilfe von Skripts direkt auf diese Methoden und Eigenschaften zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="ddf7f-107">Das Skriptobjektmodell erleichtert die folgenden Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="ddf7f-108">Anpassen der Darstellung von Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ddf7f-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="ddf7f-109">Sie können das Objektmodell verwenden, um die Anwendungseinstellungen und -optionen zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="ddf7f-110">Sie können sie beispielsweise folgendermaßen ändern:</span><span class="sxs-lookup"><span data-stu-id="ddf7f-110">For example, you can modify them as follows:</span></span>

-   <span data-ttu-id="ddf7f-111">Sie können die Farbe der Fehlermeldungen, Warnungen, ausführlichen Ausgaben, und Debugausgaben ändern.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

-   <span data-ttu-id="ddf7f-112">Sie können die Hintergrundfarben für den Befehlsbereich, den Ausgabebereich und den Skriptbereich abrufen oder festlegen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

-   <span data-ttu-id="ddf7f-113">Sie können die Vordergrundfarbe im Ausgabebereich festlegen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-113">You can set the foreground color for the Output pane.</span></span>

-   <span data-ttu-id="ddf7f-114">Sie können die Schriftart und Schriftgröße für Windows PowerShell ISE festlegen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

-   <span data-ttu-id="ddf7f-115">Sie können Warnungen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-115">You can configure warnings.</span></span> <span data-ttu-id="ddf7f-116">Diese Einstellung schließt Warnungen ein, die ausgegeben werden, wenn eine Datei in mehreren PowerShell-Registerkarten geöffnet wird oder wenn eine Datei ausgeführt wird, bevor sie gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

-   <span data-ttu-id="ddf7f-117">Sie können zwischen zwei Ansichten wechseln: Entweder werden der Skriptbereich und der Ausgabebereich nebeneinander angezeigt, oder der Skriptbereich wird über dem Ausgabebereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="ddf7f-118">Sie können den Befehlsbereich oben oder unten an den Ausgabebereich andocken.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="ddf7f-119">Erweitern der Funktionalität von Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ddf7f-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="ddf7f-120">Sie können das Objektmodell verwenden, um die Funktionalität von Windows PowerShell ISE zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="ddf7f-121">Beispielsweise können Sie folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="ddf7f-121">For example, you can:</span></span>

-   <span data-ttu-id="ddf7f-122">Fügen Sie Instanzen von Windows PowerShell ISE hinzu und ändern Sie sie.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="ddf7f-123">Sie können z.B. neue Menüelemente hinzufügen und die neuen Elemente Skripts zuordnen, um die Menüs zu ändern.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

-   <span data-ttu-id="ddf7f-124">Erstellen Sie Skripts, die einige der Aufgaben ausführen, die Sie mithilfe der Menübefehle und Schaltflächen in Windows PowerShell ISE ausführen können.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="ddf7f-125">Beispielsweise können Sie eine PowerShell-Registerkarte hinzufügen, entfernen oder auswählen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

-   <span data-ttu-id="ddf7f-126">Ergänzen Sie Aufgaben, die mithilfe der Menübefehle und Schaltflächen ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="ddf7f-127">Beispielsweise können Sie eine PowerShell-Registerkarte umbenennen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-127">For example, you can rename a PowerShell tab.</span></span>

-   <span data-ttu-id="ddf7f-128">Ändern Sie Textpuffer für den Befehlsbereich, den Ausgabebereich und den Skriptbereich, die einer Datei zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="ddf7f-129">Beispielsweise können Sie folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="ddf7f-129">For example, you can:</span></span>

    -   <span data-ttu-id="ddf7f-130">Den gesamten Text abrufen oder festlegen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-130">Get or set all text.</span></span>

    -   <span data-ttu-id="ddf7f-131">Eine Textauswahl abrufen oder festlegen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="ddf7f-132">Ein Skript ausführen oder einen ausgewählten Teil eines Skripts ausführen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="ddf7f-133">So scrollen, dass eine bestimmte Zeile in der Ansicht erscheint.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="ddf7f-134">Text an der Position des Caretzeichens einfügen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="ddf7f-135">Einen Textblock auswählen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-135">Select a block of text.</span></span>

    -   <span data-ttu-id="ddf7f-136">Die letzte Zeilennummer abrufen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-136">Get the last line number.</span></span>

-   <span data-ttu-id="ddf7f-137">Dateivorgänge ausführen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-137">Perform file operations.</span></span> <span data-ttu-id="ddf7f-138">Beispielsweise können Sie folgende Aktionen ausführen:</span><span class="sxs-lookup"><span data-stu-id="ddf7f-138">For example, you can:</span></span>

    -   <span data-ttu-id="ddf7f-139">Eine Datei öffnen, speichern oder unter einem anderen Namen speichern.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="ddf7f-140">Feststellen, ob eine Datei seit der letzten Speicherung geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="ddf7f-141">Den Dateinamen abrufen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-141">Get the file name.</span></span>

    -   <span data-ttu-id="ddf7f-142">Eine Datei auswählen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="ddf7f-143">Automatisieren von Aufgaben</span><span class="sxs-lookup"><span data-stu-id="ddf7f-143">Automating tasks</span></span>
 <span data-ttu-id="ddf7f-144">Das Skriptobjektmodell verwenden, um Tastenkombinationen für häufige Vorgänge zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ddf7f-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddf7f-145">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ddf7f-145">See Also</span></span>
- [<span data-ttu-id="ddf7f-146">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="ddf7f-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="ddf7f-147">Referenz zum Windows PowerShell ISE-Objektmodell</span><span class="sxs-lookup"><span data-stu-id="ddf7f-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="ddf7f-148">Das Windows PowerShell ISE-Skriptobjektmodell</span><span class="sxs-lookup"><span data-stu-id="ddf7f-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
