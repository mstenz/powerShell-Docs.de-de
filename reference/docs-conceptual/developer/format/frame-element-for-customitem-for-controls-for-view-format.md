---
title: Frame-Element für customItem für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5729091-78a9-4bc1-abac-210bc20c6dbe
caps.latest.revision: 7
ms.openlocfilehash: f93dc20a9c5f87c14605578062b1e60f5a3d25cf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363649"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>Element „Frame“ für CustomItem für Controls für View (Format)

Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts. Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für View (Format) customItem-Element für customentry für Steuerelemente für Ansicht (Format) Frame Element für customItem für die Ansicht (Format)

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

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Frame`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|`CustomItem Element`|Erforderliches Element|
|[Firstlinehanging-Element von Frame der Steuerelemente der Ansicht (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen die erste Zeile nach links verschoben wird.|
|[FirstLineIndent-Element von Frame der Steuerelemente der Ansicht (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen die erste Zeile nach rechts verschoben wird.|
|[LeftIndent-Element von Frame der Steuerelemente der Ansicht (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen die Daten vom linken Rand entfernt werden.|
|[RightIndent-Element von Frame-Steuerelementen der Ansicht (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen die Daten vom rechten Rand entfernt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element für customentry für Steuerelemente für Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.|

## <a name="remarks"></a>Hinweise

Sie können die Elemente [firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) nicht im selben `Frame` Element angeben.

## <a name="see-also"></a>Weitere Informationen

[Firstlinehanging-Element von Frame der Steuerelemente der Ansicht (Format)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[FirstLineIndent-Element von Frame der Steuerelemente der Ansicht (Format)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[LeftIndent-Element von Frame der Steuerelemente der Ansicht (Format)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[RightIndent-Element von Frame-Steuerelementen der Ansicht (Format)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[CustomItem-Element für customentry für Steuerelemente für Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
