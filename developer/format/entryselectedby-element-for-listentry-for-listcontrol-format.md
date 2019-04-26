---
title: EntrySelectedBy-Element für ListEntry für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066191"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a>Element „EntrySelectedBy“ für ListEntry für ListControl (Format)

Definiert .NET Typen, die diese Liste View Definition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. In den meisten Fällen ist nur eine Definition für eine Listenansicht erforderlich. Sie können jedoch mehrere Definitionen für die Listenansicht bereitstellen, sollten Sie die gleiche Listenansicht zu verwenden, um unterschiedliche Daten für verschiedene Objekte anzuzeigen.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListControl (Format) ListEntry-Element für ListEntry für ListControl (Format) EntrySelectedBy-Element für ListEntry für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die für diese Ansicht Listendefinition zu verwendende vorhanden sein muss.|
|[SelectionSetName-Element für EntrySelectedBy für ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen, die diese Ansicht Listendefinition zu verwenden.|
|[TypeName-Element für EntrySelectedBy für ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der diese Liste Sichtdefinition verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListEntry-Element für ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Definiert, wie die Zeilen aus der Liste angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens einen Typ, Auswahlsatz oder auswahlbedingung für eine Sichtdefinition Liste angeben. Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.

Auswahlbedingungen werden verwendet, um eine Bedingung zu definieren, die vorhanden, für die Definition sein muss verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder, der eine bestimmte Eigenschaft-Wert oder ein Skript ergibt, `true`. Weitere Informationen zu auswahlbedingungen, finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie die Objekte für eine Listenansicht mit ihren Typnamen .NET definiert wird.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a>Weitere Informationen

[ListEntry-Element für ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[SelectionCondition-Element für EntrySelectedBy für ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[SelectionSetName-Element für EntrySelectedBy für ListControl (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName-Element für EntrySelectedBy für ListControl (Format)](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
