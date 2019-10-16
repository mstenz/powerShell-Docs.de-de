---
title: CustomItem-Element für customentry für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33cb5350-73ef-4b79-a879-0edf051869e4
caps.latest.revision: 7
ms.openlocfilehash: 174ba6a14819f823ec39f72e49a626e781221d8c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363939"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a>Element „CustomItem“ für CustomEntry für Controls für View (Format)

Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird. Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für Steuerelemente für Ansicht (Format) customItem-Element für customentry für Steuerelemente für Ansicht (Format)

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

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomItem`-Elements beschrieben. Weitere Informationen finden Sie unter "Hinweise".

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Daten, die vom-Steuerelement angezeigt werden.|
|[Frame-Element für customItem für Steuerelemente für Ansicht (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.|
|[NewLine-Element für customItem für Steuerelemente für Ansicht (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Fügt der Anzeige des-Steuer Elements eine leere Zeile hinzu.|
|[Text-Element für customItem für Steuerelemente für Ansicht (Format)](./text-element-for-customitem-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Fügt der Anzeige des-Steuer Elements Text, z. b. Klammern oder eckige Klammern, hinzu.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für customentries für Steuerelemente für Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Stellt eine Definition des-Steuer Elements bereit.|

## <a name="remarks"></a>Hinweise

Beachten Sie Folgendes, wenn Sie die untergeordneten Elemente des Elements `CustomItem` angeben:

- Die untergeordneten Elemente müssen in der folgenden Reihenfolge hinzugefügt werden: `ExpressionBinding`, `NewLine`, `Text` und `Frame`.

- Es gibt keine maximale Beschränkung für die Anzahl der Sequenzen, die Sie angeben können.

- In jeder Sequenz gibt es keine maximale Beschränkung für die Anzahl der `ExpressionBinding`-Elemente, die Sie verwenden können.

## <a name="see-also"></a>Weitere Informationen

[ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Frame-Element für customItem für Steuerelemente für Ansicht (Format)](./frame-element-for-customitem-for-controls-for-view-format.md)

[NewLine-Element für customItem für Steuerelemente für Ansicht (Format)](./newline-element-for-customitem-for-controls-for-view-format.md)

[Text-Element für customItem für Steuerelemente für Ansicht (Format)](./text-element-for-customitem-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
