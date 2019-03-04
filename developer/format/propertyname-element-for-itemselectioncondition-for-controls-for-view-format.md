---
title: PropertyName-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857626"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>Element „PropertyName“ für ItemSeclectionCondition für Controls für View (Format)

Gibt die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für Ansicht (Format) ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format) ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für Ansicht (Format)-PropertyName-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der .NET-Eigenschaft, die die Bedingung auslöst.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, Sie können nicht angeben, die ["scriptblock"](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -Element, wenn die auswahlbedingung zu definieren.

## <a name="see-also"></a>Weitere Informationen

[ScriptBlock-Element für ItemSelectionCondition für Steuerelemente für die Ansicht (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
