---
title: TypeName-Element für SelectionCondition für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083857"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a>Element „TypeName“ für SelectionCondition für EntrySelectedBy für ListControl (Format)

Gibt einen .NET-Typ, der die Bedingung auslöst. Wenn dieses Typs vorhanden ist, wird der Listeneintrag verwendet.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListControl (Format) ListEntry-Element für ListEntries für ListControl (Format) EntrySelectedBy-Element für ListEntry für ListControl (Format) SelectionCondition-Element für EntrySelectedBy für ListControl (Format) TypeName-Element für SelectionCondition für EntrySelectedBy für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionCondition-Element für EntrySelectedBy für ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|Definiert die Bedingung, die für diesen Eintrag der Liste zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Hinweise

Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben. Weitere Informationen zur Verwendung von auswahlbedingungen finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu anderen die Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md)

[SelectionCondition-Element für EntrySelectedBy für ListControl (Format)](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
