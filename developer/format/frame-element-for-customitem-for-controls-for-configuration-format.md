---
title: Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862976"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Element „Frame“ für CustomItem für Controls für Configuration (Format)

Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für (Format) CustomItem Konfigurationselement für CustomEntry für Steuerelemente für die Frame-Konfigurationselement für CustomItem für Steuerelemente für die Konfiguration (Format)-Format)

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
|[FirstLineHanging-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wurde.|
|[FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.|
|[LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.|
|[RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.|

## <a name="remarks"></a>Hinweise

Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) Elemente in der gleichen `Frame` Element.

## <a name="see-also"></a>Weitere Informationen

[FirstLineHanging-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
