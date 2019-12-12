---
title: Control-Element für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363469"
---
# <a name="control-element-for-controls-for-view--format"></a>Element „Control“ für Controls für View (Format)

Definiert ein Steuerelement, das von der Ansicht verwendet werden kann, und den Namen, der verwendet wird, um auf das Steuerelement zu verweisen.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement für Steuerelemente für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Control`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Name-Element für das Steuer Element für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)|Erforderliches Element.<br /><br /> Gibt den Namen des Steuer Elements an.|
|[CustomControl-Element für Steuerelemente für Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Erforderliches Element.<br /><br /> Definiert das Steuerelement, das von dieser Ansicht verwendet wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Controls-Element (Format)](./controls-element-for-view-format.md)|Definiert die Sicht Steuerelemente, die von einer bestimmten Ansicht verwendet werden können.|

## <a name="remarks"></a>Hinweise

Dieses Steuerelement kann durch die folgenden Elemente angegeben werden:

- [Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [Customcontrolname-Element für ExpressionBinding für CustomControl für View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [Customcontrolname-Element für ExpressionBinding für GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [Customcontrolname-Element für GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a>Weitere Informationen

[CustomControl-Element für Steuerelemente für Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Customcontrolname-Element für ExpressionBinding für CustomControl für View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Customcontrolname-Element für ExpressionBinding für GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Customcontrolname-Element für ExpressionBinding für GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Controls-Element (Format)](./controls-element-for-view-format.md)

[Name-Element für Steuerelemente für Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
