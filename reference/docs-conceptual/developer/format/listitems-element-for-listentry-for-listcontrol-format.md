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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362739"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a>Element „ListItems“ für ListEntry für ListControl (Format)

Definiert die Eigenschaften und Skripts, deren Werte in den Zeilen der Listenansicht angezeigt werden.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für Listen Steuerelement (Format) ListEntry-Element für ListControl (Format) ListItems-Element für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `ListItems`-Elements beschrieben. Es gibt keine Beschränkung für die Anzahl der untergeordneten Elemente, die angegeben werden können. Die Reihenfolge der untergeordneten Elemente definiert die Reihenfolge, in der Werte in der Listenansicht angezeigt werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ListItem-Element für ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Erforderliches Element.<br /><br /> Definiert die Eigenschaft oder das Skript, dessen Wert in der Listenansicht angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ListEntry-Element für ListControl (Format)](./listentry-element-for-listcontrol-format.md)|Stellt eine Definition der Listenansicht bereit.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu dieser Art der Ansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt die XML-Elemente, die drei Zeilen der Listenansicht definieren.

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

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
