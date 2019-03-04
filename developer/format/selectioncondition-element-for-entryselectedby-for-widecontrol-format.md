---
title: SelectionCondition-Element für EntrySelectedBy für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854116"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a>Element „SelectionCondition“ für EntrySelectedBy für WideControl (Format)

Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden. Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für eine große Eintrag Definition angegeben werden können.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionCondition-Element für EntrySelectedBy für WideEntry (Format)

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
|[PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Optionales Element.<br /><br /> Gibt die .NET-Eigenschaft, die die Bedingung auslöst.|
|[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt den Skriptblock, der die Bedingung auslöst.|
|[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen, der die Bedingung auslöst.|
|[TypeName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definiert die .NET-Typen, die dieser breiten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.|

## <a name="remarks"></a>Hinweise

Jeder Eintrag Breite benötigen mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert.

Wenn Sie eine auswahlbedingung definieren, gelten die folgenden Anforderungen:

- Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.

- Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.

Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [definieren für Bedingungen, wenn ein Eintrag für die Ansicht oder das Element wird verwendet,](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[EntrySelectedBy-Element für WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[PropertyName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[ScriptBlock-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[TypeName-Element für SelectionCondition für EntrySelectedBy für WideEntry (Format)](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
