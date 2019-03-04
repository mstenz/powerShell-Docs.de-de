---
title: CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855606"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Element „CustomItem“ für CustomEntry für Controls für View (Format)

Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für Ansicht (Format) CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomItem` Element. Weitere Informationen finden Sie unter "Hinweise".

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Daten, die vom Steuerelement angezeigt wird.|
|[Frame-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert, wie die Daten angezeigt werden, z. B. das Verschieben von Daten nach links oder rechts.|
|[Neue-Zeile-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Eine leere Zeile eingefügt, um die Anzeige des Steuerelements.|
|[Text-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./text-element-for-customitem-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Fügt Text an, wie z. B. Klammern oder durch Klammern, der Anzeige des Steuerelements an.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Stellt eine Definition des Steuerelements.|

## <a name="remarks"></a>Hinweise

Wenn Sie die untergeordneten Elemente angeben die `CustomItem` -Element, Bedenken Sie Folgendes:

- Die untergeordneten Elemente müssen in der folgenden Reihenfolge hinzugefügt werden: `ExpressionBinding`, `NewLine`, `Text`, und `Frame`.

- Es ist nicht begrenzt auf die Anzahl der Sequenzen, die Sie angeben können.

- In der Sequenz vorhanden ist nicht begrenzt auf die Anzahl der `ExpressionBinding` Elemente, die Sie verwenden können.

## <a name="see-also"></a>Weitere Informationen

[ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Frame-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[Neue-Zeile-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Text-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
