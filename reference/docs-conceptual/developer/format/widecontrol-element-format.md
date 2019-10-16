---
title: Widecontrol-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367989"
---
# <a name="widecontrol-element-format"></a>Element „WideControl“ (Format)

Definiert ein breites Listenformat (Einzelwert) für die Sicht. Diese Ansicht zeigt einen einzelnen Eigenschafts Wert oder einen Skript Wert für jedes Objekt an.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) widecontrol-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `WideControl`-Elements beschrieben. Sie können die Elemente `AutoSize` und `ColumnNumber` nicht gleichzeitig angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[AutoSize-Element für widecontrol (Format)](./autosize-element-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt an, ob die Spaltengröße und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.|
|[ColumnNumber-Element für widecontrol (Format)](./columnnumber-element-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt die Anzahl der Spalten an, die in der breiten Ansicht angezeigt werden.|
|[Wideentries-Element (Format)](./wideentries-element-for-widecontrol-format.md)|Erforderliches Element.<br /><br /> Stellt die Definitionen der breiten Ansicht bereit.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die verwendet wird, um ein oder mehrere .NET-Objekte anzuzeigen.|

## <a name="remarks"></a>Hinweise

Wenn Sie eine breite Sicht definieren, können Sie das `AutoSize`-Element oder den `ColumnNumber` hinzufügen, aber Sie können nicht beides hinzufügen.

In den meisten Fällen ist nur eine Definition für jede Breite Ansicht erforderlich, aber es ist möglich, mehrere Definitionen zu verwenden, wenn Sie dieselbe Ansicht verwenden möchten, um unterschiedliche .NET-Objekte anzuzeigen. In diesen Fällen können Sie eine separate Definition für jedes Objekt oder jede Gruppe von Objekten bereitstellen.

Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Wide View Components](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein `WideControl`-Element, das verwendet wird, um eine Eigenschaft des [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) -Objekts anzuzeigen.

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

Ein umfassendes Beispiel für eine breite Ansicht finden Sie unter [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[AutoSize-Element für widecontrol (Format)](./autosize-element-for-widecontrol-format.md)

[ColumnNumber-Element für widecontrol (Format)](./columnnumber-element-for-widecontrol-format.md)

[View-Element (Format)](./view-element-format.md)

[Wideentries-Element (Format)](./wideentries-element-for-widecontrol-format.md)

[Breite Ansicht (Basic)](./wide-view-basic.md)

[Erstellen einer breiten Ansicht](./creating-a-wide-view.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
