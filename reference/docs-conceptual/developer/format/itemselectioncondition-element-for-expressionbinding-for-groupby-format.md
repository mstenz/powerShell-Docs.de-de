---
title: Itemselectioncondition-Element für ExpressionBinding für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6af3be7d-921e-4cf7-bd5a-d87aa0b4efbd
caps.latest.revision: 7
ms.openlocfilehash: b2b0a0d1996392614807e08b820a72978e38a0cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365289"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-groupby-format"></a>Element „ItemSelectionCondition“ für ExpressionBinding für GroupBy (Format)

Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss. Es gibt keine Beschränkung für die Anzahl der Auswahl Bedingungen, die für ein Steuerelement angegeben werden können. Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) ExpressionBinding-Element für customItem für GroupBy (Format) itemselectioncondition-Element für ExpressionBinding für GroupBy (Format)

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
|[PropertyName-Element für itemselectioncondition für GroupBy (Format)](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt die .net-Eigenschaft an, die die Bedingung auslöst.|
|[ScriptBlock-Element für itemselectioncondition für GroupBy (Format)](./scriptblock-element-for-itemselectioncondition-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element für customItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Definiert die Daten, die vom-Steuerelement angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie können einen Eigenschaftsnamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)

[ExpressionBinding-Element für customItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)
