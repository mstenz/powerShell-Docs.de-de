---
title: CustomItem-Element für customentry für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73fb11ee-0ebd-477a-ac36-acdfbb32e70d
caps.latest.revision: 7
ms.openlocfilehash: bd0cb69770817ec215ddb1862a43a838baddefcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364029"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a>Element „CustomItem“ für CustomEntry für Controls für Configuration (Format)

Definiert, welche Daten vom Steuerelement angezeigt werden und wie es angezeigt wird. Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.

Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für Configuration (Format) customItem-Element für customentry für Steuerelemente für die Konfiguration

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

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomItem`-Elements beschrieben. Weitere Informationen finden Sie unter "Hinweise".

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die Daten, die vom-Steuerelement angezeigt werden.|
|[Frame-Element für customItem für Steuerelemente für die Konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.|
|[NewLine-Element für customItem für Steuerelemente für die Konfiguration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Fügt der Anzeige des-Steuer Elements eine leere Zeile hinzu.|
|[Text-Element für customItem für Steuerelemente für die Konfiguration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Fügt der Anzeige des-Steuer Elements Text, z. b. Klammern oder eckige Klammern, hinzu.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Stellt eine Definition des-Steuer Elements bereit.|

## <a name="remarks"></a>Hinweise

Beachten Sie Folgendes, wenn Sie die untergeordneten Elemente des Elements `CustomItem` angeben:

- Die untergeordneten Elemente müssen in der folgenden Reihenfolge hinzugefügt werden: `ExpressionBinding`, `NewLine`, `Text` und `Frame`.

- Es gibt keine maximale Beschränkung für die Anzahl der Sequenzen, die Sie angeben können.

- In jeder Sequenz gibt es keine maximale Beschränkung für die Anzahl der `ExpressionBinding`-Elemente, die Sie verwenden können.

## <a name="see-also"></a>Weitere Informationen

[ExpressionBinding-Element für customItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Frame-Element für customItem für Steuerelemente für die Konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[NewLine-Element für customItem für Steuerelemente für die Konfiguration (Format)](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[Text-Element für customItem für Steuerelemente für die Konfiguration (Format)](./text-element-for-customitem-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
