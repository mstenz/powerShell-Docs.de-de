---
title: CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066650"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a>Element „CustomControlName“ für ExpressionBinding für Controls für View (Format)

Gibt den Namen eines allgemeinen Steuerelements oder einem Steuerelement an. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für Ansicht (Format) ExpressionBinding-Element für CustomItem für Steuerelemente für Ansicht (Format) CustomControlName -Element für ExpressionBindine für Steuerelemente für die Ansicht (Format)

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
|[ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Definiert die Daten, die vom Steuerelement angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Steuerelements.

## <a name="remarks"></a>Hinweise

Sie können allgemeine Steuerelemente, die von allen Ansichten des eine Formatierungsdatei verwendet werden können erstellen und Sie können Steuerelemente, die von einer bestimmten Ansicht verwendet werden können erstellen. Die folgenden Elemente geben Sie die Namen dieser Steuerelemente:

- [Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
