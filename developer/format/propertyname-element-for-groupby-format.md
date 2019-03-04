---
title: PropertyName-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863266"
---
# <a name="propertyname-element-for-groupby-format"></a>Element „PropertyName“ für GroupBy (Format)

Gibt die .NET-Eigenschaft, die eine neue Gruppe beginnt, wenn sich der Wert ändert.

Configuration Element (Format) ViewDefinitions-Element (Format) GroupBy Ansichtselement Element (Format) für Ansicht (Format)-PropertyName-Element für GroupBy (Format)

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
|[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)|Definiert, wie eine Gruppe von .NET-Objekten angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der .NET-Eigenschaft.

## <a name="remarks"></a>Hinweise

Windows PowerShell startet eine neue Gruppe aus, wenn der Wert dieser Eigenschaft geändert wird.

Wenn dieses Element angegeben ist, können Sie nicht angeben der ["scriptblock"](./scriptblock-element-for-groupby-format.md) Element um eine neue Gruppe zu starten.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie eine neue Gruppe zu starten, wenn der Wert einer Eigenschaft geändert wird.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Ein Beispiel für eine vollständige Formatierung-Datei, die dieses Element enthält, finden Sie unter [Breite Ansicht (-GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Weitere Informationen

[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

[ScriptBlock-Element für GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
