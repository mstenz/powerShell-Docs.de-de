---
title: FirstLineHanging-Element für Frame für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065831"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>Element „FirstLineHanging“ für Frame für GroupBy (Format)

Gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wurde. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format)-Frame-Element für CustomItem für GroupBy (Format) FirstLineHanging-Element für Frame für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `FirstLineHanging` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Frame-Element für CustomItem für GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.|

## <a name="text-value"></a>Textwert

Geben Sie die Anzahl der Zeichen, die die erste Zeile der Daten verschoben werden sollen.

## <a name="remarks"></a>Hinweise

Wenn dieses Element angegeben ist, Sie können nicht angeben, die [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) Element.

## <a name="see-also"></a>Weitere Informationen

[FirstLineIndent-Element für Frame für GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[Frame-Element für CustomItem für GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
