---
title: Expand-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368739"
---
# <a name="expand-element-format"></a>Element „Expand“ (Format)

Gibt an, wie das Sammlungsobjekt für diese Definition erweitert wird.

Configuration-Element (Format) DefaultSettings-Element (Format) enumerableexpand-Element (Format) enumerableweiterung-Element (Format) Expand Element (Format)

## <a name="syntax"></a>Syntax

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Expand`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Enumerableweiterung-Element (Format)](./enumerableexpansion-element-format.md)|Definiert, wie bestimmte .net-Auflistungs Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.|

## <a name="text-value"></a>Textwert

Geben Sie einen der folgenden Werte an.

- Enumonly: zeigt nur die Eigenschaften der Objekte in der Auflistung an.

- Coreonly: zeigt nur die Eigenschaften des Auflistungs Objekts an.

- Beides: zeigt die Eigenschaften der Objekte in der Auflistung und die Eigenschaften des Auflistungs Objekts an.

## <a name="remarks"></a>Hinweise

Dieses Element wird verwendet, um zu definieren, wie Auflistungs Objekte und die Objekte in der Auflistung angezeigt werden. In diesem Fall bezieht sich ein Auflistungs Objekt auf jedes Objekt, das die **System. Collections. ICollection** -Schnittstelle unterstützt.

Standardmäßig werden nur die Eigenschaften der Objekte in der Auflistung angezeigt.

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
