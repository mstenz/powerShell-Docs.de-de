---
title: CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862936"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Element „CustomItem“ für CustomEntry für Controls für Configuration (Format)

Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( Format) CustomEntry-Element für CustomControl für Steuerelemente für (Format) CustomItem Konfigurationselement für CustomEntry für Steuerelemente für die Konfiguration

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomItem` Element. Weitere Informationen finden Sie unter "Hinweise".

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die Daten, die vom Steuerelement angezeigt wird.|
|[Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.|
|[Neue-Zeile-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Eine leere Zeile eingefügt, um die Anzeige des Steuerelements.|
|[Text-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Fügt Text an, wie z. B. Klammern oder durch Klammern, der Anzeige des Steuerelements an.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Stellt eine Definition des Steuerelements.|

## <a name="remarks"></a>Hinweise

Wenn Sie die untergeordneten Elemente angeben die `CustomItem` -Element, Bedenken Sie Folgendes:

- Die untergeordneten Elemente müssen in der folgenden Reihenfolge hinzugefügt werden: `ExpressionBinding`, `NewLine`, `Text`, und `Frame`.

- Es ist nicht begrenzt auf die Anzahl der Sequenzen, die Sie angeben können.

- In der Sequenz vorhanden ist nicht begrenzt auf die Anzahl der `ExpressionBinding` Elemente, die Sie verwenden können.

## <a name="see-also"></a>Weitere Informationen

[ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Frame-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Neue-Zeile-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Text-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
