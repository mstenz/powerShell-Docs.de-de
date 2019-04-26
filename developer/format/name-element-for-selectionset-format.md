---
title: Namen von Element für SelectionSet (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065154"
---
# <a name="name-element-for-selectionset-format"></a>Element „Name“ für SelectionSet (Format)

Gibt den Namen verwendet, um den Auswahlsatz zu verweisen.

Konfiguration-Element (Format) SelectionSets-Element (Format) SelectionSet-Element (Format)-Name-Element der SelectionSet (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `Name` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionSet-Element (Format)](./selectionset-element-format.md)|Definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen auf den Auswahlsatz verweisen. Es gibt keine Einschränkungen, welche Zeichen verwendet werden können.

## <a name="remarks"></a>Hinweise

Der hier angegebene Name wird verwendet, der `SelectionSetName` Element. Der Auswahlsatz, der durch eine Sicht, indem Sie eine Definition einer Sicht verwendet werden kann (Ansichten können hat mehrere Definitionen), oder wenn Sie eine auswahlbedingung angeben. Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `SelectionSet` -Element, das vier Typen von .NET definiert. Der Name des Satzes Auswahl ist "FileSystemTypes".

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

[Auswahl definieren](./defining-selection-sets.md)

[SelectionSet-Element (Format)](./selectionset-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
