---
title: Firstlinehanging-Element für Frame für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363819"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>Element „FirstLineHanging“ für Frame für GroupBy (Format)

Gibt an, wie viele Zeichen die erste Zeile der Daten nach links verschoben wird. Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) customItem-Element für customentry für GroupBy (Format) Frame-Element für customItem für GroupBy (Format) firstlinehanging-Element für Frame für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `FirstLineHanging`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Frame-Element für customItem für GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.|

## <a name="text-value"></a>Textwert

Geben Sie die Anzahl der Zeichen an, die Sie in die erste Zeile der Daten verschieben möchten.

## <a name="remarks"></a>Hinweise

Wenn dieses Element angegeben ist, können Sie das [firstlineingedent](./firstlineindent-element-for-frame-for-groupby-format.md) -Element nicht angeben.

## <a name="see-also"></a>Weitere Informationen

[FirstLineIndent-Element für Frame für GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Frame-Element für customItem für GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
