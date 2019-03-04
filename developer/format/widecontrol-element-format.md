---
title: WideControl-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859826"
---
# <a name="widecontrol-element-format"></a>Element „WideControl“ (Format)

Definiert eine Vielzahl (Einzelwert) Listenformat für die Ansicht. Diese Ansicht zeigt eine einzelne Eigenschaft-Wert oder die Skriptwert für jedes Objekt.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `WideControl` Element. Sie können nicht angeben, die `AutoSize` und `ColumnNumber` Elemente zur gleichen Zeit.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[AutoSize-Element für WideControl (Format)](./autosize-element-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt an, ob die Größe der Spalte und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.|
|[ColumnNumber-Element für WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt die Anzahl der Spalten in der breiten Ansicht angezeigt.|
|[WideEntries-Element (Format)](./wideentries-element-for-widecontrol-format.md)|Erforderliches Element.<br /><br /> Enthält die Definitionen der breiten Ansicht an.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die verwendet wird, um eine oder mehrere .NET Objekte anzuzeigen.|

## <a name="remarks"></a>Hinweise

Wenn Sie eine Breite Ansicht definieren zu können, können Sie Hinzufügen der `AutoSize` Element oder die `ColumnNumber` jedoch beide kann nicht hinzugefügt werden.

Klicken Sie in den meisten Fällen nur eine Definition für die einzelnen Breiten Ansichten erforderlich ist, aber es ist möglich, mehrere Definitionen zu besitzen, sollten Sie die gleiche Ansicht zu verwenden, um verschiedene .NET Objekte anzuzeigen. In diesen Fällen können Sie eine separate Definition für jedes Objekt bzw. den Satz von Objekten bereitstellen.

Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [Wide Ansichtskomponenten](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `WideControl` -Element, das verwendet wird, eine Eigenschaft der an die ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) Objekt.

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

Ein vollständiges Beispiel eine Breite Ansicht, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[AutoSize-Element für WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[ColumnNumber-Element für WideControl (Format)](./columnnumber-element-for-widecontrol-format.md)

[View-Element (Format)](./view-element-format.md)

[WideEntries-Element (Format)](./wideentries-element-for-widecontrol-format.md)

[Breite Ansicht (Basic)](./wide-view-basic.md)

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
