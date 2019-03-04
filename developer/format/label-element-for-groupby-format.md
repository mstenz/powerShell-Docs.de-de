---
title: Versehen Sie Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862396"
---
# <a name="label-element-for-groupby-format"></a>Element „Label“ für GroupBy (Format)

Gibt eine Bezeichnung, die angezeigt wird, wenn eine neue Gruppe gefunden wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Ansicht (Format)-Beschriftungselement für die GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `Label` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)|Definiert, wie eine neue Gruppe von Objekten angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie den Text, der angezeigt wird, wenn Windows PowerShell eine neue Eigenschaft oder eines Werts trifft.

## <a name="remarks"></a>Hinweise

Zusätzlich zu den Text, der von diesem Element angegeben wird zeigt Windows PowerShell den neuen Wert, der die Gruppe beginnt und eine leere Zeile vor und nach der Gruppe eingefügt.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Bezeichnung für eine neue Gruppe. Die angezeigte Bezeichnung würde etwa wie folgt aussehen: `Service Type: NewValueofProperty`

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

Ein Beispiel für eine vollständige Formatierung-Datei, die dieses Element enthält, finden Sie unter [Breite Ansicht (-GroupBy)](./wide-view-groupby.md).

## <a name="see-also"></a>Weitere Informationen

[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
