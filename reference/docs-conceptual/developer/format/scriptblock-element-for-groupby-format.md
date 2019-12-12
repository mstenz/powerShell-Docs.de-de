---
title: ScriptBlock-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364929"
---
# <a name="scriptblock-element-for-groupby-format"></a>Element „ScriptBlock“ für GroupBy (Format)

Gibt das Skript an, das eine neue Gruppe startet, wenn sich der Wert ändert.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) ScriptBlock-Element für GroupBy (Format)

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
|[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)|Definiert, wie eine Gruppe von .NET-Objekten angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie das auszuwertende Skript an.

## <a name="remarks"></a>Hinweise

PowerShell startet immer dann eine neue Gruppe, wenn der Wert dieses Skripts geändert wird.

Wenn dieses Element angegeben ist, können Sie das [propertyName](propertyname-element-for-groupby-format.md) -Element nicht angeben, um eine neue Gruppe zu starten.

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für GroupBy (Format)](propertyname-element-for-groupby-format.md)

[GroupBy-Element für Ansicht (Format)](groupby-element-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](writing-a-powershell-formatting-file.md)
