---
title: PropertyName-Element für ItemSelectionCondition für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064865"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a>Element „PropertyName“ für ItemSeclectionCondition für CustomControl für View (Format)

Gibt die .NET-Eigenschaft, die die Bedingung auslöst. Wenn diese Eigenschaft vorhanden ist oder wenn ergibt die Auswertung `true`, die Bedingung ist erfüllt, und das Steuerelement wird verwendet. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem-Element für CustomEntry für Ansicht (Format) ExpressionBinding-Element für CustomItem für CustomControl für ItemSelectionCondition-Element für Ausdrucksbindung für CustomControl für Ansicht (Format)-PropertyName-Element für ItemSelectionCondition für Ansicht (Format) CustomControl für Ansicht (Format

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ItemSelectionCondition-Element für Ausdrucksbindung für CustomControl für Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der .NET-Eigenschaft, die die Bedingung auslöst.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, Sie können nicht angeben, die ["scriptblock"](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) -Element, wenn die auswahlbedingung zu definieren.

## <a name="see-also"></a>Weitere Informationen

[ScriptBlock-Element für ItemSelectionCondition für CustomControl für Ansicht (Format)](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[ItemSelectionCondition-Element für Ausdrucksbindung für CustomControl für Ansicht (Format)](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
