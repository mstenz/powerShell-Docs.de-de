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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362519"
---
# <a name="propertyname-element-for-groupby-format"></a>Element „PropertyName“ für GroupBy (Format)

Gibt die .net-Eigenschaft an, die eine neue Gruppe startet, wenn sich der Wert ändert.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) propertyName-Element für GroupBy (Format)

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
|[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)|Definiert, wie eine Gruppe von .NET-Objekten angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der .net-Eigenschaft an.

## <a name="remarks"></a>Hinweise

Windows PowerShell startet eine neue Gruppe, wenn der Wert dieser Eigenschaft geändert wird.

Wenn dieses Element angegeben ist, können Sie das [ScriptBlock](./scriptblock-element-for-groupby-format.md) -Element nicht angeben, um eine neue Gruppe zu starten.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie eine neue Gruppe gestartet wird, wenn sich der Wert einer Eigenschaft ändert.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Ein Beispiel für eine komplette Formatierungs Datei, die dieses Element enthält, finden Sie unter [Wide View (GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Weitere Informationen

[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)

[ScriptBlock-Element für GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
