---
title: PropertyName-Element für den ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064914"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a>Element „PropertyName“ für ListItem für ListControl (Format)

Gibt die .NET-Eigenschaft, deren Wert in der Liste angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) ListItems-Element (Format) ListItem-Element (Format) PropertyName Konfigurationselement für ListItem (Format)

## <a name="syntax"></a>Syntax

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `PropertyName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListItem-Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definiert die Eigenschaft oder ein Skript, dessen Wert in der Zeile in der Listenansicht angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen der Eigenschaft, deren Wert angezeigt wird.

## <a name="remarks"></a>Hinweise

Wenn dieses Element angegeben ist, können Sie nicht angeben der ["scriptblock"](./scriptblock-element-for-listitem-for-listcontrol-format.md) Element.

Zusätzlich zur Anzeige der Wert der Eigenschaft, können Sie auch eine Bezeichnung für den Wert oder eine Zeichenfolge, die verwendet werden kann, so ändern Sie die Anzeige des Werts angeben. Weitere Informationen zum Angeben von Daten in einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie angeben, die Bezeichnung und die Eigenschaft, deren Wert angezeigt wird.

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Weitere Informationen

[ScriptBlock-Element für den ListItem für ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[ListItem-Element für ListControl(Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
