---
title: TypeName-Element für Typen (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057925"
---
# <a name="typename-element-for-types-format"></a>Element „TypeName“ für Types (Format)

Gibt den Typ .NET eines Objekts, das auf die Auswahl gehört.

Element (Format) SelectionSets-Element (Format) SelectionSet Konfigurationselement (Format)-Typen (Format)-Element TypeName-Element der Typen (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element. Mindestens ein `TypeName` Element in der Auswahl enthalten sein muss.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Types-Element (Format)](./types-element-for-selectionset-format.md)|Definiert die .NET Objekte, die in der Auswahl festgelegt werden.|

## <a name="text-value"></a>Textwert

Geben Sie den vollqualifizierten Namen für den Typ .NET.

## <a name="remarks"></a>Hinweise

Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten. Wenn Sie Ihre Ansichten definieren, können Sie den Satz von Objekten angeben, mit dem Namen der Markierung anstelle Auflisten aller Objekte in jeder Ansicht festgelegt.

Typische Auswahl Sets werden anhand ihres Namens angegeben, bei der Definition der Ansichten die Formatierungsdatei. In diesen Fällen die `SelectionSetName` untergeordnetes Element von der `ViewSelectedBy` das-Element für die Sicht angibt. Verschiedene Einträge einer Sicht können jedoch auch einen Auswahlsatz angeben, der für nur diesen Eintrag der Sicht gilt. Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert.

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

[Auswahl definieren](./defining-selection-sets.md)

[SelectionSet-Element (Format)](./selectionset-element-format.md)

[SelectionSets-Element (Format)](./selectionsets-element-format.md)

[Types-Element (Format)](./types-element-for-selectionset-format.md)

[Schreiben Sie eine Windows PowerShell Formatierungsdatei](./writing-a-powershell-formatting-file.md)
