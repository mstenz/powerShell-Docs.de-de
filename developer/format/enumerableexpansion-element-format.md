---
title: EnumerableExpansion-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066140"
---
# <a name="enumerableexpansion-element-format"></a>Element „EnumerableExpansion“ (Format)

Definiert, wie .NET Datenbanksammlung Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.

-Element (Format) DefaultSettings-Element (Format) EnumerableExpansions-Element (Format) EnumerableExpansion Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EnumerableExpansion` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für EnumerableExpansion (Format)](./entryselectedby-element-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Definiert, welche .NET Sammlung Objekte nach dieser Definition erweitert werden.|
|[Erweitern Sie (Format)-Element](./expand-element-format.md)|Gibt an, wie das Objekt für diese Definition erweitert wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EnumerableExpansions-Element (Format)](./enumerableexpansions-element-format.md)|Definiert den verschiedenen Möglichkeiten, .NET-Auflistung, die Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.|

## <a name="remarks"></a>Hinweise

Dieses Element wird verwendet, um zu definieren, Auflistungsobjekte und die Objekte in der Auflistung angezeigt werden. In diesem Fall ein Auflistungsobjekt verweist auf ein Objekt, das unterstützt die **System.Collections.ICollection** Schnittstelle.

Standardmäßig werden nur die Eigenschaften der Objekte in der Auflistung angezeigt.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
