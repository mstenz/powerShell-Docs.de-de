---
title: CustomItem-Element für CustomEntry für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066412"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Element „CustomItem“ für CustomEntry für CustomControl für View (Format)

Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird. Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem-Element für CustomEntry für Ansicht (Format)

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
|[ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Daten, die vom Steuerelement angezeigt wird.|
|[Frame-Element für CustomItem für CustomControl für Ansicht (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Definiert, welche Daten von der Sicht des benutzerdefinierten Steuerelements angezeigt werden und wie diese angezeigt wird.|
|[Neue-Zeile-Element für CustomItem für benutzerdefiniertes Steuerelement für die Ansicht (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Eine leere Zeile eingefügt, um die Anzeige des Steuerelements.|
|[Text-Element für CustomItem für CustomControl für Ansicht (Format)](./text-element-for-customitem-for-customview-for-view-format.md)|Optionales Element.<br /><br /> Gibt die zusätzlichen Text ein, die vom Steuerelement angezeigten Daten an.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomEntries für CustomControl für Ansicht (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Stellt eine Definition der benutzerdefinierten Steuerelements an.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[CustomEntry-Element für CustomEntries für Ansicht (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Frame-Element für CustomItem für CustomControl für Ansicht (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[Neue-Zeile-Element für CustomItem für CustomControl für Ansicht (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Text-Element für CustomItem für CustomControl für Ansicht (Format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
