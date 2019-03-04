---
title: ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855136"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Element „ExpressionBinding“ für CustomItem für Controls für Configuration (Format)

Definiert die Daten, die vom Steuerelement angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) CustomItem Konfigurationselement für CustomEntry für Steuerelemente für die ExpressionBinding-Konfigurationselement für CustomItem für Steuerelemente für die Konfiguration (Format)-Format)

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
|[CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an.|
|[EnumerateCollection-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Angegeben, dass die Elemente der Auflistungen, die vom Steuerelement angezeigt werden.|
|[ItemSelectionCondition-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die für dieses allgemeinen Steuerelement zu verwendende vorhanden sein muss.|
|[PropertyName-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt die .NET-Eigenschaft, deren Wert durch das allgemeine Steuerelement angezeigt wird.|
|[ScriptBlock-Element für die ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert durch das allgemeine Steuerelement angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
