---
title: Frame-Element für CustomItem für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1a13100-41a4-4847-9f07-458c85783505
caps.latest.revision: 6
ms.openlocfilehash: 925ef86e61801f5a66f89dd25e0756f00dd35155
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065579"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>Element „Frame“ für CustomItem für CustomControl für View (Format)

Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem-Element für CustomEntry für CustomControlView (Format)-Frame-Element für CustomItem für CustomControl für Ansicht (Format)

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
|[FirstLineHanging-Element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die erste Zeile der Daten auf der linken Seite verschoben wurde.|
|[FirstLineIndent-Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die erste Zeile der Daten nach rechts verschoben wurde.|
|[LeftIndent-Element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die Daten von den linken Rand verschoben wurde.|
|[RightIndent-Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt an, wie viele Zeichen, die die Daten von den rechten Rand verschoben wurde.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomItem-Element für CustomEntry für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.|

## <a name="remarks"></a>Hinweise

Sie nicht angeben, die [FirstLineHanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) und [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) Elemente in der gleichen `Frame` Element.

## <a name="see-also"></a>Weitere Informationen

[FirstLineHanging-Element](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent-Element](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[LeftIndent-Element](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent-Element](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[CustomItem-Element für CustomEntry für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
