---
title: Label-Element für ListItem für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362889"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a>Element „Label“ für ListItem für ListControl (Format)

Gibt die Bezeichnung an, die auf der linken Seite des Eigenschafts-oder Skript Werts in der Zeile angezeigt wird.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für ListControl (Format) ListEntry-Element für ListControl (Format) ListItems für ListEntry für ListControl-Element ( Format) ListItem-Element für ListItems für ListControl (Format) Label-Element für ListItem für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Label`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ListItem-Element für ListItems für ListControl (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)|Definiert die Eigenschaft oder das Skript, dessen Wert in einer Zeile der Listenansicht angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie die Bezeichnung an, die auf der linken Seite des Eigenschafts-oder Skript Werts angezeigt werden soll.

## <a name="remarks"></a>Hinweise

Wenn keine Bezeichnung angegeben ist, wird der Name der Eigenschaft oder des Skripts angezeigt. Weitere Informationen zum Verwenden von Bezeichnungen in einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie einer Zeile eine Bezeichnung hinzugefügt wird.

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[ListItem-Element (Format)](./listitem-element-for-listitems-for-listcontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
