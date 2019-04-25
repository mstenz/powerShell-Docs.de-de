---
title: CustomItem-Element für CustomEntry für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066396"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Element „CustomItem“ für CustomEntry für GroupBy (Format)

Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomItem-Element für CustomEntry für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomItem` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ExpressionBinding-Element für CustomItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert die Daten, die vom Steuerelement angezeigt wird.|
|[Frame-Element für CustomItem für GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.|
|[Neue-Zeile-Element für CustomItem für GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)|Optionales Element.<br /><br /> Eine leere Zeile eingefügt, um die Anzeige des Steuerelements.|
|[Text-Element für CustomItem für GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt die zusätzlichen Text ein, die vom Steuerelement angezeigten Daten an.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomControl für GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Stellt eine Definition der benutzerdefinierten Steuerelements an.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[CustomEntry-Element für CustomControl für GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[ExpressionBinding-Element für CustomItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Frame-Element für CustomItem für GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[Neue-Zeile-Element für CustomItem für GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)

[Text-Element für CustomItem für GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
