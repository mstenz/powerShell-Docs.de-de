---
title: Element-Typen für SelectionSet (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862376"
---
# <a name="types-element-for-selectionset-format"></a>Element „Types“ für SelectionSet (Format)

Definiert die .NET Objekte, die in der Auswahl festgelegt werden.

-Element (Format) SelectionSets-Element (Format) SelectionSet Konfigurationselement (Format)-Typen (Format)-Element

## <a name="syntax"></a>Syntax

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Types` Element. Es muss mindestens ein untergeordnetes Element vorhanden sein, aber es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die hinzugefügt werden können.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TypeName-Element der Typen (Format)](./typename-element-for-types-format.md)|Erforderliches Element.<br /><br /> Gibt das .NET-Objekt, das auf die Auswahl gehört.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionSet-Element (Format)](./selectionset-element-format.md)|Definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.|

## <a name="remarks"></a>Hinweise

Die von diesem Element definierten Objekte bilden einen Auswahlsatz, die durch eine Sicht, indem Sie eine Definition einer Sicht verwendet werden kann (Ansichten können hat mehrere Definitionen), oder wenn Sie eine auswahlbedingung angeben.  Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert.

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

[Definieren von Gruppen von Objekten](./defining-selection-sets.md)

[SelectionSet-Element (Format)](./selectionset-element-format.md)

[TypeName-Element der Typen (Format)](./typename-element-for-types-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
