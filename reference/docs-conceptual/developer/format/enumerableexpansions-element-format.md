---
title: Enumerableexpansions-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363299"
---
# <a name="enumerableexpansions-element-format"></a>Element „EnumerableExpansions“ (Format)

Definiert, wie .net-Auflistungs Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.

Configuration-Element (Format) DefaultSettings-Element (Format) enumerableerweiterungen-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EnumerableExpansions`-Elements beschrieben. Es gibt keine Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Enumerableweiterung-Element (Format)](./enumerableexpansion-element-format.md)|Optionales Element.<br /><br /> Definiert die spezifischen .net-Auflistungs Objekte, die erweitert werden, wenn Sie in einer Ansicht angezeigt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[DefaultSettings-Element (Format)](./defaultsettings-element-format.md)|Definiert allgemeine Einstellungen, die für alle Sichten der Formatierungs Datei gelten.|

## <a name="remarks"></a>Hinweise

Dieses Element wird verwendet, um zu definieren, wie Auflistungs Objekte und die Objekte in der Auflistung angezeigt werden. In diesem Fall bezieht sich ein Auflistungs Objekt auf jedes Objekt, das die **System. Collections. ICollection** -Schnittstelle unterstützt.

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
