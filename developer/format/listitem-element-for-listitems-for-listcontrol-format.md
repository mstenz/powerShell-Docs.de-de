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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855156"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a>Element „ListItem“ für ListItems für ListControl (Format)

Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries Konfigurationselement für ListControl (Format) ListEntry-Element für ListControl (Format) ListItems-Element für ListControl (Format) ListItem für ListControl-Element (Format)

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

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ListItem` Element. Nur eine Eigenschaft oder ein Skript kann angegeben werden.

### <a name="attributes"></a>Attributes

Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[FormatString-Element für den ListItem für ListControl (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt eine Zeichenfolge, die definiert, wie der Wert der Eigenschaft oder ein Skript angezeigt wird.|
|[ItemSelectionCondition-Element für den ListItem für ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die für dieses Listenelement zu verwendende vorhanden sein muss.|
|[Label-Element für den ListItem für ListControl (Format)](./label-element-for-listitem-for-listcontrol-format.md)|Optionales element<br /><br /> Gibt die Bezeichnung, die auf der linken Seite des Eigenschaft oder des Skripts in der Zeile angezeigt wird.|
|[PropertyName-Element für den ListItem für ListControl (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt die .NET-Eigenschaft, deren Wert in der Zeile angezeigt wird.|
|[ScriptBlock-Element für den ListItem für ListControl (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, dessen Wert in der Zeile angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListItems-Element für das Listensteuerelement (Format)](./listitems-element-for-listentry-for-listcontrol-format.md)|Definiert die Eigenschaften und Skripts, deren Werte in der Listenansicht angezeigt werden.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt die XML-Elemente, die drei Zeilen der Listenansicht zu definieren. Die ersten beiden Zeilen den Wert einer Eigenschaft für die .NET anzeigen, und die letzte Zeile zeigt einen Wert, der durch ein Skript generiert.

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

[FormatString-Element für den ListItem (Format)](./formatstring-element-for-listitem-for-listcontrol-format.md)

[Label-Element für den ListItem (Format)](./label-element-for-listitem-for-listcontrol-format.md)

[PropertyName-Element für den ListItem (Format)](./propertyname-element-for-listitem-for-listcontrol-format.md)

[ScriptBlock-Element für den ListItem (Format)](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei](./writing-a-powershell-formatting-file.md)
