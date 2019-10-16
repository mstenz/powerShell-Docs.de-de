---
title: Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362919"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a>Element „ItemSelectionCondition“ für ExpressionBinding für Controls für Configuration (Format)

Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss. Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.

Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für Configuration (Format) customItem-Element für customentry für Steuerelemente für das Configuration ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format) Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)

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
|[PropertyName-Element für itemselectioncondition für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt die .net-Eigenschaft an, die die Bedingung auslöst.|
|[ScriptBlock-Element für itemselectioncondition für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definiert die Daten, die vom-Steuerelement angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie können einen Eigenschaftsnamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für itemselectioncondition für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock-Element für itemselectioncondition für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
