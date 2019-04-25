---
title: WideEntries-Element für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083687"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Element „WideEntries“ für WideControl (Format)

Enthält die Definitionen der breiten Ansicht an. Die Breite Ansicht muss eine oder mehrere Definitionen angeben.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `WideEntries` Element. Mindestens ein untergeordnetes Element muss angegeben werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[WideEntry-Element (Format)](./wideentry-element-for-widecontrol-format.md)|Stellt eine Definition der breiten Ansicht.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[WideControl-Element (Format)](./widecontrol-element-format.md)|Definiert eine Vielzahl (Einzelwert) Listenformat für die Ansicht.|

## <a name="remarks"></a>Hinweise

Eine Breite Ansicht ist einer Liste an, in dem eine einzelne Eigenschaft-Wert oder die Skriptwert für jedes Objekt angezeigt. Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [Wide Ansichtskomponenten](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `WideEntries` Element, das ein einzelnes definiert `WideEntry` Element. Die `WideEntry` -Element enthält ein einzelnes `WideItem` Element, das definiert, welche Eigenschaft oder ein Skript-Wert in der Ansicht angezeigt wird.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Ein vollständiges Beispiel eine Breite Ansicht, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[WideControl-Element (Format)](./widecontrol-element-format.md)

[WideEntry-Element (Format)](./wideentry-element-for-widecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
