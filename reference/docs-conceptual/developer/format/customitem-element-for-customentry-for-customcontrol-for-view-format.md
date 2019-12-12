---
title: CustomItem-Element für customentry für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363949"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a>Element „CustomItem“ für CustomEntry für CustomControl für View (Format)

Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden. Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries für View (Format) customItem-Element für Customentry für Ansicht (Format)

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
|[ExpressionBinding-Element für customItem für CustomControl für View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Daten, die vom-Steuerelement angezeigt werden.|
|[Frame-Element für customItem für CustomControl für Ansicht (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Definiert, welche Daten von der benutzerdefinierten Steuerelement Ansicht und der Anzeige angezeigt werden.|
|[NewLine-Element für customItem für benutzerdefiniertes Steuer Element für Ansicht (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Fügt der Anzeige des-Steuer Elements eine leere Zeile hinzu.|
|[Text-Element für customItem für CustomControl für Ansicht (Format)](./text-element-for-customitem-for-customview-for-view-format.md)|Optionales Element.<br /><br /> Gibt zusätzlichen Text zu den Daten an, die vom-Steuerelement angezeigt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für customentries für CustomControl für Ansicht (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Stellt eine Definition der benutzerdefinierten Steuerelement Ansicht bereit.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[Customentry-Element für customentries für View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[ExpressionBinding-Element für customItem für CustomControl für View (Format)](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[Frame-Element für customItem für CustomControl für Ansicht (Format)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[NewLine-Element für customItem für CustomControl für Ansicht (Format)](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[Text-Element für customItem für CustomControl für Ansicht (Format)](./text-element-for-customitem-for-customview-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
