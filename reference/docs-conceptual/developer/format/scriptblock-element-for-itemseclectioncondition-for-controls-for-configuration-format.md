---
title: ScriptBlock-Element für itemabclectioncondition für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362119"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a>Element „ScriptBlock“ für ItemSeclectionCondition für Controls für Configuration (Format)

Gibt das Skript an, das die Bedingung auslöst. Wenn dieses Skript `true` ausgewertet wird, wird die Bedingung erfüllt, und das-Steuerelement wird verwendet. Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.

Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für Configuration (Format) customItem-Element für customentry für Steuerelemente für das Configuration ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format) Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für das Configuration (Format) ScriptBlock-Element für itemselectioncondition für Steuerelemente für die Konfiguration (Format)

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
|[Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.|

## <a name="text-value"></a>Textwert

Geben Sie das auszuwertende Skript an.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, können Sie beim Definieren der Auswahlbedingung nicht das [propertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) -Element angeben.

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für itemabclectioncondition für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[Itemselectioncondition-Element für ExpressionBinding für Steuerelemente für die Konfiguration (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
