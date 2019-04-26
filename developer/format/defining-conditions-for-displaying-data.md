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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066327"
---
# <a name="defining-conditions-for-displaying-data"></a>Definieren von Bedingungen für die Datenanzeige

Beim definieren, welche Daten von einer Sicht oder ein Steuerelement angezeigt werden, können Sie eine Bedingung angeben, die vorhanden sein muss, bis die Daten angezeigt werden soll. Die Bedingung kann ausgelöst werden, durch eine bestimmte Eigenschaft oder ein Skript oder Eigenschaftswert ergibt `true`. Wenn die auswahlbedingung erfüllt ist, wird die Definition der Sicht oder Steuerelement verwendet.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Angeben einer Auswahlbedingung eine für die Definition eines

Beim Erstellen einer Definition für eine Sicht oder ein Steuerelement, das `EntrySelectedBy` Element verwendet, um anzugeben, welche Objekte verwenden, werden die Definition oder welcher Bedingung vorhanden sein muss, für die Definition verwendet werden. Die Bedingung wird angegeben, indem die `SelectionCondition` Element.

Im folgenden Beispiel wird eine auswahlbedingung für eine Definition einer Tabellenansicht angegeben. In diesem Beispiel wird die Definition verwendet, nur, wenn das angegebene Skript Auswertung `true`.

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

Es gibt keine Beschränkung für die Anzahl der von auswahlbedingungen, die Sie eine Definition für eine Sicht für oder Kontrolle angeben können. Die einzige Voraussetzung ist Folgendes:

- Die auswahlbedingung muss angeben, einen Eigenschaftennamen oder Skript, um die Bedingung auslösen, aber nicht beides angeben.

- Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.

## <a name="specifying-a-selection-condition-for-an-item"></a>Eine Auswahlbedingung für ein Element angeben

Sie können auch angeben, wenn ein Element eines Listenansicht oder eines Steuerelements verwendet wird, durch Einschließen der `ItemSelectionCondition` Element in der Elementdefinition. Im folgenden Beispiel wird eine auswahlbedingung für ein Element einer Listenansicht angegeben. In diesem Beispiel wird das Element verwendet, nur, wenn das Skript, um ausgewertet wird `true`.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Sie können nur eine Auswahl der Bedingung für ein Element angeben. Und die Bedingung angeben muss, einen Eigenschaftennamen oder Skript, um die Bedingung auslösen, aber nicht beides angeben.

## <a name="xml-elements"></a>XML-Elemente

 Die folgenden XML-Elemente werden verwendet, um eine auswahlbedingung zu erstellen.

- Geben Sie die folgenden Elemente auswahlbedingungen für Definitionen anzeigen:

    - [SelectionCondition-Element für EntrySelectedBy für TableControl (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionCondition-Element für EntrySelectedBy für ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionCondition-Element für EntrySelectedBy für WideControl (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionCondition-Element für EntrySelectedBy für CustomControl (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Geben Sie die folgenden Elemente Auswahl Bedingungen für allgemeine und Ansicht steuern Definitionen:

    - [SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Das folgende Element gibt die auswahlbedingung zum Erweitern von Auflistungsobjekten an:

    - [SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Das folgende Element gibt die auswahlbedingung für die Anzeige von eine neue Gruppe von Daten an:

    - [SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Das folgende Element gibt an, ein Element für eine Listenansicht erfüllt:

    - [ItemSelectionCondition-Element für den ListItem für ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Geben Sie die folgenden Elemente erfüllt ein Element für Steuerelemente:

    - [ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [ItemSelectionCondition-Element für die ExpressionBinding für CustomControl (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
