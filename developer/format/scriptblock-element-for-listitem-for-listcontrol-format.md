---
title: ScriptBlock-Element für den ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064576"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a>Element „ScriptBlock“ für ListItem für ListControl (Format)

Gibt das Skript an, dessen Wert in der Zeile angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListEntry-Element für ListEntries für ListControl (Format) ListItems-Element für ListEntry ListControl (Format) für ListControl (Format) ListItem-Element für ListItems für ListControl (Format)-ScriptBlock-Element für ListItem für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListItem-Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie das Skript, das in der Zeile, deren Wert angezeigt wird.

## <a name="remarks"></a>Hinweise

Wenn dieses Element angegeben ist, können Sie nicht angeben der [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) Element.

Weitere Informationen zum Angeben von Skripts in einer Listenansicht finden Sie unter [Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie die Eigenschaft angeben, dessen Wert angezeigt wird.

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für den ListItem für ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[ListItem-Element für ListItems für ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
