---
title: Frame-Element für CustomItem für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab2a5379-299d-4c97-86a2-b639ea890fae
caps.latest.revision: 6
ms.openlocfilehash: 7f9066c0fe0954fadff9dc8f0c35a62c6710f516
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065596"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>Element „Frame“ für CustomItem für GroupBy (Format)

Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format)-Frame-Element für CustomItem für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Frame` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|`CustomItem Element`|Erforderliches Element|
|[FirstLineHanging-Element für Frame für GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wurde.|
|[FirstLineIndent-Element für Frame für GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.|
|[LeftIndent-Element für Frame für GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.|
|[RightIndent-Element für Frame für GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)RightIndent-Element|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomItem-Element für CustomEntry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.|

## <a name="remarks"></a>Hinweise

Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-groupby-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) Elemente in der gleichen `Frame` Element.

## <a name="see-also"></a>Weitere Informationen

[FirstLineHanging-Element für Frame für GroupBy (Format)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[FirstLineIndent-Element für Frame für GroupBy (Format)](./firstlineindent-element-for-frame-for-groupby-format.md)

[LeftIndent-Element für Frame für GroupBy (Format)](./leftindent-element-for-frame-for-groupby-format.md)

[RightIndent-Element für Frame für GroupBy (Format)](./rightindent-element-for-frame-for-groupby-format.md)

[CustomItem-Element für CustomEntry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
