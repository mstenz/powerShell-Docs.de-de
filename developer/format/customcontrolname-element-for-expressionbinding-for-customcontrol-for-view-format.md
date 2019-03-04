---
title: CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860436"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>Element „CustomControlName“ für ExpressionBinding für CustomControl für View (Format)

Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem -Element für CustomEntry für Ansicht (Format) ExpressionBinding-Element für CustomItem (Format) CustomControlName-Element für Ausdrucksbindung für CustomItem (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomControlName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ExpressionBinding-Element für CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definiert die Daten, die vom Steuerelement angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Steuerelements.

## <a name="remarks"></a>Hinweise

Sie können allgemeine Steuerelemente, die von allen Ansichten des eine Formatierungsdatei verwendet werden können erstellen aus, und Sie können Steuerelemente, die von einer bestimmten Ansicht verwendet werden können erstellen. Die Namen dieser Steuerelemente werden durch die folgenden Elemente angegeben.

- [Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-Element für CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
