---
title: SelectionCondition-Element für EntrySelectedBy für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075714"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a>Element „SelectionCondition“ für EntrySelectedBy für GroupBy (Format)

Definiert eine Bedingung, die für die Steuerelementdefinition eines zu verwendenden vorhanden sein muss. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) EntrySelectedBy-Element für CustomEntry für GroupBy (Format) SelectionCondition-Element für EntrySelectedBy für GroupBy (Format)

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
|[PropertyName-Element für SelectionCondition für GroupBy (Format)](./propertyname-element-for-selectioncondition-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt eine .NET-Eigenschaft, die die Bedingung auslöst.|
|[ScriptBlock-Element für SelectionCondition für GroupBy (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|
|[SelectionSetName-Element für SelectionCondition für GroupBy (Format)](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen, der die Bedingung auslöst.|
|[TypeName-Element für SelectionCondition für GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für CustomEntry für GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|

## <a name="remarks"></a>Hinweise

Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:

- Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.

- Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.

Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für SelectionCondition für CustomControl für Ansicht (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName-Element für SelectionCondition für benutzerdefiniertes Steuerelement für die Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[TypeName-Element für SelectionCondition für GroupBy (Format)](./typename-element-for-selectioncondition-for-groupby-format.md)

[EntrySelectedBy-Element für CustomEntry für GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
