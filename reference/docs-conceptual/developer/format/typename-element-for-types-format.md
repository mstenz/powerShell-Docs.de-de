---
title: Typname-Element für Typen (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368029"
---
# <a name="typename-element-for-types-format"></a>Element „TypeName“ für Types (Format)

Gibt den .NET-Typ eines Objekts an, das zum Auswahl Satz gehört.

Configuration-Element (Format) selectionsets-Element (Format) SelectionSet-Element (Format) Types-Element (Format) Typname Element of Types (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `TypeName`-Elements beschrieben. Mindestens ein `TypeName` Element muss im Auswahl Satz enthalten sein.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Types-Element (Format)](./types-element-for-selectionset-format.md)|Definiert die .NET-Objekte, die sich im Auswahl Satz befinden.|

## <a name="text-value"></a>Textwert

Geben Sie den voll qualifizierten Namen des .net-Typs an.

## <a name="remarks"></a>Hinweise

Sie können Auswahl Sätze verwenden, wenn Sie über einen Satz verwandter Objekte verfügen, auf die Sie verweisen möchten, indem Sie einen einzelnen Namen verwenden, z. b. eine Gruppe von Objekten, die durch Vererbung verknüpft sind. Wenn Sie die Ansichten definieren, können Sie den Satz von-Objekten angeben, indem Sie den Namen des Auswahl Satzes verwenden, anstatt alle Objekte in jeder Ansicht aufzulisten.

Allgemeine Auswahl Sätze werden durch ihren Namen angegeben, wenn die Ansichten der Formatierungs Datei definiert werden. In diesen Fällen gibt das `SelectionSetName` untergeordnete Element des `ViewSelectedBy`-Elements für die Sicht den Satz an. Bei verschiedenen Einträgen einer Sicht kann jedoch auch ein Auswahl Satz angegeben werden, der nur für diesen Eintrag der Sicht gilt. Weitere Informationen zu Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein `SelectionSet`-Element, das vier .NET-Typen definiert.

```
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

[SelectionSet-Element (Format)](./selectionset-element-format.md)

[Selectionsets-Element (Format)](./selectionsets-element-format.md)

[Types-Element (Format)](./types-element-for-selectionset-format.md)

[Schreiben einer Windows PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
