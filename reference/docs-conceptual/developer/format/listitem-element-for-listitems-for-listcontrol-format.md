---
title: ListItem-Element für ListItems für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365129"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Element „ListItem“ für ListItems für ListControl (Format)

Definiert die Eigenschaft oder das Skript, dessen Wert in einer Zeile der Listenansicht angezeigt wird.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für ListControl (Format) ListEntry-Element für ListControl (Format) ListItems-Element für ListControl (Format) ListItem für ListControl-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `ListItem`-Elements beschrieben. Es kann nur eine Eigenschaft oder ein Skript angegeben werden.

### <a name="attributes"></a>Attributes

Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[FormatString-Element für ListItem für ListControl (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt eine Format Zeichenfolge an, die definiert, wie der Eigenschafts-oder Skript Wert angezeigt wird.|
|[Itemselectioncondition-Element für ListItem für ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit dieses Listenelement verwendet werden muss.|
|[Label-Element für ListItem für ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md)|Optionales Element<br /><br /> Gibt die Bezeichnung an, die auf der linken Seite des Eigenschafts-oder Skript Werts in der Zeile angezeigt wird.|
|[PropertyName-Element für ListItem für ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt die .net-Eigenschaft an, deren Wert in der Zeile angezeigt wird.|
|[ScriptBlock-Element für ListItem für ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert in der Zeile angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ListItems-Element für Listen Steuer Element (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definiert die Eigenschaften und Skripts, deren Werte in der Listenansicht angezeigt werden.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt die XML-Elemente, die drei Zeilen der Listenansicht definieren. Die ersten beiden Zeilen zeigen den Wert einer .net-Eigenschaft an, und die letzte Zeile zeigt einen Wert an, der von einem Skript generiert wurde.

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a>Weitere Informationen

[ListItems-Element (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)

[FormatString-Element für ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Label-Element für ListItem (Format)](./label-element-for-listitem-for-listcontrol-format.md)

[PropertyName-Element für ListItem (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ScriptBlock-Element für ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei](./writing-a-powershell-formatting-file.md)
