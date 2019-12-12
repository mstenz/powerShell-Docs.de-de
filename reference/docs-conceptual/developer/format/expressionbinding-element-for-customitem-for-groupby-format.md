---
title: ExpressionBinding-Element für customItem für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368629"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>Element „ExpressionBinding“ für CustomItem für GroupBy (Format)

Definiert die Daten, die vom-Steuerelement angezeigt werden. Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) ExpressionBinding-Element für customItem für GroupBy (Format)

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
|[Customcontrolname-Element für ExpressionBinding für GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.|
|[Enumeratecollection-Element für ExpressionBinding für GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) Enumeratecollection-Element für ExpressionBinding für GroupBy (Format)|Optionales Element.<br /><br /> Gibt an, dass die Elemente der Auflistungen angezeigt werden.|
|[Itemselectioncondition-Element für ExpressionBinding für GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.|
|[PropertyName-Element für ExpressionBinding für GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt die .net-Eigenschaft an, deren Wert vom-Steuerelement angezeigt wird.|
|[ScriptBlock-Element für ExpressionBinding für GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert vom-Steuerelement angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element für customentry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.|

## <a name="see-also"></a>Weitere Informationen

[Customcontrolname-Element für ExpressionBinding für GroupBy (Format)](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[Enumeratecollection-Element für ExpressionBinding für GroupBy (Format)](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[Itemselectioncondition-Element für ExpressionBinding für GroupBy (Format)](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[PropertyName-Element für ExpressionBinding für GroupBy (Format)](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[ScriptBlock-Element für ExpressionBinding für GroupBy (Format)](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[CustomItem-Element für customentry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
