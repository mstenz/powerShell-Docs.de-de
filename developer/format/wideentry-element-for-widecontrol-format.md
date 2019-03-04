---
title: WideEntry-Element für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856526"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Element „WideEntry“ für WideControl (Format)

Stellt eine Definition der breiten Ansicht.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `WideEntry` Element. Sie müssen angeben, dass eine einzelne `WideItem` untergeordnetes Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Optionales Element.<br /><br /> Definiert die Typen von .NET, mit denen diese Breite Eintrag-Definition oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|
|[WideItem-Element (Format)](./wideitem-element-for-widecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Eigenschaft oder ein Skript, dessen Wert angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[WideEntries-Element (Format)](./wideentries-element-for-widecontrol-format.md)|Enthält die Definitionen der breiten Ansicht an.|

## <a name="remarks"></a>Hinweise

Eine Breite Ansicht ist einer Liste an, in dem eine einzelne Eigenschaft-Wert oder die Skriptwert für jedes Objekt angezeigt. Im Gegensatz zu anderen Arten von Ansichten können Sie nur eine Item-Element für jede Sichtdefinition angeben. Weitere Informationen zu den anderen Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `WideEntry` Element, das ein einzelnes definiert `WideItem` Element. Die `WideItem` -Element definiert die Eigenschaft, deren Wert in der Ansicht angezeigt wird.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Ein vollständiges Beispiel eine Breite Ansicht, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[SelectionCondition-Element für WideEntry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[SelectionSetName-Element für WideEntry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[TypeName-Element für WideEntry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries-Element (Format)](./wideentries-element-for-widecontrol-format.md)

[WideItem-Element (Format)](./wideitem-element-for-widecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
