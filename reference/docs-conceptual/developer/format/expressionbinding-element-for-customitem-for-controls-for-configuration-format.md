---
title: ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363189"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a>Element „ExpressionBinding“ für CustomItem für Controls für Configuration (Format)

Definiert die Daten, die vom-Steuerelement angezeigt werden. Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.

Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für Configuration (Format) customItem-Element für customentry für Steuerelemente für das Configuration ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format)

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
|[Customcontrolname-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an.|
|[Enumeratecollection-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, dass die Elemente der Auflistungen vom-Steuerelement angezeigt werden.|
|[Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit dieses allgemeine Steuerelement verwendet werden muss.|
|[PropertyName-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt die .net-Eigenschaft an, deren Wert durch das allgemeine Steuerelement angezeigt wird.|
|[ScriptBlock-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert durch das allgemeine Steuerelement angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element für customentry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[CustomItem-Element für customentry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
