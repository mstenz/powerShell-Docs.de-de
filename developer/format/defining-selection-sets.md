---
title: Definieren die Auswahl legt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858926"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="99a49-102">Definieren von Auswahlgruppen</span><span class="sxs-lookup"><span data-stu-id="99a49-102">Defining Selection Sets</span></span>

<span data-ttu-id="99a49-103">Wenn Sie mehrere Ansichten und Steuerelementen zu erstellen, können Sie Gruppen von Objekten, die auf die verwiesen werden, als Auswahl legt definieren.</span><span class="sxs-lookup"><span data-stu-id="99a49-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="99a49-104">Ein Auswahlsatz können Sie die Objekte einmal definieren, ohne dass sie wiederholt für jede Sicht oder ein Steuerelement definieren.</span><span class="sxs-lookup"><span data-stu-id="99a49-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="99a49-105">Auswahl legt werden in der Regel verwendet, wenn Sie einen Satz von verknüpften Objekten für .NET verfügen.</span><span class="sxs-lookup"><span data-stu-id="99a49-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="99a49-106">Z. B. die `FileSystem` Formatierungsdatei (FileSystem.format.ps1xml) definiert einen Auswahlsatz das System der Typen von Dateien, die mehrere Ansichten verwenden.</span><span class="sxs-lookup"><span data-stu-id="99a49-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="99a49-107">Wo sind Auswahl definiert und auf die verwiesen wird</span><span class="sxs-lookup"><span data-stu-id="99a49-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="99a49-108">Sie definieren die Auswahl legt als Teil der allgemeinen Daten, die von den Ansichten und Steuerelemente, die in die Formatierungsdatei verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="99a49-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="99a49-109">Das folgende Beispiel zeigt, wie drei Sätze der Auswahl definiert wird.</span><span class="sxs-lookup"><span data-stu-id="99a49-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="99a49-110">Sie können eine Auswahl verweisen legt fest, es gibt folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="99a49-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="99a49-111">Jede Ansicht hat eine `ViewSelectedBy` -Element, das definiert, welche Objekte mithilfe der Sicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99a49-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="99a49-112">Die `ViewSelectedBy` Element verfügt über eine `SelectionSetName` untergeordnetes Element, das die Auswahl gibt an, die festlegen, die alle Definitionen zur Verwendung anzeigen.</span><span class="sxs-lookup"><span data-stu-id="99a49-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="99a49-113">Es gibt keine Einschränkung für die Anzahl der Auswahl-Sätze, die Sie aus einer Sicht verweisen können.</span><span class="sxs-lookup"><span data-stu-id="99a49-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="99a49-114">In jeder Definition einer Ansicht oder das Steuerelement das `EntrySelectedBy` -Element definiert, welche Objekte über dieser Definition angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99a49-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="99a49-115">In der Regel eine Sicht für oder Kontrolle hat nur eine Definition, damit die Objekte, indem definiert sind die `ViewSelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="99a49-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="99a49-116">Die `EntrySelectedBy` Element der Definition verfügt über eine `SelectionSetName` untergeordnetes Element, das die Auswahl festlegt.</span><span class="sxs-lookup"><span data-stu-id="99a49-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="99a49-117">Wenn Sie die Auswahl, legen Sie für die Definition eines angeben, können nicht Sie keines der anderen untergeordneten Elementen angeben der `EntrySelectedBy` Element.</span><span class="sxs-lookup"><span data-stu-id="99a49-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="99a49-118">In jeder Definition einer Ansicht oder das Steuerelement das `SelectionCondition` Element kann verwendet werden, um für die bei der Definition verwendet wird, eine Bedingung angeben.</span><span class="sxs-lookup"><span data-stu-id="99a49-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="99a49-119">Die `SelectionCondition` Element verfügt über eine `SelectionSetName` untergeordneten-Element, das angibt, die Auswahl festgelegt wird, löst die Bedingung.</span><span class="sxs-lookup"><span data-stu-id="99a49-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="99a49-120">Die Bedingung wird immer dann ausgelöst, wenn eines der Objekte, die definiert, in der Auswahl angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="99a49-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="99a49-121">Weitere Informationen zum Festlegen dieser Bedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="99a49-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="99a49-122">Auswahl & ndash; Beispiel</span><span class="sxs-lookup"><span data-stu-id="99a49-122">Selection Set Example</span></span>

<span data-ttu-id="99a49-123">Das folgende Beispiel zeigt eine Auswahl-Gruppe, die direkt aus der `FileSystem` Formatierung der Datei, die von Windows PowerShell bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="99a49-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="99a49-124">Weitere Informationen zu anderen Windows PowerShell-Formatierungsdateien, finden Sie unter [Formatieren von Windows PowerShell-Dateien](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="99a49-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="99a49-125">Die vorherige Auswahl Gruppe verwiesen wird, der `ViewSelectedBy` Element einer Tabellenansicht.</span><span class="sxs-lookup"><span data-stu-id="99a49-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="99a49-126">XML-Elemente</span><span class="sxs-lookup"><span data-stu-id="99a49-126">XML Elements</span></span>

 <span data-ttu-id="99a49-127">Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die Sie definieren können.</span><span class="sxs-lookup"><span data-stu-id="99a49-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="99a49-128">Die folgende XML-Elemente werden verwendet, um einen Auswahlsatz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="99a49-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="99a49-129">Die [SelectionSets](./selectionsets-element-format.md) -Element definiert, die Sätze von .NET-Objekten, die von den Sichten verwiesen werden und die Steuerelemente die Formatierungsdatei.</span><span class="sxs-lookup"><span data-stu-id="99a49-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="99a49-130">Die [SelectionSet](./selectionset-element-format.md) Element definiert einen Satz von .NET-Objekten.</span><span class="sxs-lookup"><span data-stu-id="99a49-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="99a49-131">Die [Namen](./name-element-for-selectionset-format.md) Element gibt den Namen, die auf der Auswahlsatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="99a49-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="99a49-132">Die [Typen](./types-element-for-selectionset-format.md) Element gibt die .NET Typen der Objekte des Satzes Auswahl.</span><span class="sxs-lookup"><span data-stu-id="99a49-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="99a49-133">(In Formatierungsdateien, werden Objekte anhand ihres Typs .NET angegeben.)</span><span class="sxs-lookup"><span data-stu-id="99a49-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="99a49-134">Die folgende XML-Elemente werden verwendet, um einen Auswahlsatz anzugeben.</span><span class="sxs-lookup"><span data-stu-id="99a49-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="99a49-135">Das folgende Element gibt an, die Auswahl, in der Ansicht alle Definitionen verwenden:</span><span class="sxs-lookup"><span data-stu-id="99a49-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="99a49-136">SelectionSetName-Element für ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="99a49-137">SelectionSetName-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="99a49-138">Die folgenden Elemente angeben die Auswahlsatz definitionsgemäß eine einzelne Ansicht verwendet:</span><span class="sxs-lookup"><span data-stu-id="99a49-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="99a49-139">SelectionSetName-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="99a49-140">SelectionSetName-Element für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="99a49-141">SelectionSetName-Element für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="99a49-142">SelectionSetName-Element für EntrySelectedBy für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="99a49-143">Die folgenden Elemente angeben, die Auswahlsatz von allgemeinen verwendet und Steuerelementdefinitionen anzeigen:</span><span class="sxs-lookup"><span data-stu-id="99a49-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="99a49-144">SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="99a49-145">SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="99a49-146">Die folgenden Elemente angeben, den Auswahlsatz verwendet, wenn Sie, welches Objekt definieren zu erweitern:</span><span class="sxs-lookup"><span data-stu-id="99a49-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="99a49-147">SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="99a49-148">Die folgenden Elemente angeben die Auswahlsatz von auswahlbedingungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="99a49-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="99a49-149">SelectionSetName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="99a49-150">SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="99a49-151">SelectionSetName-Element für SelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="99a49-152">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="99a49-153">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="99a49-154">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="99a49-155">SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="99a49-156">SelectionSetName-Element für SelectionCondition für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="99a49-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="99a49-157">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="99a49-157">See Also</span></span>

[<span data-ttu-id="99a49-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="99a49-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="99a49-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="99a49-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="99a49-160">Name</span><span class="sxs-lookup"><span data-stu-id="99a49-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="99a49-161">Typen</span><span class="sxs-lookup"><span data-stu-id="99a49-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="99a49-162">Formatieren von PowerShell-Dateien</span><span class="sxs-lookup"><span data-stu-id="99a49-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="99a49-163">Definieren von Bedingungen für, wenn die Daten angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="99a49-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="99a49-164">Schreiben eine PowerShell-Formatierung und Typendatei</span><span class="sxs-lookup"><span data-stu-id="99a49-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
