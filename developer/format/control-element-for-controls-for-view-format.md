---
title: Control-Element für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066769"
---
# <a name="control-element-for-controls-for-view--format"></a>Element „Control“ für Controls für View (Format)

Definiert ein Steuerelement, das von der Ansicht und der Name, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.

-Element (Format) ViewDefinitions-Element (Format) Ansicht Konfigurationselement (Format) steuert Elementen (-Format)-Steuerelement für Steuerelemente für die Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Control` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Name-Element für das Steuerelement für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)|Erforderliches Element.<br /><br /> Gibt den Namen des Steuerelements.|
|[CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Erforderliches Element.<br /><br /> Definiert das Steuerelement ab, die von dieser Sicht.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Controls-Element (Format)](./controls-element-for-view-format.md)|Definiert die Steuerelemente, die von einer bestimmten Ansicht verwendet werden können.|

## <a name="remarks"></a>Hinweise

Dieses Steuerelement kann durch die folgenden Elemente angegeben werden:

- [CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [CustomControlName-Element für die ExpressionBinding für GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [CustomControlName-Element für GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Weitere Informationen

[CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[CustomControlName-Element für die ExpressionBinding für Steuerelemente für die Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[CustomControlName-Element für die ExpressionBinding für CustomControl für Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomControlName-Element für die ExpressionBinding für GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[CustomControlName-Element für die ExpressionBinding für GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls-Element (Format)](./controls-element-for-view-format.md)

[Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
