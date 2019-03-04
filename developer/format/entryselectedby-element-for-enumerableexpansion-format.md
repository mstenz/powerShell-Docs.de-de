---
title: EntrySelectedBy-Element für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855586"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>Element „EntrySelectedBy“ für EnumerableExpansion (Format)

Definiert die .NET-Typen, die dieser Definition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.

-Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EntrySelectedBy` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.|
|[SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen, mit denen diese Definition, wie die Auflistungsobjekte erweitert werden.|
|[TypeName-Element für EntrySelectedBy für EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der verwendet diese Definition, wie die Auflistungsobjekte erweitert werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EnumerableExpansion-Element (Format)](./enumerableexpansion-element-format.md)|Definiert, wie .NET Datenbanksammlung Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens einen Typ, Auswahlsatz oder auswahlbedingung für einen Definitionseintrag angeben. Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.

Auswahlbedingungen werden verwendet, um eine Bedingung zu definieren, die vorhanden, für die Definition sein muss verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder, der eine bestimmte Eigenschaft-Wert oder ein Skript ergibt, `true`. Weitere Informationen zu auswahlbedingungen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md)

[EnumerableExpansion-Element (Format)](./enumerableexpansion-element-format.md)

[SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[SelectionSetName-Element für EntrySelectedBy für EnumerableExpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[TypeName-Element für EntrySelectedBy für EnumerableExpansion (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
