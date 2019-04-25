---
title: ColumnNumber-Element für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe9eb5f9-a193-41a4-ad47-a96ba3f8d7e3
caps.latest.revision: 8
ms.openlocfilehash: 49f501538b8f72777984a5e575b999866abcdebf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066905"
---
# <a name="columnnumber-element-for-widecontrol-format"></a>Element „ColumnNumber“ für WideControl (Format)

Gibt die Anzahl der Spalten in der breiten Ansicht angezeigt.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) ColumnNumber Konfigurationselement für WideControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ColumnNumber>PositiveInteger</ColumnNumber>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ColumnNumber` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[WideControl-Element (Format)](./widecontrol-element-format.md)|Definiert eine Vielzahl (Einzelwert) Listenformat für die Ansicht.|

## <a name="text-value"></a>Textwert

Geben Sie eine positive ganze Zahl.

## <a name="remarks"></a>Hinweise

Wenn Sie eine Breite Ansicht definieren zu können, können Sie Hinzufügen der `AutoSize` Element oder die `ColumnNumber` -Element, aber Sie können nicht beide hinzufügen.

Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

Ein Beispiel für eine Breite Ansicht, finden Sie unter [Breite Ansicht (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[AutoSize-Element für WideControl (Format)](./autosize-element-for-widecontrol-format.md)

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Breite Ansicht (Basic)](./wide-view-basic.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
