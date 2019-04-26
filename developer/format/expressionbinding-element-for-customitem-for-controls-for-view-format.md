---
title: ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065945"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Element „ExpressionBinding“ für CustomItem für Controls für View (Format)

Definiert die Daten, die vom Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für Ansicht (Format) ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ExpressionBinding` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|`CustomControl Element`|Optionales Element.<br /><br /> Definiert ein Steuerelement, das von diesem Steuerelement verwendet wird.|
|[CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.|
|[EnumerateCollection-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, dass die Elemente der Auflistungen angezeigt werden.|
|[ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.|
|[PropertyName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt die .NET-Eigenschaft, deren Wert durch das Steuerelement angezeigt wird.|
|[ScriptBlock-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert vom Steuerelement angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[EnumerateCollection-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[ItemSelectionCondition-Element des ExpressionBinding für Steuerelemente für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PropertyName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[ScriptBlock-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
