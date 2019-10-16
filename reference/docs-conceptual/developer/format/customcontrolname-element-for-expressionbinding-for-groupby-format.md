---
title: Customcontrolname-Element für ExpressionBinding für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368909"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>Element „CustomControlName“ für ExpressionBinding für GroupBy (Format)

Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an. Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) ExpressionBinding-Element für customItem für GroupBy (Format) customcontrolname-Element für ExpressionBinding für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomControlName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element für customItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definiert die Daten, die vom-Steuerelement angezeigt werden.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Steuer Elements an.

## <a name="remarks"></a>Hinweise

Sie können allgemeine Steuerelemente erstellen, die von allen Ansichten einer Formatierungs Datei verwendet werden können, und Sie können Ansichts Steuerelemente erstellen, die von einer bestimmten Ansicht verwendet werden können. Die folgenden Elemente geben die Namen dieser Steuerelemente an:

- [Name-Element für Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-Element für Steuerelemente für Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[Name-Element für Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-Element für Steuerelemente für Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-Element für customItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
