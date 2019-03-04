---
title: Frame-Element für CustomItem für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859816"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Element „Frame“ für CustomItem für Controls für View (Format)

Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für Ansicht (Format)-Frame-Element für CustomItem für Steuerelemente für die Ansicht (Format)

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
|[FirstLineHanging-Element des Frames von Steuerelementen der Ansicht (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die auf der linken Seite die erste Zeile verschoben wurde.|
|[FirstLineIndent-Element des Frames von Steuerelementen der Ansicht (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die erste Zeile nach rechts verschoben wurde.|
|[LeftIndent-Element des Frames von Steuerelementen der Ansicht (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.|
|[RightIndent-Element des Frames von Steuerelementen der Ansicht (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.|

## <a name="remarks"></a>Hinweise

Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) Elemente in der gleichen `Frame` Element.

## <a name="see-also"></a>Weitere Informationen

[FirstLineHanging-Element des Frames von Steuerelementen der Ansicht (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent-Element des Frames von Steuerelementen der Ansicht (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent-Element des Frames von Steuerelementen der Ansicht (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent-Element des Frames von Steuerelementen der Ansicht (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
