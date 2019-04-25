---
title: EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066242"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a>Element „EntrySelectedBy“ für CustomEntry für Controls für View (Format)

Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)

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
|[SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|
|[SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen, die dieser Definition des Steuerelements verwenden.|
|[TypeName-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format)](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, ein, der dieser Definition des Steuerelements verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Stellt eine Definition des Steuerelements.|

## <a name="remarks"></a>Hinweise

Auswahlbedingungen werden verwendet, um eine Bedingung, die vorhanden sein muss, für die Definition verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder einen bestimmten Eigenschaftswert zu definieren oder Skripts ergibt `true`. Weitere Informationen zu auswahlbedingungen, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
