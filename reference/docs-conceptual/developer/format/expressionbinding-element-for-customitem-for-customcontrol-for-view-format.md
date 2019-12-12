---
title: ExpressionBinding-Element für customItem für CustomControl für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363149"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a>Element „ExpressionBinding“ für CustomItem für CustomControl für View (Format)

Definiert die Daten, die vom-Steuerelement angezeigt werden. Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.

Konfigurationselement (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element für View (Format) customentries-Element für CustomControl for View (Format) customentry-Element für customentries für CustomControl für Ansicht ( Format) customItem-Element für customentry für CustomControl für View (Format) ExpressionBinding-Element für customItem für CustomControl for View (Format)

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
|[Customcontrolname-Element für ExpressionBinding für CustomControl für View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.|
|[Enumeratecollection-Element für ExpressionBinding für CustomControl für View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, dass die Elemente der Auflistungen angezeigt werden.|
|[Itemselectioncondition-Element für ExpressionBinding für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.|
|[PropertyName-Element für ExpressionBinding für CustomControl für View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt die .net-Eigenschaft an, deren Wert vom-Steuerelement angezeigt wird.|
|[ScriptBlock-Element für ExpressionBinding für customcustomcontrol für View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert vom-Steuerelement angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element für customentry für CustomControl für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[Customcontrolname-Element für ExpressionBinding für CustomControl für View (Format)](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Enumeratecollection-Element für ExpressionBinding für CustomControl für View (Format)](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[Itemselectioncondition-Element für ExpressionBinding für die Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[PropertyName-Element für ExpressionBinding für CustomControl für View (Format)](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[ScriptBlock-Element für ExpressionBinding für CustomControl für View (Format)](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[CustomItem-Element für customentry für CustomControl für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
