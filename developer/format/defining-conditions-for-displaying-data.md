---
title: Definieren von Bedingungen für die Anzeige von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855646"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="6f880-102">Definieren von Bedingungen für die Datenanzeige</span><span class="sxs-lookup"><span data-stu-id="6f880-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="6f880-103">Beim definieren, welche Daten von einer Sicht oder ein Steuerelement angezeigt werden, können Sie eine Bedingung angeben, die vorhanden sein muss, bis die Daten angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="6f880-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="6f880-104">Die Bedingung kann ausgelöst werden, durch eine bestimmte Eigenschaft oder ein Skript oder Eigenschaftswert ergibt `true`.</span><span class="sxs-lookup"><span data-stu-id="6f880-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="6f880-105">Wenn die auswahlbedingung erfüllt ist, wird die Definition der Sicht oder Steuerelement verwendet.</span><span class="sxs-lookup"><span data-stu-id="6f880-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="6f880-106">Angeben einer Auswahlbedingung eine für die Definition eines</span><span class="sxs-lookup"><span data-stu-id="6f880-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="6f880-107">Beim Erstellen einer Definition für eine Sicht oder ein Steuerelement, das `EntrySelectedBy` Element verwendet, um anzugeben, welche Objekte verwenden, werden die Definition oder welcher Bedingung vorhanden sein muss, für die Definition verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="6f880-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="6f880-108">Die Bedingung wird angegeben, indem die `SelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="6f880-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="6f880-109">Im folgenden Beispiel wird eine auswahlbedingung für eine Definition einer Tabellenansicht angegeben.</span><span class="sxs-lookup"><span data-stu-id="6f880-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="6f880-110">In diesem Beispiel wird die Definition verwendet, nur, wenn das angegebene Skript Auswertung `true`.</span><span class="sxs-lookup"><span data-stu-id="6f880-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="6f880-111">Es gibt keine Beschränkung für die Anzahl der von auswahlbedingungen, die Sie eine Definition für eine Sicht für oder Kontrolle angeben können.</span><span class="sxs-lookup"><span data-stu-id="6f880-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="6f880-112">Die einzige Voraussetzung ist Folgendes:</span><span class="sxs-lookup"><span data-stu-id="6f880-112">The only requirements are the following:</span></span>

- <span data-ttu-id="6f880-113">Die auswahlbedingung muss angeben, einen Eigenschaftennamen oder Skript, um die Bedingung auslösen, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="6f880-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="6f880-114">Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="6f880-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="6f880-115">Eine Auswahlbedingung für ein Element angeben</span><span class="sxs-lookup"><span data-stu-id="6f880-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="6f880-116">Sie können auch angeben, wenn ein Element eines Listenansicht oder eines Steuerelements verwendet wird, durch Einschließen der `ItemSelectionCondition` Element in der Elementdefinition.</span><span class="sxs-lookup"><span data-stu-id="6f880-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="6f880-117">Im folgenden Beispiel wird eine auswahlbedingung für ein Element einer Listenansicht angegeben.</span><span class="sxs-lookup"><span data-stu-id="6f880-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="6f880-118">In diesem Beispiel wird das Element verwendet, nur, wenn das Skript, um ausgewertet wird `true`.</span><span class="sxs-lookup"><span data-stu-id="6f880-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="6f880-119">Sie können nur eine Auswahl der Bedingung für ein Element angeben.</span><span class="sxs-lookup"><span data-stu-id="6f880-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="6f880-120">Und die Bedingung angeben muss, einen Eigenschaftennamen oder Skript, um die Bedingung auslösen, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="6f880-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="6f880-121">XML-Elemente</span><span class="sxs-lookup"><span data-stu-id="6f880-121">XML Elements</span></span>

 <span data-ttu-id="6f880-122">Die folgenden XML-Elemente werden verwendet, um eine auswahlbedingung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6f880-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="6f880-123">Geben Sie die folgenden Elemente auswahlbedingungen für Definitionen anzeigen:</span><span class="sxs-lookup"><span data-stu-id="6f880-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="6f880-124">SelectionCondition-Element für EntrySelectedBy für TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="6f880-125">SelectionCondition-Element für EntrySelectedBy für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="6f880-126">SelectionCondition-Element für EntrySelectedBy für WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="6f880-127">SelectionCondition-Element für EntrySelectedBy für CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="6f880-128">Geben Sie die folgenden Elemente Auswahl Bedingungen für allgemeine und Ansicht steuern Definitionen:</span><span class="sxs-lookup"><span data-stu-id="6f880-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="6f880-129">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="6f880-130">SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="6f880-131">Das folgende Element gibt die auswahlbedingung zum Erweitern von Auflistungsobjekten an:</span><span class="sxs-lookup"><span data-stu-id="6f880-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="6f880-132">SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="6f880-133">Das folgende Element gibt die auswahlbedingung für die Anzeige von eine neue Gruppe von Daten an:</span><span class="sxs-lookup"><span data-stu-id="6f880-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="6f880-134">SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="6f880-135">Das folgende Element gibt an, ein Element für eine Listenansicht erfüllt:</span><span class="sxs-lookup"><span data-stu-id="6f880-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="6f880-136">ItemSelectionCondition-Element für den ListItem für ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="6f880-137">Geben Sie die folgenden Elemente erfüllt ein Element für Steuerelemente:</span><span class="sxs-lookup"><span data-stu-id="6f880-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="6f880-138">ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="6f880-139">ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="6f880-140">ItemSelectionCondition-Element für die ExpressionBinding für CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6f880-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="6f880-141">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6f880-141">See Also</span></span>

[<span data-ttu-id="6f880-142">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f880-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
