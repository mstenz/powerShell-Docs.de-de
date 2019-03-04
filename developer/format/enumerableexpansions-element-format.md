---
title: EnumerableExpansions-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860256"
---
# <a name="enumerableexpansions-element-format"></a>Element „EnumerableExpansions“ (Format)

Definiert, wie .NET Auflistungsobjekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.

-Element (Format) DefaultSettings-Element (Format) EnumerableExpansions Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `EnumerableExpansions` Element. Es gibt keine Beschränkung der Anzahl von untergeordneten Elementen, die Sie verwenden können.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EnumerableExpansion-Element (Format)](./enumerableexpansion-element-format.md)|Optionales Element.<br /><br /> Definiert die spezifische .NET Auflistungsobjekte, die erweitert werden, wenn sie in einer Ansicht angezeigt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[DefaultSettings-Element (Format)](./defaultsettings-element-format.md)|Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten.|

## <a name="remarks"></a>Hinweise

Dieses Element wird verwendet, um zu definieren, Auflistungsobjekte und die Objekte in der Auflistung angezeigt werden. In diesem Fall ein Auflistungsobjekt verweist auf ein Objekt, das unterstützt die **System.Collections.ICollection** Schnittstelle.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
