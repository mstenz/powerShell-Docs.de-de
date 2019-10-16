---
title: Wideentries-Element für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361429"
---
# <a name="wideentries-element-for-widecontrol-format"></a>Element „WideEntries“ für WideControl (Format)

Stellt die Definitionen der breiten Ansicht bereit. In der breiten Ansicht muss mindestens eine Definition angegeben werden.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) widecontrol-Element (Format) wideentries-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `WideEntries`-Elements beschrieben. Es muss mindestens ein untergeordnetes Element angegeben werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Wideentry-Element (Format)](./wideentry-element-for-widecontrol-format.md)|Stellt eine Definition der breiten Ansicht bereit.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Widecontrol-Element (Format)](./widecontrol-element-format.md)|Definiert ein breites Listenformat (Einzelwert) für die Sicht.|

## <a name="remarks"></a>Hinweise

Eine breite Ansicht ist ein Listenformat, in dem ein einzelner Eigenschafts Wert oder ein Skript Wert für jedes Objekt angezeigt wird. Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Wide View Components](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein `WideEntries`-Element, das ein einzelnes `WideEntry`-Element definiert. Das `WideEntry`-Element enthält ein einzelnes `WideItem`-Element, das definiert, welcher Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

Ein umfassendes Beispiel für eine breite Ansicht finden Sie unter [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer breiten Ansicht](./creating-a-wide-view.md)

[Widecontrol-Element (Format)](./widecontrol-element-format.md)

[Wideentry-Element (Format)](./wideentry-element-for-widecontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
