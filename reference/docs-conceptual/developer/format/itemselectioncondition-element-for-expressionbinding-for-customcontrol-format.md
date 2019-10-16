---
title: Itemselectioncondition-Element für ExpressionBinding für CustomControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362909"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a>Element „ItemSelectionCondition“ für ExpressionBinding für CustomControl (Format)

Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss. Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die für ein Steuerelement angegeben werden können. Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für das View (Format)-ExpressionBinding-Element für customItem für CustomControl für View (Format) itemselectioncondition-Element für die Ausdrucks Bindung von CustomControl für View (Format)

## <a name="syntax"></a>Syntax

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ItemSelectionCondition`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[PropertyName-Element für itemselectioncondition für CustomControl für View (Format](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt die .net-Eigenschaft an, die die Bedingung auslöst.|
|[ScriptBlock-Element für itemselectioncondition für CustomControl für View (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element für customItem für CustomControl für View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Definiert die Daten, die vom-Steuerelement angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie können einen Eigenschaftsnamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-Element für customItem für CustomControl für View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
