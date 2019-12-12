---
title: Wideentry-Element für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367899"
---
# <a name="wideentry-element-for-widecontrol-format"></a>Element „WideEntry“ für WideControl (Format)

Stellt eine Definition der breiten Ansicht bereit.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `WideEntry`-Elements beschrieben. Sie müssen ein einzelnes `WideItem` untergeordnetes Element angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Entryselectedby-Element für wideentry (Format)](./entryselectedby-element-for-wideentry-format.md)|Optionales Element.<br /><br /> Definiert die .NET-Typen, die diese Breite Eingabe Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.|
|[Wideitem-Element (Format)](./wideitem-element-for-widecontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Eigenschaft oder das Skript, dessen Wert angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Wideentries-Element (Format)](./wideentries-element-for-widecontrol-format.md)|Stellt die Definitionen der breiten Ansicht bereit.|

## <a name="remarks"></a>Hinweise

Eine breite Ansicht ist ein Listenformat, in dem ein einzelner Eigenschafts Wert oder ein Skript Wert für jedes Objekt angezeigt wird. Im Gegensatz zu anderen Sicht Typen können Sie für jede Sicht Definition nur ein Element Element angeben. Weitere Informationen zu den anderen Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein `WideEntry`-Element, das ein einzelnes `WideItem` Element definiert. Das `WideItem`-Element definiert die-Eigenschaft, deren Wert in der Ansicht angezeigt wird.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

Ein umfassendes Beispiel für eine breite Ansicht finden Sie unter [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer breiten Ansicht](./creating-a-wide-view.md)

[Selectioncondition-Element für wideentry (Format)](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[Selectionsetname-Element für wideentry (Format)](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[Tyname-Element für wideentry (Format)](./typename-element-for-entryselectedby-for-wideentry-format.md)

[Wideentries-Element (Format)](./wideentries-element-for-widecontrol-format.md)

[Wideitem-Element (Format)](./wideitem-element-for-widecontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
