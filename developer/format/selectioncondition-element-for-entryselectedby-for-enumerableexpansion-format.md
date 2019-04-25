---
title: SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064134"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a>Element „SelectionCondition“ für EntrySelectedBy für EnumerableExpansion (Format)

Definiert die Bedingung, die vorhanden sein muss, um die Auflistungsobjekte dieser Definition zu erweitern.

Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion-Element (Format) EntrySelectedBy Konfigurationselement für EnumerableExpansion (Format) SelectionCondition-Element für EntrySelectedBy für EnumerableExpansion (Format)

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

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element. Sie müssen angeben, dass eine einzelne `PropertyName` oder `ScriptBlock` Element. Die `SelectionSetName` und `TypeName` Elemente sind optional. Sie können eine der beiden Element angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[PropertyName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Gibt die .NET-Eigenschaft, die die Bedingung auslöst.|
|[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|
|[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen, der die Bedingung auslöst.|
|[TypeName-Element für SelectionCondition für EntrySelectedBy für EnumerableExpansion (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Definiert, welche .NET Sammlung Objekte nach dieser Definition erweitert werden.|

## <a name="remarks"></a>Hinweise

Jede Definition muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.

Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:

- Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.

- Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.

Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für Diplaying Daten](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).

## <a name="see-also"></a>Weitere Informationen

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
