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
# <a name="defining-conditions-for-displaying-data"></a>Definieren von Bedingungen für die Datenanzeige

Wenn Sie definieren, welche Daten von einer Ansicht oder einem Steuerelement angezeigt werden, können Sie eine Bedingung angeben, die vorhanden sein muss, damit die Daten angezeigt werden. Die Bedingung kann durch eine bestimmte Eigenschaft ausgelöst werden, oder wenn ein Skript oder ein Eigenschafts Wert als `true` ausgewertet wird. Wenn die Auswahlbedingung erfüllt ist, wird die Definition der Ansicht bzw. des Steuer Elements verwendet.

## <a name="specifying-a-selection-condition-for-a-definition"></a>Angeben einer Auswahlbedingung für eine Definition

Wenn eine Definition für eine Sicht oder ein Steuerelement erstellt wird, wird das `EntrySelectedBy`-Element verwendet, um anzugeben, welche Objekte die Definition verwenden, oder welche Bedingung für die zu verwendende Definition vorhanden sein muss. Die Bedingung wird durch das `SelectionCondition`-Element angegeben.

Im folgenden Beispiel wird eine Auswahlbedingung für eine Definition einer Tabellenansicht angegeben. In diesem Beispiel wird die Definition nur verwendet, wenn das angegebene Skript `true` ausgewertet wird.

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

Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die Sie für die Definition einer Sicht oder eines Steuer Elements angeben können. Die einzigen Anforderungen sind die folgenden:

- Die Auswahlbedingung muss einen Eigenschaftsnamen oder ein Skript angeben, um die Bedingung zu initiieren, kann jedoch nicht beides angeben.

- Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.

## <a name="specifying-a-selection-condition-for-an-item"></a>Angeben einer Auswahlbedingung für ein Element

Sie können auch angeben, wann ein Element einer Listenansicht oder eines Steuer Elements verwendet wird, indem Sie das `ItemSelectionCondition`-Element in die Element Definition einschließen. Im folgenden Beispiel wird eine Auswahlbedingung für ein Element einer Listenansicht angegeben. In diesem Beispiel wird das Element nur verwendet, wenn das Skript `true` ausgewertet wird.

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

Sie können nur eine Auswahlbedingung für ein Element angeben. Und die Bedingung muss einen Eigenschaftsnamen oder ein Skript angeben, um die Bedingung zu initiieren, kann jedoch nicht beides angeben.

## <a name="xml-elements"></a>XML-Elemente

 Die folgenden XML-Elemente werden verwendet, um eine Auswahlbedingung zu erstellen.

- Die folgenden Elemente geben Auswahl Bedingungen für Sicht Definitionen an:

    - [Selectioncondition-Element für entryselectedby für tablecontrol (Format)](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Selectioncondition-Element für entryselectedby für ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [Selectioncondition-Element für entryselectedby für widecontrol (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [Selectioncondition-Element für entryselectedby für CustomControl (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- Die folgenden Elemente geben Auswahl Bedingungen für allgemeine und Ansicht-Steuerelement Definitionen an:

    - [Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- Mit dem folgenden Element wird die Auswahlbedingung zum Erweitern von Auflistungs Objekten angegeben:

    - [Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Das folgende Element gibt die Auswahlbedingung zum Anzeigen einer neuen Gruppe von Daten an:

    - [Selectioncondition-Element für entryselectedby für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- Das folgende Element gibt eine Elementauswahl Bedingung für eine Listenansicht an:

    - [Itemselectioncondition-Element für ListItem für ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- Die folgenden Elemente geben eine Elementauswahl Bedingung für-Steuerelemente an:

    - [Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [Itemselectioncondition-Element für ExpressionBinding für CustomControl (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
