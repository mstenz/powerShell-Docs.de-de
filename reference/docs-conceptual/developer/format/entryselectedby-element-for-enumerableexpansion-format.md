---
title: Entryselectedby-Element für enumerableexpansion (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3af6aff8-4c2d-4f08-9bb1-e1f3ed3e583e
caps.latest.revision: 11
ms.openlocfilehash: 6a371bdbb85d07730c32931a4a79ee40856ce298
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368799"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a>Element „EntrySelectedBy“ für EnumerableExpansion (Format)

Definiert die .NET-Typen, die diese Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.

Configuration-Element (Format) DefaultSettings-Element (Format) enumerableerweiterungen-Element (Format) enumerableweiterung-Element (Format) entryselectedby-Element für enumerableweiterung (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, um die Auflistungs Objekte dieser Definition zu erweitern.|
|[Selectionsetname-Element für entryselectedby für enumerableexpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Gibt eine Gruppe von .NET-Typen an, die diese Definition der Erweiterung von Auflistungs Objekten verwenden.|
|[Typname-Element für entryselectedby für enumerableweiterung (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ an, der diese Definition der Erweiterung von Auflistungs Objekten verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Enumerableweiterung-Element (Format)](./enumerableexpansion-element-format.md)|Definiert, wie bestimmte .net-Auflistungs Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für einen Definitions Eintrag angeben. Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.

Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt über eine bestimmte Eigenschaft verfügt oder ein bestimmter Eigenschafts Wert oder Skript zu `true` ausgewertet wird. Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md)

[Enumerableweiterung-Element (Format)](./enumerableexpansion-element-format.md)

[Selectioncondition-Element für entryselectedby für enumerableweiterung (Format)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Selectionsetname-Element für entryselectedby für enumerableexpansion (Format)](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Typname-Element für entryselectedby für enumerableweiterung (Format)](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
