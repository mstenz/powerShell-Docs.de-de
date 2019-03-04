---
title: EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859586"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Element „EntrySelectedBy“ für CustomEntry für CustomControl für View (Format)

Definiert die .NET-Typen, die dieser benutzerdefinierten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) EntrySelectedBy -Element für CustomEntry für Ansicht (Format)

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
|[SelectionCondition-Element für EntrySelectedBy für CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|
|[SelectionSetName-Element für EntrySelectedBy für CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen, die dieser Definition der Ansicht des Steuerelement zu verwenden.|
|[TypeName-Element für EntrySelectedBy für CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, ein, der dieser Definition der Ansicht des Steuerelement verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomEntries für Ansicht (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Definiert die Steuerelemente, die von bestimmten .NET Objekten verwendet wird.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens einen Typ, Auswahlsatz oder auswahlbedingung nach einem Eintrag angeben. Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die Sie verwenden können.

Auswahlbedingungen werden verwendet, um eine Bedingung, die vorhanden sein muss, für den Eintrag, der verwendet werden, z. B. wenn ein Objekt eine bestimmte Eigenschaft hat, oder einen bestimmten Eigenschaftswert zu definieren oder Skripts ergibt `true`. Weitere Informationen zu auswahlbedingungen, finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu den Komponenten einer Ansicht des benutzerdefinierten Steuerelements finden Sie unter [benutzerdefinierte Ansicht des Steuerelement](./creating-custom-controls.md).

## <a name="see-also"></a>Weitere Informationen

[SelectionCondition-Element für EntrySelectedBy für CustomEntry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[SelectionSetName-Element für EntrySelectedBy für CustomEntry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[TypeName-Element für EntrySelectedBy für CustomEntry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[CustomEntry-Element für CustomEntries für Ansicht (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Benutzerdefiniertes Steuerelement anzeigen](./creating-custom-controls.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
