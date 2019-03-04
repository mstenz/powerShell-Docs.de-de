---
title: ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853136"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>Element „ItemSelectionCondition“ für ExpressionBinding für GroupBy (Format)

Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss. Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für ein Steuerelement ein Element angegeben werden können. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format) ExpressionBinding-Element für CustomItem für GroupBy (Format) ItemSelectionCondition-Element für die ExpressionBinding für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ItemSelectionCondition` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[PropertyName-Element für ItemSelectionCondition für GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt die .NET-Eigenschaft, die die Bedingung auslöst.|
|[ScriptBlock-Element für ItemSelectionCondition für GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ExpressionBinding-Element für CustomItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definiert die Daten, die vom Steuerelement angezeigt wird.|

## <a name="remarks"></a>Hinweise

Sie können einen Eigenschaftennamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-Element für CustomItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
