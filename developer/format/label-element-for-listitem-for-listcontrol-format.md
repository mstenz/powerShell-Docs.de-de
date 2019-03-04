---
title: Bezeichnen Sie Element für ListControl (Format) für den ListItem | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854776"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Element „Label“ für ListItem für ListControl (Format)

Gibt die Bezeichnung, die auf der linken Seite des Eigenschaft oder des Skripts in der Zeile angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListControl (Format) ListEntry-Element für ListControl (Format) ListItems für ListEntry für ListControl-Element ( ListItem-Element für ListItems für ListControl (Format)-Label-Element für den ListItem für ListControl (Format)-Format)

## <a name="syntax"></a>Syntax

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Label` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListItem-Element für ListItems für ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie die Bezeichnung, um die Anzeige auf der linken Seite des Eigenschaft oder des Skripts werden.

## <a name="remarks"></a>Hinweise

Wenn eine Bezeichnung nicht angegeben ist, wird der Name der Eigenschaft oder des Skripts angezeigt. Weitere Informationen zum Verwenden von Bezeichnungen in einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie eine Bezeichnung auf eine Zeile hinzuzufügen.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[ListItem-Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
