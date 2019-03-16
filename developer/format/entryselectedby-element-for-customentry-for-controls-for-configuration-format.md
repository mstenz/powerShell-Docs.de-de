---
title: EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059217"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Element „EntrySelectedBy“ für CustomEntry für Controls für Configuration (Format)

Definiert die Typen von .NET, mit denen die Definition eines allgemeinen Steuerelement oder die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für die Konfiguration (Format)-Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
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
|[SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, für die allgemeine Steuerelementdefinition verwendet werden.|
|[SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen, die dieser Definition des allgemeinen Steuerelements verwenden.|
|[TypeName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, ein, der dieser Definition des allgemeinen Steuerelements verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Stellt eine Definition des allgemeinen-Steuerelements.|

## <a name="remarks"></a>Hinweise

Zumindest muss jede Definition mindestens .NET Typ, Auswahlsatz, oder auswahlbedingung angegeben sein. Es ist nicht begrenzt auf die Anzahl der Typen, legt der Auswahl oder auswahlbedingungen, die Sie angeben können.

## <a name="see-also"></a>Weitere Informationen

[SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[SelectionSetName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[TypeName-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
