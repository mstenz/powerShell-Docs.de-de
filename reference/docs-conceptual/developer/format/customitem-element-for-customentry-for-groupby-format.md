---
title: CustomItem-Element für customentry für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c517aa-24f5-41ae-b82d-cb0fac81a245
caps.latest.revision: 7
ms.openlocfilehash: 2d821f5e3bc8d0f81ef8a8a040c6f9bcb1658bee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363879"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a>Element „CustomItem“ für CustomEntry für GroupBy (Format)

Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden. Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customItem-Element für Customentry für GroupBy (Format)

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

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomItem`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element für customItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert die Daten, die vom-Steuerelement angezeigt werden.|
|[Frame-Element für customItem für GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.|
|[NewLine-Element für customItem für GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)|Optionales Element.<br /><br /> Fügt der Anzeige des-Steuer Elements eine leere Zeile hinzu.|
|[Text-Element für customItem für GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt zusätzlichen Text zu den Daten an, die vom-Steuerelement angezeigt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für CustomControl für GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Stellt eine Definition der benutzerdefinierten Steuerelement Ansicht bereit.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[Customentry-Element für CustomControl für GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)

[ExpressionBinding-Element für customItem für GroupBy (Format)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[Frame-Element für customItem für GroupBy (Format)](./frame-element-for-customitem-for-groupby-format.md)

[NewLine-Element für customItem für GroupBy (Format)](./newline-element-for-customitem-for-groupby-format.md)

[Text-Element für customItem für GroupBy (Format)](./text-element-for-customitem-for-groupby-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
