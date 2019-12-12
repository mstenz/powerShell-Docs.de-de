---
title: Frame-Element für customItem für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d879c8ce-679d-4622-bc43-c207f6413871
caps.latest.revision: 9
ms.openlocfilehash: b11b154a94daccead57bdfb5e579e1de2c190c09
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363659"
---
# <a name="frame-element-for-customitem-for-controls-for-configuration-format"></a>Element „Frame“ für CustomItem für Controls für Configuration (Format)

Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts. Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.

Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für Configuration (Format) customItem-Element für customentry für Steuerelemente für das Configuration Frame-Element für customItem für Steuerelemente für die Konfiguration (Format)

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
|[Firstlinehanging-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen die erste Zeile der Daten nach links verschoben wird.|
|[FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen die erste Zeile der Daten nach rechts verschoben wird.|
|[LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen die Daten vom linken Rand entfernt werden.|
|[RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen die Daten vom rechten Rand entfernt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomItem-Element für customentry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird.|

## <a name="remarks"></a>Hinweise

Sie können die Elemente [firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md) nicht im selben `Frame` Element angeben.

## <a name="see-also"></a>Weitere Informationen

[Firstlinehanging-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlineindent-element-for-frame-for-controls-for-configuration-format.md)

[LeftIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./leftindent-element-for-frame-for-controls-for-configuration-format.md)

[RightIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)](./rightindent-element-for-frame-for-controls-for-configuration-format.md)

[CustomItem-Element für customentry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
