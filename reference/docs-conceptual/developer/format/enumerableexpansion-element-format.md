---
title: Enumerableweiterung-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368749"
---
# <a name="enumerableexpansion-element-format"></a>Element „EnumerableExpansion“ (Format)

Definiert, wie bestimmte .net-Auflistungs Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.

Configuration-Element (Format) DefaultSettings-Element (Format) enumerableerweiterungen-Element (Format) enumerableerweiterung-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EnumerableExpansion`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Entryselectedby-Element für enumerableexpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Definiert, welche .net-Auflistungs Objekte durch diese Definition erweitert werden.|
|[Expand-Element (Format)](./expand-element-format.md)|Gibt an, wie das Sammlungsobjekt für diese Definition erweitert wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Enumerableexpansions-Element (Format)](./enumerableexpansions-element-format.md)|Definiert die verschiedenen Möglichkeiten, wie .net-Auflistungs Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.|

## <a name="remarks"></a>Hinweise

Dieses Element wird verwendet, um zu definieren, wie Auflistungs Objekte und die Objekte in der Auflistung angezeigt werden. In diesem Fall bezieht sich ein Auflistungs Objekt auf jedes Objekt, das die **System. Collections. ICollection** -Schnittstelle unterstützt.

Standardmäßig werden nur die Eigenschaften der Objekte in der Auflistung angezeigt.

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
