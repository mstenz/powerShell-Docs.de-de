---
title: SelectionSetName-Element für EntrySelectedBy für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859d2335-7fcd-4efd-b1cc-3d171e334c6b
caps.latest.revision: 7
ms.openlocfilehash: f4bf820be88919af43eeaf043b3ed8b9c06e1bf2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063972"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a>Element „SelectionSetName“ für EntrySelectedBy für CustomControl für View (Format)

Gibt einen Satz von .NET-Objekten für den Listeneintrag. Es gibt keine Beschränkung der Anzahl der von Auswahlgruppen, die nach einem Eintrag angegeben werden können.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) EntrySelectedBy -Element für CustomEntry für Ansicht (Format) SelectionSetName-Element für EntrySelectedBy für CustomEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für CustomEntry für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definiert die .NET-Typen, die dieser benutzerdefinierten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Satzes Auswahl.

## <a name="remarks"></a>Hinweise

Jeder Eintrag benutzerdefiniertes Steuerelement muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.

Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten. Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen. Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren die Auswahl wird](./defining-selection-sets.md).

Weitere Informationen zu den Komponenten einer Ansicht des benutzerdefinierten Steuerelements finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

## <a name="see-also"></a>Weitere Informationen

[EntrySelectedBy-Element für CustomEntry für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Benutzerdefiniertes Steuerelement anzeigen](./creating-custom-controls.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
