---
title: SelectionCondition-Element für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7649d5d0-2b56-49b5-a670-dde46caca343
caps.latest.revision: 11
ms.openlocfilehash: f04a07c241268566eaedfe2b299c33d5be4dc19d
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735090"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a>Element „SelectionCondition“ für EntrySelectedBy für ListControl (Format)

Definiert die Bedingung, die vorhanden sein muss, um diese Definition der Listenansicht zu verwenden. Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für eine Listendefinition angegeben werden können.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für ListEntry (Format) SelectionCondition-Element für EntrySelectedBy für ListEntry (Format)

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

### <a name="attributes"></a>Attribute

Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[PropertyName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt die .NET-Eigenschaft, die die Bedingung auslöst.|
|[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|
|[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen, die die Bedingung auslösen.|
|[TypeName-Element für SelectionCondition für EntrySelectedBy für ListEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für TableRowEntry (Format)](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|Definiert die .NET-Typen, die diesen Tabelleneintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.|

## <a name="remarks"></a>Hinweise

lWhen, die Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:

- Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.

- Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.

Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu anderen Komponenten einer Listenansicht, finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[ListEntry-Element (Format)](./listentry-element-for-listcontrol-format.md)

[SelectionSetName-Element für EntrySelectedBy für ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[TypeName-Element für EntrySelectedBy für ListEntry (Format)](/powershell/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
