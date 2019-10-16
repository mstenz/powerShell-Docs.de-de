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
# <a name="defining-selection-sets"></a>Definieren von Auswahlgruppen

Wenn Sie mehrere Ansichten und Steuerelemente erstellen, können Sie Sätze von Objekten definieren, die als Auswahl Sätze bezeichnet werden. Mithilfe eines Auswahl Satzes können Sie die Objekte einmal definieren, ohne Sie für jede Ansicht oder jedes Steuerelement wiederholt definieren zu müssen. Normalerweise werden Auswahl Sätze verwendet, wenn Sie über einen Satz verwandter .NET-Objekte verfügen. Die Formatierungs Datei `FileSystem` (File System. Format. ps1xml) definiert z. b. einen Auswahl Satz der Dateisystemtypen, die von mehreren Ansichten verwendet werden.

## <a name="where-selection-sets-are-defined-and-referenced"></a>Wo Auswahl Sätze definiert sind und referenziert werden

Sie definieren Auswahl Sätze als Teil der allgemeinen Daten, die von allen Sichten und Steuerelementen verwendet werden können, die in der Formatierungs Datei definiert sind. Im folgenden Beispiel wird gezeigt, wie drei Auswahl Sätze definiert werden.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

Auf folgende Weise können Sie auf eine Auswahl festgelegt werden:

- Jede Sicht verfügt über ein `ViewSelectedBy`-Element, das definiert, welche Objekte mithilfe der-Sicht angezeigt werden. Das `ViewSelectedBy`-Element verfügt über ein untergeordnetes `SelectionSetName`-Element, das den Auswahl Satz angibt, der von allen Definitionen der Sicht verwendet wird. Es gibt keine Einschränkung hinsichtlich der Anzahl von Auswahl Sätzen, auf die Sie von einer Ansicht aus verweisen können.

- In jeder Definition einer Sicht oder eines Steuer Elements definiert das `EntrySelectedBy`-Element, welche Objekte mit dieser Definition angezeigt werden. In der Regel verfügt eine Ansicht oder ein Steuerelement nur über eine Definition, sodass die Objekte vom `ViewSelectedBy`-Element definiert werden. Das `EntrySelectedBy`-Element der Definition verfügt über ein untergeordnetes `SelectionSetName`-Element, das den Auswahl Satz angibt. Wenn Sie den Auswahl Satz für eine Definition angeben, können Sie keines der anderen untergeordneten Elemente des `EntrySelectedBy`-Elements angeben.

- In jeder Definition einer Sicht oder eines Steuer Elements kann das `SelectionCondition`-Element verwendet werden, um eine Bedingung für die Verwendung der Definition anzugeben. Das `SelectionCondition`-Element verfügt über ein untergeordnetes `SelectionSetName`-Element, das den Auswahl Satz angibt, der die Bedingung auslöst. Die Bedingung wird ausgelöst, wenn eines der im Auswahl Satz definierten Objekte angezeigt wird. Weitere Informationen zum Festlegen dieser Bedingungen finden Sie unter Definieren von [Bedingungen für den Fall, dass Daten angezeigt](./defining-conditions-for-displaying-data.md)werden.

## <a name="selection-set-example"></a>Beispiel für Auswahl Satz

Das folgende Beispiel zeigt einen Auswahl Satz, der direkt aus der von Windows PowerShell bereitgestellten `FileSystem`-Formatierungs Datei entnommen wird. Weitere Informationen zu anderen Windows PowerShell-Formatierungs Dateien finden Sie unter [Windows PowerShell-Formatierungs Dateien](./powershell-formatting-files.md).

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

Auf den vorherigen Auswahl Satz wird im `ViewSelectedBy`-Element einer Tabellen Sicht verwiesen.

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

 Es gibt keine Beschränkung für die Anzahl der Auswahl Sätze, die Sie definieren können. Die folgenden XML-Elemente werden verwendet, um einen Auswahl Satz zu erstellen.

- Das [selectionsets](./selectionsets-element-format.md) -Element definiert die Sätze von .NET-Objekten, auf die von den Sichten und Steuerelementen der Formatierungs Datei verwiesen wird.

- Das [SelectionSet](./selectionset-element-format.md) -Element definiert einen einzelnen Satz von .NET-Objekten.

- Das [Name](./name-element-for-selectionset-format.md) -Element gibt den Namen an, der verwendet wird, um auf den Auswahl Satz zu verweisen.

- Das [types](./types-element-for-selectionset-format.md) -Element gibt die .NET-Typen der Objekte des Auswahl Satzes an. (In Formatierungs Dateien werden Objekte durch ihren .NET-Typ angegeben.)

 Die folgenden XML-Elemente werden verwendet, um einen Auswahl Satz anzugeben.

- Das folgende Element gibt den Auswahl Satz an, der in allen Definitionen der Sicht verwendet werden soll:

    - [Selectionsetname-Element für viewselectedby (Format)](./selectionsetname-element-for-viewselectedby-format.md)

    - [Selectionsetname-Element für entryselectedby für GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- Die folgenden Elemente geben den Auswahl Satz an, der von einer einzelnen Sicht Definition verwendet wird:

    - [Selectionsetname-Element für entryselectedby für ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [Selectionsetname-Element für entryselectedby für tablecontrol (Format)](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [Selectionsetname-Element für entryselectedby für widecontrol (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [Selectionsetname-Element für entryselectedby für CustomControl für Ansicht (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- Die folgenden Elemente geben den Auswahl Satz an, der von Common-und View-Steuerelement Definitionen verwendet wird:

    - [Selectionsetname-Element für entryselectedby für Steuerelemente für View (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [Selectionsetname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- Die folgenden Elemente geben den Auswahl Satz an, der verwendet wird, wenn Sie definieren, welches Objekt erweitert werden soll:

    - [Selectionsetname-Element für entryselectedby für enumerableexpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- Die folgenden Elemente geben den Auswahl Satz an, der von Auswahl Bedingungen verwendet wird.

    - [Selectionsetname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [Selectionsetname-Element für selectioncondition für Steuerelemente für View (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [Selectionsetname-Element für selectioncondition für CustomControl für Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [Selectionsetname-Element für selectioncondition für entryselectedby für enumerableweiterung (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [Selectionsetname-Element für selectioncondition für entryselectedby für ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [Selectionsetname-Element für selectioncondition für entryselectedby für tablecontrol (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [Selectionsetname-Element für selectioncondition für entryselectedby für wideentry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [Selectionsetname-Element für selectioncondition für GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>Weitere Informationen

[Selectionsets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[Benennen](./name-element-for-selectionset-format.md)

[Solche](./types-element-for-selectionset-format.md)

[PowerShell-Formatierungs Dateien](./powershell-formatting-files.md)

[Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md)

[Schreiben einer PowerShell-Formatierungs-und-Typen Datei](./writing-a-powershell-formatting-file.md)
