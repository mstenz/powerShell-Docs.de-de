---
title: SelectionSetName-Element für EntrySelectedBy für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cff7763c-5ce0-49c1-a480-1249c9f57a13
caps.latest.revision: 11
ms.openlocfilehash: 7fd431b4b1ddecd3a7358c2bf97f299b97162b34
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075561"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a>Element „SelectionSetName“ für EntrySelectedBy für ListControl (Format)

Gibt einen Satz von .NET-Objekten für den Listeneintrag. Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) ListControl-Element (Format) ListEntries-Element (Format) ListEntry-Element (Format) EntrySelectedBy Konfigurationselement für ListEntry (Format) SelectionSetName-Element für EntrySelectedBy für ListEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `SelectionSetName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|Definiert die .NET-Typen, die diesen Eintrag der Liste oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Satzes Auswahl.

## <a name="remarks"></a>Hinweise

Jeder Listeneintrag muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.

Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten. Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen. Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren Sätze von Objekten, die für eine Sicht](./defining-selection-sets.md).

Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie eine Auswahl, legen Sie für einen Eintrag in einer Listenansicht angeben.

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[EntrySelectedBy-Element für ListEntry (Format)](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
