---
title: PropertyName-Element für ItemSelectionCondition für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855536"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a>Element „PropertyName“ für ItemSeclectionCondition für ListControl (Format)

Gibt die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung erfüllt ist und die Ansicht wird verwendet. Dieses Element wird verwendet, wenn Sie eine Ansicht zu definieren.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries-Element (Format) ListEntry Konfigurationselement für ListItems-Element für ListEntry für ListControl (Format) ListItem ListControl (Format) -Element für ListItems für ListControl (Format) ItemSelectionCondition-Element für ListItem für ListControls PropertyName-Element für ItemSelectionCondition für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente der `PropertyName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ItemSelectionCondition-Element für den ListItem für ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a>Textwert

Geben Sie den Namen der Eigenschaft, deren Wert angezeigt wird.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, Sie können nicht angeben, die ["scriptblock"](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) -Element, wenn die auswahlbedingung zu definieren.

## <a name="see-also"></a>Weitere Informationen

[ScriptBlock-Element für ItemSelectionCondition für ListIControl (Format)](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[ItemSelectionCondition-Element für den ListItem für ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
