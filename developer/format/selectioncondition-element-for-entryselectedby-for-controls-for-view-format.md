---
title: SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064230"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a>Element „SelectionCondition“ für EntrySelectedBy für Controls für View (Format)

Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für Steuerelemente für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für Steuerelemente für Ansicht) -Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[PropertyName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt eine .NET-Eigenschaft, die die Bedingung auslöst.|
|[ScriptBlock-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|
|[SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen, der die Bedingung auslöst.|
|[TypeName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|

## <a name="remarks"></a>Hinweise

Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:

- Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.

- Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.

Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[ScriptBlock-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[SelectionSetName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[TypeName-Element für SelectionCondition für Steuerelemente für die Ansicht (Format)](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
