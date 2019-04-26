---
title: EntrySelectedBy-Element für CustomEntry für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066225"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>Element „EntrySelectedBy“ für CustomEntry für GroupBy (Format)

Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `EntrySelectedBy` Element. Sie müssen mindestens einen Typ, Auswahlsatz oder der auswahlbedingung für die Definition eines angeben. Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|
|[SelectionSetName-Element für EntrySelectedBy für GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen, die dieser Definition des Steuerelements verwenden.|
|[TypeName-Element für EntrySelectedBy für GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, ein, der dieser Definition des Steuerelements verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomControl für GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Stellt eine Definition des Steuerelements.|

## <a name="remarks"></a>Hinweise

Auswahlbedingungen werden verwendet, um eine Bedingung, die vorhanden sein muss, für die Definition verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder einen bestimmten Eigenschaftswert zu definieren oder Skripts ergibt `true`. Weitere Informationen zu auswahlbedingungen, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[SelectionSetName-Element für EntrySelectedBy für GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[TypeName-Element für EntrySelectedBy für GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)

[CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
