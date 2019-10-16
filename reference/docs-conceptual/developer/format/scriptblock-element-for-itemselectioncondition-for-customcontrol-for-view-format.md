---
title: ScriptBlock-Element für itemselectioncondition für CustomControl für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362069"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Element „ScriptBlock“ für ItemSeclectionCondition für CustomControl für View (Format)

Gibt das Skript an, das die Bedingung auslöst. Wenn dieses Skript `true` ausgewertet wird, wird die Bedingung erfüllt, und das-Steuerelement wird verwendet. Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für das View (Format)-ExpressionBinding-Element für customItem für CustomControl für View (Format) itemselectioncondition-Element für die Ausdrucks Bindung von CustomControl für View (Format) ScriptBlock-Element für itemselectioncondition für CustomControl für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Itemselectioncondition-Element für die Ausdrucks Bindung für "CustomControl" für "View" (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.|

## <a name="text-value"></a>Textwert

Geben Sie das auszuwertende Skript an.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, können Sie beim Definieren der Auswahlbedingung nicht das [propertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -Element angeben.

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für itemselectioncondition für CustomControl für View (Format)](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[Itemselectioncondition-Element für die Ausdrucks Bindung für "CustomControl" für "View" (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
