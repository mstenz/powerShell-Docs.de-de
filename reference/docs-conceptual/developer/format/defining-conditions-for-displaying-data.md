---
title: Definieren von Bedingungen zum Anzeigen von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363899"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="fea9e-102">Definieren von Bedingungen für die Datenanzeige</span><span class="sxs-lookup"><span data-stu-id="fea9e-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="fea9e-103">Wenn Sie definieren, welche Daten von einer Ansicht oder einem Steuerelement angezeigt werden, können Sie eine Bedingung angeben, die vorhanden sein muss, damit die Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fea9e-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="fea9e-104">Die Bedingung kann durch eine bestimmte Eigenschaft ausgelöst werden, oder wenn ein Skript oder ein Eigenschafts Wert als `true` ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="fea9e-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="fea9e-105">Wenn die Auswahlbedingung erfüllt ist, wird die Definition der Ansicht bzw. des Steuer Elements verwendet.</span><span class="sxs-lookup"><span data-stu-id="fea9e-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="fea9e-106">Angeben einer Auswahlbedingung für eine Definition</span><span class="sxs-lookup"><span data-stu-id="fea9e-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="fea9e-107">Wenn eine Definition für eine Sicht oder ein Steuerelement erstellt wird, wird das `EntrySelectedBy`-Element verwendet, um anzugeben, welche Objekte die Definition verwenden, oder welche Bedingung für die zu verwendende Definition vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="fea9e-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="fea9e-108">Die Bedingung wird durch das `SelectionCondition`-Element angegeben.</span><span class="sxs-lookup"><span data-stu-id="fea9e-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="fea9e-109">Im folgenden Beispiel wird eine Auswahlbedingung für eine Definition einer Tabellenansicht angegeben.</span><span class="sxs-lookup"><span data-stu-id="fea9e-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="fea9e-110">In diesem Beispiel wird die Definition nur verwendet, wenn das angegebene Skript `true` ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="fea9e-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="fea9e-111">Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die Sie für die Definition einer Sicht oder eines Steuer Elements angeben können.</span><span class="sxs-lookup"><span data-stu-id="fea9e-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="fea9e-112">Die einzigen Anforderungen sind die folgenden:</span><span class="sxs-lookup"><span data-stu-id="fea9e-112">The only requirements are the following:</span></span>

- <span data-ttu-id="fea9e-113">Die Auswahlbedingung muss einen Eigenschaftsnamen oder ein Skript angeben, um die Bedingung zu initiieren, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="fea9e-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="fea9e-114">Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="fea9e-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="fea9e-115">Angeben einer Auswahlbedingung für ein Element</span><span class="sxs-lookup"><span data-stu-id="fea9e-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="fea9e-116">Sie können auch angeben, wann ein Element einer Listenansicht oder eines Steuer Elements verwendet wird, indem Sie das `ItemSelectionCondition`-Element in die Element Definition einschließen.</span><span class="sxs-lookup"><span data-stu-id="fea9e-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="fea9e-117">Im folgenden Beispiel wird eine Auswahlbedingung für ein Element einer Listenansicht angegeben.</span><span class="sxs-lookup"><span data-stu-id="fea9e-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="fea9e-118">In diesem Beispiel wird das Element nur verwendet, wenn das Skript `true` ausgewertet wird.</span><span class="sxs-lookup"><span data-stu-id="fea9e-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="fea9e-119">Sie können nur eine Auswahlbedingung für ein Element angeben.</span><span class="sxs-lookup"><span data-stu-id="fea9e-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="fea9e-120">Und die Bedingung muss einen Eigenschaftsnamen oder ein Skript angeben, um die Bedingung zu initiieren, kann jedoch nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="fea9e-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="fea9e-121">XML-Elemente</span><span class="sxs-lookup"><span data-stu-id="fea9e-121">XML Elements</span></span>

 <span data-ttu-id="fea9e-122">Die folgenden XML-Elemente werden verwendet, um eine Auswahlbedingung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="fea9e-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="fea9e-123">Die folgenden Elemente geben Auswahl Bedingungen für Sicht Definitionen an:</span><span class="sxs-lookup"><span data-stu-id="fea9e-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="fea9e-124">Selectioncondition-Element für entryselectedby für tablecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="fea9e-125">Selectioncondition-Element für entryselectedby für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="fea9e-126">Selectioncondition-Element für entryselectedby für widecontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="fea9e-127">Selectioncondition-Element für entryselectedby für CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="fea9e-128">Die folgenden Elemente geben Auswahl Bedingungen für allgemeine und Ansicht-Steuerelement Definitionen an:</span><span class="sxs-lookup"><span data-stu-id="fea9e-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="fea9e-129">Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="fea9e-130">Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="fea9e-131">Mit dem folgenden Element wird die Auswahlbedingung zum Erweitern von Auflistungs Objekten angegeben:</span><span class="sxs-lookup"><span data-stu-id="fea9e-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="fea9e-132">Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="fea9e-133">Das folgende Element gibt die Auswahlbedingung zum Anzeigen einer neuen Gruppe von Daten an:</span><span class="sxs-lookup"><span data-stu-id="fea9e-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="fea9e-134">Selectioncondition-Element für entryselectedby für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="fea9e-135">Das folgende Element gibt eine Elementauswahl Bedingung für eine Listenansicht an:</span><span class="sxs-lookup"><span data-stu-id="fea9e-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="fea9e-136">Itemselectioncondition-Element für ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="fea9e-137">Die folgenden Elemente geben eine Elementauswahl Bedingung für-Steuerelemente an:</span><span class="sxs-lookup"><span data-stu-id="fea9e-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="fea9e-138">Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="fea9e-139">Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für View (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="fea9e-140">Itemselectioncondition-Element für ExpressionBinding für CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fea9e-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="fea9e-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fea9e-141">See Also</span></span>

[<span data-ttu-id="fea9e-142">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="fea9e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
