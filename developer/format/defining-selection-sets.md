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
# <a name="defining-selection-sets"></a>Definieren von Auswahlgruppen

Wenn Sie mehrere Ansichten und Steuerelementen zu erstellen, können Sie Gruppen von Objekten, die auf die verwiesen werden, als Auswahl legt definieren. Ein Auswahlsatz können Sie die Objekte einmal definieren, ohne dass sie wiederholt für jede Sicht oder ein Steuerelement definieren. Auswahl legt werden in der Regel verwendet, wenn Sie einen Satz von verknüpften Objekten für .NET verfügen. Z. B. die `FileSystem` Formatierungsdatei (FileSystem.format.ps1xml) definiert einen Auswahlsatz das System der Typen von Dateien, die mehrere Ansichten verwenden.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Wo sind Auswahl definiert und auf die verwiesen wird

Sie definieren die Auswahl legt als Teil der allgemeinen Daten, die von den Ansichten und Steuerelemente, die in die Formatierungsdatei verwendet werden können. Das folgende Beispiel zeigt, wie drei Sätze der Auswahl definiert wird.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Sie können eine Auswahl verweisen legt fest, es gibt folgende Möglichkeiten:

- Jede Ansicht hat eine `ViewSelectedBy` -Element, das definiert, welche Objekte mithilfe der Sicht angezeigt werden. Die `ViewSelectedBy` Element verfügt über eine `SelectionSetName` untergeordnetes Element, das die Auswahl gibt an, die festlegen, die alle Definitionen zur Verwendung anzeigen. Es gibt keine Einschränkung für die Anzahl der Auswahl-Sätze, die Sie aus einer Sicht verweisen können.

- In jeder Definition einer Ansicht oder das Steuerelement das `EntrySelectedBy` -Element definiert, welche Objekte über dieser Definition angezeigt werden. In der Regel eine Sicht für oder Kontrolle hat nur eine Definition, damit die Objekte, indem definiert sind die `ViewSelectedBy` Element. Die `EntrySelectedBy` Element der Definition verfügt über eine `SelectionSetName` untergeordnetes Element, das die Auswahl festlegt. Wenn Sie die Auswahl, legen Sie für die Definition eines angeben, können nicht Sie keines der anderen untergeordneten Elementen angeben der `EntrySelectedBy` Element.

- In jeder Definition einer Ansicht oder das Steuerelement das `SelectionCondition` Element kann verwendet werden, um für die bei der Definition verwendet wird, eine Bedingung angeben. Die `SelectionCondition` Element verfügt über eine `SelectionSetName` untergeordneten-Element, das angibt, die Auswahl festgelegt wird, löst die Bedingung. Die Bedingung wird immer dann ausgelöst, wenn eines der Objekte, die definiert, in der Auswahl angezeigt werden. Weitere Informationen zum Festlegen dieser Bedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

## <a name="selection-set-example"></a>Auswahl & ndash; Beispiel

Das folgende Beispiel zeigt eine Auswahl-Gruppe, die direkt aus der `FileSystem` Formatierung der Datei, die von Windows PowerShell bereitgestellt. Weitere Informationen zu anderen Windows PowerShell-Formatierungsdateien, finden Sie unter [Formatieren von Windows PowerShell-Dateien](./powershell-formatting-files.md).

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

Die vorherige Auswahl Gruppe verwiesen wird, der `ViewSelectedBy` Element einer Tabellenansicht.

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

## <a name="xml-elements"></a>XML-Elemente

 Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die Sie definieren können. Die folgende XML-Elemente werden verwendet, um einen Auswahlsatz zu erstellen.

- Die [SelectionSets](./selectionsets-element-format.md) -Element definiert, die Sätze von .NET-Objekten, die von den Sichten verwiesen werden und die Steuerelemente die Formatierungsdatei.

- Die [SelectionSet](./selectionset-element-format.md) Element definiert einen Satz von .NET-Objekten.

- Die [Namen](./name-element-for-selectionset-format.md) Element gibt den Namen, die auf der Auswahlsatz verwendet wird.

- Die [Typen](./types-element-for-selectionset-format.md) Element gibt die .NET Typen der Objekte des Satzes Auswahl. (In Formatierungsdateien, werden Objekte anhand ihres Typs .NET angegeben.)

 Die folgende XML-Elemente werden verwendet, um einen Auswahlsatz anzugeben.

- Das folgende Element gibt an, die Auswahl, in der Ansicht alle Definitionen verwenden:

    - [SelectionSetName-Element für ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

    - [SelectionSetName-Element für EntrySelectedBy für GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Die folgenden Elemente angeben die Auswahlsatz definitionsgemäß eine einzelne Ansicht verwendet:

    - [SelectionSetName-Element für EntrySelectedBy für ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [SelectionSetName-Element für EntrySelectedBy für TableControl (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName-Element für EntrySelectedBy für WideControl (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [SelectionSetName-Element für EntrySelectedBy für CustomControl für Ansicht (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Die folgenden Elemente angeben, die Auswahlsatz von allgemeinen verwendet und Steuerelementdefinitionen anzeigen:

    - [SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Die folgenden Elemente angeben, den Auswahlsatz verwendet, wenn Sie, welches Objekt definieren zu erweitern:

    - [SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Die folgenden Elemente angeben die Auswahlsatz von auswahlbedingungen verwendet.

    - [SelectionSetName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [SelectionSetName-Element für SelectionCondition für CustomControl für Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [SelectionSetName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [SelectionSetName-Element für SelectionCondition für EntrySelectedBy für TableControl (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [SelectionSetName-Element für SelectionCondition für GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Weitere Informationen

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Name](./name-element-for-selectionset-format.md)

[Typen](./types-element-for-selectionset-format.md)

[Formatieren von PowerShell-Dateien](./powershell-formatting-files.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[Schreiben eine PowerShell-Formatierung und Typendatei](./writing-a-powershell-formatting-file.md)
