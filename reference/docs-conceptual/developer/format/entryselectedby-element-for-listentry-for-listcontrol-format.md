---
title: Entryselectedby-Element für ListEntry für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363829"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Element „EntrySelectedBy“ für ListEntry für ListControl (Format)

Definiert die .NET-Typen, die diese Listen Ansichts Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss. In den meisten Fällen ist nur eine Definition für eine Listenansicht erforderlich. Sie können jedoch mehrere Definitionen für die Listenansicht bereitstellen, wenn Sie die gleiche Listenansicht verwenden möchten, um unterschiedliche Daten für unterschiedliche Objekte anzuzeigen.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für ListControl (Format) ListEntry-Element für ListEntry für ListControl (Format) entryselectedby-Element für ListEntry für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Selectioncondition-Element für entryselectedby für ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die für die Verwendung dieser Listen Ansichts Definition vorhanden sein muss.|
|[Selectionsetname-Element für entryselectedby für ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt eine Gruppe von .NET-Typen an, die diese Listen Ansichts Definition verwenden.|
|[Tyname-Element für entryselectedby für ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ an, der diese Listen Ansichts Definition verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ListEntry-Element für ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Definiert, wie die Zeilen der Liste angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für eine Listen Ansichts Definition angeben. Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.

Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt über eine bestimmte Eigenschaft verfügt oder ein bestimmter Eigenschafts Wert oder Skript zu `true` ausgewertet wird. Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für den Fall, dass Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie die-Objekte für eine Listenansicht mithilfe Ihres .net-Typnamens definiert werden.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Weitere Informationen

[ListEntry-Element für ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[Selectioncondition-Element für entryselectedby für ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Selectionsetname-Element für entryselectedby für ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Tyname-Element für entryselectedby für ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
