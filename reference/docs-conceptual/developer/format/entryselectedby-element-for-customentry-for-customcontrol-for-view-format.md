---
title: Entryselectedby-Element für customentry für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7828b45b-eabf-4432-b127-131b4ef0c800
caps.latest.revision: 8
ms.openlocfilehash: e7176f9f6ef67116ea7c07a46797fb0ba84f915d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368779"
---
# <a name="entryselectedby-element-for-customentry-for-customcontrol-for-view-format"></a>Element „EntrySelectedBy“ für CustomEntry für CustomControl für View (Format)

Definiert die .NET-Typen, die diesen benutzerdefinierten Eintrag verwenden, oder die Bedingung, die für die Verwendung dieses Eintrags vorhanden sein muss.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries for View (Format) entryselectedby Element für customentry für View (Format)

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
|[Selectioncondition-Element für entryselectedby für customentry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.|
|[Selectionsetname-Element für entryselectedby für customentry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen an, die diese Definition der Steuerelement Ansicht verwenden.|
|[Typname-Element für entryselectedby für customentry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ an, der diese Definition der Steuerelement Ansicht verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für customentries für View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Definiert die Steuerelemente, die von bestimmten .NET-Objekten verwendet werden.|

## <a name="remarks"></a>Hinweise

Sie müssen mindestens einen Typ, einen Auswahl Satz oder eine Auswahlbedingung für einen Eintrag angeben. Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die Sie verwenden können.

Auswahl Bedingungen werden verwendet, um eine Bedingung zu definieren, die für den zu verwendenden Eintrag vorhanden sein muss, z. b. Wenn ein Objekt eine bestimmte Eigenschaft hat oder wenn ein bestimmter Eigenschafts Wert oder ein Skript zu `true`ausgewertet wird. Weitere Informationen zu Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Verwendung eines Ansichts Eintrags oder eines Elements](./defining-conditions-for-displaying-data.md).

Weitere Informationen zu den Komponenten einer benutzerdefinierten Steuerelement Ansicht finden Sie unter [benutzerdefinierte Steuerelement Ansicht](./creating-custom-controls.md).

## <a name="see-also"></a>Weitere Informationen

[Selectioncondition-Element für entryselectedby für customentry (Format)](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[Selectionsetname-Element für entryselectedby für customentry (Format)](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

[Typname-Element für entryselectedby für customentry (Format)](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[Customentry-Element für customentries für View (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Benutzerdefinierte Steuerelement Ansicht](./creating-custom-controls.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
