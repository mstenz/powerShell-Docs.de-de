---
title: SelectionSet-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368379"
---
# <a name="selectionset-element-format"></a>Element „SelectionSet“ (Format)

Definiert einen Satz von .NET-Objekten, auf die durch den Namen des Satzes verwiesen werden kann.

Configuration-Element (Format) selectionsets-Element (Format) SelectionSet-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `SelectionSet`-Elements beschrieben. Jeder Auswahl Satz muss über einen Namen verfügen, und er muss die .NET-Objekte des Satzes angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Name-Element für SelectionSet (Format)](./name-element-for-selectionset-format.md)|Erforderliches Element.<br /><br /> Gibt den Namen an, mit dem auf den Auswahl Satz verwiesen wird.|
|[Types-Element (Format)](./types-element-for-selectionset-format.md)|Erforderliches Element.<br /><br /> Definiert die .NET-Objekte, die sich im Auswahl Satz befinden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Selectionsets-Element Format](./selectionsets-element-format.md)|Definiert die allgemeinen Sätze von .NET-Objekten, die von allen Sichten der Formatierungs Datei verwendet werden können.|

## <a name="remarks"></a>Hinweise

Sie können Auswahl Sätze verwenden, wenn Sie über einen Satz verwandter Objekte verfügen, auf die Sie verweisen möchten, indem Sie einen einzelnen Namen verwenden, z. b. eine Gruppe von Objekten, die durch Vererbung verknüpft sind. Wenn Sie die Ansichten definieren, können Sie den Satz von-Objekten angeben, indem Sie den Namen des Auswahl Satzes verwenden, anstatt alle Objekte in jeder Ansicht aufzulisten.

Beim Definieren der Sichten der Formatierungs Datei oder der Definitionen der Sichten werden allgemeine Auswahl Sätze durch ihren Namen angegeben. In diesen Fällen gibt das `SelectionSetName` untergeordnete Element der `ViewSelectedBy`-und `EntrySelectedBy`-Elemente die zu verwendende Gruppe an. Weitere Informationen zu Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein `SelectionSet`-Element, das vier .NET-Typen definiert.

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a>Weitere Informationen

[Definieren von Auswahl Sätzen](./defining-selection-sets.md)

[Name-Element von SelectionSet (Format)](./name-element-for-selectionset-format.md)

[Selectionsets-Element (Format)](./selectionsets-element-format.md)

[Types-Element (Format)](./types-element-for-selectionset-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
