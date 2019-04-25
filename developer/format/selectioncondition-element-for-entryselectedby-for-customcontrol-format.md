---
title: SelectionCondition-Element für EntrySelectedBy für CustomControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075748"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a>Element „SelectionCondition“ für EntrySelectedBy für CustomControl (Format)

Definiert eine Bedingung, die für die Steuerelementdefinition eines zu verwendenden vorhanden sein muss. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für CustomControl für Ansicht ( CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)-Format)

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
|[PropertyName-Element für SelectionCondition für CustomControl für Ansicht (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt eine .NET-Eigenschaft, die die Bedingung auslöst.|
|[ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|
|[SelectionSetName-Element für SelectionCondition für benutzerdefiniertes Steuerelement für die Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen, der die Bedingung auslöst.|
|[TypeName-Element für SelectionCondition für CustomControl für Ansicht (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|

## <a name="remarks"></a>Hinweise

Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:

- Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.

- Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.

Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für SelectionCondition für CustomControl für Ansicht (Format)](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[SelectionSetName-Element für SelectionCondition für benutzerdefiniertes Steuerelement für die Ansicht (Format)](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[TypeName-Element für SelectionCondition für CustomControl für Ansicht (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[EntrySelectedBy-Element für CustomEntry für CustomControl für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
