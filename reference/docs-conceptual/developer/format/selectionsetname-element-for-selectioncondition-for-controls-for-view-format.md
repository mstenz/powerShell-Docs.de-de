---
title: Selectionsetname-Element für selectioncondition für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: daea8c6f-873a-4639-9eee-599642822958
caps.latest.revision: 6
ms.openlocfilehash: 697f2ea284393ebddd77a862c408f27f3d332900
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361969"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-view-format"></a>Element „SelectionSetName“ für SelectionCondition für Controls für View (Format)

Gibt den Satz von .NET-Typen an, die die Bedingung auslöst. Wenn einer der Typen in diesem Satz vorhanden ist, wird die Bedingung erfüllt, und das Objekt wird mithilfe dieses Steuer Elements angezeigt. Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für das View (Format) customentry-Element für customentries für Steuerelemente für das View (Format) entryselectedby-Element für customentry für Steuerelemente für das View (Format) selectioncondition-Element für entryselectedby für Steuerelemente für View ( Format) selectionsetname-Element für selectioncondition für Steuerelemente für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|Definiert eine Bedingung, die vorhanden sein muss, damit die Steuerelement Definition verwendet werden muss.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Auswahl Satzes an.

## <a name="remarks"></a>Hinweise

Auswahl Sätze sind allgemeine Gruppen von .NET-Objekten, die von jeder Sicht verwendet werden können, die von der Formatierungs Datei definiert wird. Weitere Informationen zum Erstellen und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Auswahl Sätzen](./defining-selection-sets.md).

Die Auswahlbedingung kann einen Auswahl Satz oder einen .NET-Typ angeben, kann jedoch nicht beides angeben. Weitere Informationen zum Verwenden von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen zum Anzeigen von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[Selectioncondition-Element für entryselectedby für Steuerelemente für View (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md)

[Definieren von Auswahl Sätzen](./defining-selection-sets.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
