---
title: ListItems-Element für ListEntry für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065239"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Element „ListItems“ für ListEntry für ListControl (Format)

Definiert die Eigenschaften und Skripts, deren Werte in den Zeilen der Listenansicht angezeigt werden.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für Liste (Format) ListEntry Steuerelement für ListControl (Format) ListItems-Element für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ListItems` Element. Es gibt keine Beschränkung der Anzahl der untergeordneten Elemente, die angegeben werden können. Die Reihenfolge der untergeordneten Elemente definiert, die Reihenfolge, in der Werte in der Listenansicht angezeigt werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListItem-Element für ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Eigenschaft oder ein Skript, dessen Wert von der Listenansicht angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListEntry-Element für ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Stellt eine Definition der Listenansicht angezeigt.|

## <a name="remarks"></a>Hinweise

Weitere Informationen über diese Art von Ansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt die XML-Elemente, die drei Zeilen der Listenansicht zu definieren.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a>Weitere Informationen

[ListEntry-Element für ListControl (Format)](./listentry-element-for-listcontrol-format.md)

[ListItem-Element für ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
