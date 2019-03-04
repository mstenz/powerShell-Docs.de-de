---
title: ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7031fa8b-3e2b-4ea8-89cb-95171f467b5a
caps.latest.revision: 6
ms.openlocfilehash: e55d1c5aa533005b258ecbbbf3ed9d55f852eab6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857416"
---
# <a name="scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format"></a>Element „ScriptBlock“ für SelectionCondition für CustomControl für View (Format)

Gibt das Skript an, das die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und die Definition verwendet. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für CustomControl für Ansicht ( CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)-ScriptBlock-Element für SelectionCondition für CustomControl für Ansicht (Format)-Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.|

## <a name="text-value"></a>Textwert

Geben Sie das Skript aus, das ausgewertet wird.

## <a name="remarks"></a>Hinweise

Die auswahlbedingung muss einen angeben mindestens ein Skript oder eine Eigenschaft zu evaluieren, aber nicht beide angeben. Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[SelectionCondition-Element für EntrySelectedBy für CustomControl für Ansicht (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
