---
title: PropertyName-Element für ItemSelectionCondition für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 221cbdc2-f794-4f3a-9d40-bfdd8cba1013
caps.latest.revision: 6
ms.openlocfilehash: aae65789cf5572cbcc9251eca802a2d43065e49f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064763"
---
# <a name="propertyname-element-for-itemselectioncondition-for-groupby-format"></a>Element „PropertyName“ für ItemSeclectionCondition für GroupBy (Format)

Gibt die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format) ExpressionBinding-Element für CustomItem für GroupBy (Format) ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)-PropertyName-Element für ItemSelectionCondition für GroupBy (Format)

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
|[ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der .NET-Eigenschaft, die die Bedingung auslöst.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, Sie können nicht angeben, die ["scriptblock"](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md) -Element, wenn die auswahlbedingung zu definieren.

## <a name="see-also"></a>Weitere Informationen

[ScriptBlock-Element für ItemSelectionCondition für GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)

[ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
