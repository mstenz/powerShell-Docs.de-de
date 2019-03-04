---
title: SelectionSetName-Element für EntrySelectedBy für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856796"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a>Element „SelectionSetName“ für EntrySelectedBy für WideControl (Format)

Gibt einen Satz von .NET-Objekten für die Definition. Die Definition wird verwendet, wenn eines dieser Objekte angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für WideEntry (Format) SelectionSetName-Element für EntrySelectedBy für WideEntry (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definiert die .NET-Typen, die dieser breiten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Satzes Auswahl.

## <a name="remarks"></a>Hinweise

Jede Definition muss ein Typname, Auswahlsatz oder auswahlbedingung angeben.

Auswahl legt werden normalerweise verwendet, wenn Sie eine Gruppe von Objekten, die verwendet werden in mehreren Ansichten definieren möchten. Beispielsweise empfiehlt es sich um eine Tabellenansicht und eine Ansicht für den gleichen Satz von Objekten zu erstellen. Weitere Informationen zu Auswahl definieren, finden Sie unter [definieren legt der Objekte für eine Sicht](./defining-selection-sets.md).

Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Auswahl definieren](./defining-selection-sets.md)

[EntrySelectedBy-Element für WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
