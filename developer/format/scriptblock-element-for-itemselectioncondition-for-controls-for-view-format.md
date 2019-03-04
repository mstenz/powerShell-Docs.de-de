---
title: ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856736"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a>Element „ScriptBlock“ für ItemSeclectionCondition für Controls für View (Format)

Gibt das Skript an, das die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für Ansicht (Format) ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format) ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für Ansicht (Format)-ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)

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
|[ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie das Skript aus, das ausgewertet wird.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, Sie können nicht angeben, die [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) -Element, wenn die auswahlbedingung zu definieren.

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
