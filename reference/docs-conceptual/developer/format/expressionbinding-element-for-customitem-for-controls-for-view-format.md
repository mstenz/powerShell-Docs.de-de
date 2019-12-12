---
title: ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b9da6c5-548b-480f-86ae-6de6fecabaca
caps.latest.revision: 8
ms.openlocfilehash: 06089730008839f18c471711a4b4411722f99c38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363779"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-view-format"></a>Element „ExpressionBinding“ für CustomItem für Controls für View (Format)

Definiert die Daten, die vom-Steuerelement angezeigt werden. Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) customItem-Element für customentry für Steuerelemente für View (Format) ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)

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

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `ExpressionBinding`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|`CustomControl Element`|Optionales Element.<br /><br /> Definiert ein Steuerelement, das von diesem Steuerelement verwendet wird.|
|[Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.|
|[Enumeratecollection-Element für ExpressionBinding für Steuerelemente für View (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, dass die Elemente der Auflistungen angezeigt werden.|
|[Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.|
|[PropertyName-Element für ExpressionBinding für Steuerelemente für View (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt die .net-Eigenschaft an, deren Wert vom-Steuerelement angezeigt wird.|
|[ScriptBlock-Element für ExpressionBinding für Steuerelemente für View (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert vom-Steuerelement angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element für customentry für Steuerelemente für Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[CustomItem-Element für customentry für Steuerelemente für Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Customcontrolname-Element für ExpressionBinding für Steuerelemente für Ansicht (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[Enumeratecollection-Element für ExpressionBinding für Steuerelemente für View (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-view-format.md)

[Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[PropertyName-Element für ExpressionBinding für Steuerelemente für View (Format)](./propertyname-element-for-expressionbinding-for-controls-for-view-format.md)

[ScriptBlock-Element für ExpressionBinding für Steuerelemente für View (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
