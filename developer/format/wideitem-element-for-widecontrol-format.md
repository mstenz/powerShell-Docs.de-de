---
title: WideItem-Element für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862626"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Element „WideItem“ für WideControl (Format)

Definiert die Eigenschaft oder ein Skript, dessen Wert angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) WideItem Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `WideItem` Element. Das `FormatString`-Element ist optional. Allerdings müssen Sie angeben einer `PropertyName` oder `ScriptBlock` -Element, aber Sie können nicht beide angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[FormatString-Element für WideItem für WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird.|
|[PropertyName-Element für WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Gibt die Eigenschaft des Objekts, dessen Wert in der breiten Ansicht angezeigt wird.|
|[ScriptBlock-Element für WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[WideEntry-Element (Format)](./wideentry-element-for-widecontrol-format.md)|Stellt eine Definition der breiten Ansicht.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [Breite Ansicht](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `WideEntry` Element, das ein einzelnes definiert `WideItem` Element. Die `WideItem` -Element definiert die Eigenschaft oder ein Skript, dessen Wert in der Ansicht angezeigt wird.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Ein vollständiges Beispiel eine Breite Ansicht, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[FormatString-Element für WideItem für WideControl (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName-Element für WideItem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[ScriptBlock-Element für WideItem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[WideEntry-Element (Format)](./wideentry-element-for-widecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
