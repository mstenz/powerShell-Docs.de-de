---
title: TypeName-Element für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 3f0c0ba1fe85d70557e67a30b3a9a59a33043475
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856106"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a>Element „TypeName“ für EntrySelectedBy für ListControl (Format)

Gibt einen .NET-Typ, der diesen Eintrag der Listenansicht wird verwendet. Es gibt keine Beschränkung der Anzahl von Typen, die für einen Eintrag für eine angegeben werden können.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für TypeName-Element für ListEntry (Format) EntrySelectedBy für ListControl (Format)

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
|[EntrySelectedBy-Element für ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definiert die .NET-Typen, die diesen Eintrag der Liste oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Hinweise

Jeder Listeneintrag muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.

Weitere Informationen zur Verwendung dieses Elements in einer Listenansicht finden Sie unter [Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie eine Auswahl, legen Sie für einen Eintrag in einer Listenansicht angeben.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[EntrySelectedBy-Element für ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[SelectionSetName-Element für EnrtySelectedBy für ListEntry (Format)](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
