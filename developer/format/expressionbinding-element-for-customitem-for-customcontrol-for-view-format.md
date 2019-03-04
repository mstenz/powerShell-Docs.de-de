---
title: ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860686"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Element „ExpressionBinding“ für CustomItem für CustomControl für View (Format)

Definiert die Daten, die vom Steuerelement angezeigt wird. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für CustomControl für Ansicht ( CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format)-Format)

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
|[CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.|
|[EnumerateCollection-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Angegeben, dass die Elemente der Auflistungen angezeigt werden.|
|[ItemSelectionCondition-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.|
|[PropertyName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt die .NET-Eigenschaft, deren Wert durch das Steuerelement angezeigt wird.|
|[ScriptBlock-Element für die ExpressionBinding für CustomCustomControl für Ansicht (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert vom Steuerelement angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[EnumerateCollection-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PropertyName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ScriptBlock-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
