---
title: Entryselectedby-Element für customentry für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a317d482-73cc-4c98-a002-1357fa879cd7
caps.latest.revision: 7
ms.openlocfilehash: cf1a80e845c38d97d71f26eba63c38a550958b79
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363859"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a>Element „EntrySelectedBy“ für CustomEntry für GroupBy (Format)

Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss. Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format) entryselectedby-Element für customentry für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `EntrySelectedBy`-Elements beschrieben. Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für eine Definition angeben. Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Selectioncondition-Element für entryselectedby für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.|
|[Selectionsetname-Element für entryselectedby für GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen an, die diese Definition des-Steuer Elements verwenden.|
|[Tyname-Element für entryselectedby für GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ an, der diese Definition des-Steuer Elements verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für CustomControl für GroupBy (Format)](./customentry-element-for-customcontrol-for-groupby-format.md)|Stellt eine Definition des-Steuer Elements bereit.|

## <a name="remarks"></a>Hinweise

Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für die zu verwendende Definition vorhanden sein muss, z. b. Wenn ein Objekt eine bestimmte Eigenschaft hat oder wenn ein bestimmter Eigenschafts Wert oder ein Skript zu `true`ausgewertet wird. Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder eines Elements](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[Selectioncondition-Element für entryselectedby für GroupBy (Format)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[Selectionsetname-Element für entryselectedby für GroupBy (Format)](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[Tyname-Element für entryselectedby für GroupBy (Format)](./typename-element-for-entryselectedby-for-groupby-format.md)

[Customentry-Element für customentries für Steuerelemente für Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
