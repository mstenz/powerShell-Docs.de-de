---
title: PropertyName-Element für itemselectioncondition für Steuerelemente für View (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362479"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a>Element „PropertyName“ für ItemSeclectionCondition für Controls für View (Format)

Gibt die .net-Eigenschaft an, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder als zu `true`ausgewertet wird, wird die Bedingung erfüllt, und das-Steuerelement wird verwendet. Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) customItem-Element für customentry für Steuerelemente für View (Format) ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format) Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für das View (Format) propertyName-Element für itemselectioncondition für Steuerelemente für View (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `PropertyName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|Definiert die Bedingung, die vorhanden sein muss, damit dieses Steuerelement verwendet werden muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der .net-Eigenschaft an, die die Bedingung auslöst.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, können Sie das [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) -Element nicht angeben, wenn Sie die Auswahlbedingung definieren.

## <a name="see-also"></a>Weitere Informationen

[ScriptBlock-Element für itemselectioncondition für Steuerelemente für View (Format)](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[Itemselectioncondition-Element von ExpressionBinding für Steuerelemente für View (Format)](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
