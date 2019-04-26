---
title: EntrySelectedBy-Element für WideEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066174"
---
# <a name="entryselectedby-element-for-wideentry-format"></a>Element „EntrySelectedBy“ für WideEntry (Format)

Definiert die Typen von .NET, mit denen diese Definition von der breiten Ansicht oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format)

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
|[SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit diese Definition Breite Ansicht verwendet werden.|
|[SelectionSetName-Element für EntrySelectedBy für WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen, die dieser Definition Breite Ansicht verwenden.|
|[TypeName-Element für EntrySelectedBy für WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der diese Breite Ansichtsdefinition verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[WideEntry-Element (Format)](./wideentry-element-for-widecontrol-format.md)|Stellt eine Definition der breiten Ansicht.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens einen Typ, Auswahlsatz oder erfüllt eine Breite Ansicht-Definition angeben. Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.

Auswahlbedingungen werden verwendet, um eine Bedingung zu definieren, die vorhanden, für die Definition sein muss verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder, der einen bestimmten Eigenschaftswert oder das Skriptwert ergibt, `true`. Weitere Informationen zu auswahlbedingungen, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

## <a name="see-also"></a>Weitere Informationen

[WideEntry-Element (Format)](./wideentry-element-for-widecontrol-format.md)

[SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-Element für EntrySelectedBy für WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-Element für EntrySelectedBy für WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
