---
title: Definieren von Auswahl Sätzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368849"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="bd90f-102">Definieren von Auswahlgruppen</span><span class="sxs-lookup"><span data-stu-id="bd90f-102">Defining Selection Sets</span></span>

<span data-ttu-id="bd90f-103">Wenn Sie mehrere Ansichten und Steuerelemente erstellen, können Sie Sätze von Objekten definieren, die als Auswahl Sätze bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="bd90f-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="bd90f-104">Mithilfe eines Auswahl Satzes können Sie die Objekte einmal definieren, ohne Sie für jede Ansicht oder jedes Steuerelement wiederholt definieren zu müssen.</span><span class="sxs-lookup"><span data-stu-id="bd90f-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="bd90f-105">Normalerweise werden Auswahl Sätze verwendet, wenn Sie über einen Satz verwandter .NET-Objekte verfügen.</span><span class="sxs-lookup"><span data-stu-id="bd90f-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="bd90f-106">Die Formatierungs Datei `FileSystem` (File System. Format. ps1xml) definiert z. b. einen Auswahl Satz der Dateisystemtypen, die von mehreren Ansichten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bd90f-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="bd90f-107">Wo Auswahl Sätze definiert sind und referenziert werden</span><span class="sxs-lookup"><span data-stu-id="bd90f-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="bd90f-108">Sie definieren Auswahl Sätze als Teil der allgemeinen Daten, die von allen Sichten und Steuerelementen verwendet werden können, die in der Formatierungs Datei definiert sind.</span><span class="sxs-lookup"><span data-stu-id="bd90f-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="bd90f-109">Im folgenden Beispiel wird gezeigt, wie drei Auswahl Sätze definiert werden.</span><span class="sxs-lookup"><span data-stu-id="bd90f-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="bd90f-110">Auf folgende Weise können Sie auf eine Auswahl festgelegt werden:</span><span class="sxs-lookup"><span data-stu-id="bd90f-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="bd90f-111">Jede Sicht verfügt über ein `ViewSelectedBy`-Element, das definiert, welche Objekte mithilfe der-Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bd90f-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="bd90f-112">Das `ViewSelectedBy`-Element verfügt über ein untergeordnetes `SelectionSetName`-Element, das den Auswahl Satz angibt, der von allen Definitionen der Sicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bd90f-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="bd90f-113">Es gibt keine Einschränkung hinsichtlich der Anzahl von Auswahl Sätzen, auf die Sie von einer Ansicht aus verweisen können.</span><span class="sxs-lookup"><span data-stu-id="bd90f-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="bd90f-114">In jeder Definition einer Sicht oder eines Steuer Elements definiert das `EntrySelectedBy`-Element, welche Objekte mit dieser Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bd90f-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="bd90f-115">In der Regel verfügt eine Ansicht oder ein Steuerelement nur über eine Definition, sodass die Objekte vom `ViewSelectedBy`-Element definiert werden.</span><span class="sxs-lookup"><span data-stu-id="bd90f-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="bd90f-116">Das `EntrySelectedBy`-Element der Definition verfügt über ein untergeordnetes `SelectionSetName`-Element, das den Auswahl Satz angibt.</span><span class="sxs-lookup"><span data-stu-id="bd90f-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="bd90f-117">Wenn Sie den Auswahl Satz für eine Definition angeben, können Sie keines der anderen untergeordneten Elemente des `EntrySelectedBy`-Elements angeben.</span><span class="sxs-lookup"><span data-stu-id="bd90f-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="bd90f-118">In jeder Definition einer Sicht oder eines Steuer Elements kann das `SelectionCondition`-Element verwendet werden, um eine Bedingung für die Verwendung der Definition anzugeben.</span><span class="sxs-lookup"><span data-stu-id="bd90f-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="bd90f-119">Das `SelectionCondition`-Element verfügt über ein untergeordnetes `SelectionSetName`-Element, das den Auswahl Satz angibt, der die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="bd90f-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="bd90f-120">Die Bedingung wird ausgelöst, wenn eines der im Auswahl Satz definierten Objekte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bd90f-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="bd90f-121">Weitere Informationen zum Festlegen dieser Bedingungen finden Sie unter Definieren von [Bedingungen für den Fall, dass Daten angezeigt](./defining-conditions-for-displaying-data.md)werden.</span><span class="sxs-lookup"><span data-stu-id="bd90f-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="bd90f-122">Beispiel für Auswahl Satz</span><span class="sxs-lookup"><span data-stu-id="bd90f-122">Selection Set Example</span></span>

<span data-ttu-id="bd90f-123">Das folgende Beispiel zeigt einen Auswahl Satz, der direkt aus der von Windows PowerShell bereitgestellten `FileSystem`-Formatierungs Datei entnommen wird.</span><span class="sxs-lookup"><span data-stu-id="bd90f-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="bd90f-124">Weitere Informationen zu anderen Windows PowerShell-Formatierungs Dateien finden Sie unter [Windows PowerShell-Formatierungs Dateien](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="bd90f-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="bd90f-125">Auf den vorherigen Auswahl Satz wird im `ViewSelectedBy`-Element einer Tabellen Sicht verwiesen.</span><span class="sxs-lookup"><span data-stu-id="bd90f-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="bd90f-126">XML-Elemente</span><span class="sxs-lookup"><span data-stu-id="bd90f-126">XML Elements</span></span>

 <span data-ttu-id="bd90f-127">Es gibt keine Beschränkung für die Anzahl der Auswahl Sätze, die Sie definieren können.</span><span class="sxs-lookup"><span data-stu-id="bd90f-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="bd90f-128">Die folgenden XML-Elemente werden verwendet, um einen Auswahl Satz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bd90f-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="bd90f-129">Das [selectionsets](./selectionsets-element-format.md) -Element definiert die Sätze von .NET-Objekten, auf die von den Sichten und Steuerelementen der Formatierungs Datei verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="bd90f-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="bd90f-130">Das [SelectionSet](./selectionset-element-format.md) -Element definiert einen einzelnen Satz von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="bd90f-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="bd90f-131">Das [Name](./name-element-for-selectionset-format.md) -Element gibt den Namen an, der verwendet wird, um auf den Auswahl Satz zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="bd90f-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="bd90f-132">Das [types](./types-element-for-selectionset-format.md) -Element gibt die .NET-Typen der Objekte des Auswahl Satzes an.</span><span class="sxs-lookup"><span data-stu-id="bd90f-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="bd90f-133">(In Formatierungs Dateien werden Objekte durch ihren .NET-Typ angegeben.)</span><span class="sxs-lookup"><span data-stu-id="bd90f-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="bd90f-134">Die folgenden XML-Elemente werden verwendet, um einen Auswahl Satz anzugeben.</span><span class="sxs-lookup"><span data-stu-id="bd90f-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="bd90f-135">Das folgende Element gibt den Auswahl Satz an, der in allen Definitionen der Sicht verwendet werden soll:</span><span class="sxs-lookup"><span data-stu-id="bd90f-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="bd90f-136">Selectionsetname-Element für viewselectedby (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="bd90f-137">Selectionsetname-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="bd90f-138">Die folgenden Elemente geben den Auswahl Satz an, der von einer einzelnen Sicht Definition verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="bd90f-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="bd90f-139">Selectionsetname-Element für entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="bd90f-140">Selectionsetname-Element für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="bd90f-141">Selectionsetname-Element für entryselectedby für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="bd90f-142">Selectionsetname-Element für entryselectedby für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="bd90f-143">Die folgenden Elemente geben den Auswahl Satz an, der von Common-und View-Steuerelement Definitionen verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="bd90f-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="bd90f-144">Selectionsetname-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="bd90f-145">Selectionsetname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="bd90f-146">Die folgenden Elemente geben den Auswahl Satz an, der verwendet wird, wenn Sie definieren, welches Objekt erweitert werden soll:</span><span class="sxs-lookup"><span data-stu-id="bd90f-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="bd90f-147">Selectionsetname-Element für entryselectedby für enumerableexpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="bd90f-148">Die folgenden Elemente geben den Auswahl Satz an, der von Auswahl Bedingungen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bd90f-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="bd90f-149">Selectionsetname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="bd90f-150">Selectionsetname-Element für selectioncondition für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="bd90f-151">Selectionsetname-Element für selectioncondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="bd90f-152">Selectionsetname-Element für selectioncondition für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="bd90f-153">Selectionsetname-Element für selectioncondition für entryselectedby für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="bd90f-154">Selectionsetname-Element für selectioncondition für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="bd90f-155">Selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="bd90f-156">Selectionsetname-Element für selectioncondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bd90f-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="bd90f-157">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bd90f-157">See Also</span></span>

[<span data-ttu-id="bd90f-158">Selectionsets</span><span class="sxs-lookup"><span data-stu-id="bd90f-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="bd90f-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="bd90f-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="bd90f-160">Benennen</span><span class="sxs-lookup"><span data-stu-id="bd90f-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="bd90f-161">Solche</span><span class="sxs-lookup"><span data-stu-id="bd90f-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="bd90f-162">PowerShell-Formatierungs Dateien</span><span class="sxs-lookup"><span data-stu-id="bd90f-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="bd90f-163">Definieren von Bedingungen für die Anzeige von Daten</span><span class="sxs-lookup"><span data-stu-id="bd90f-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="bd90f-164">Schreiben einer PowerShell-Formatierungs-und-Typen Datei</span><span class="sxs-lookup"><span data-stu-id="bd90f-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
