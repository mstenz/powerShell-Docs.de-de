---
title: SelectionCondition-Element für EntrySelectedBy für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075765"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Element „SelectionCondition“ für EntrySelectedBy für Controls für Configuration (Format)

Definiert eine Bedingung, die vorhanden sein muss, für die Steuerelementdefinition eines allgemeinen verwendet werden. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement-Element (Format)-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Steuerelemente für (-Format) CustomEntry Konfigurationselement für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für (Format) SelectionCondition Konfigurationselement für EntrySelectedBy für CustomEntry für Konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionCondition` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[PropertyName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt eine .NET-Eigenschaft, die die Bedingung auslöst.|
|[ScriptBlock-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|
|[SelectionSetName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen, der die Bedingung auslöst.|
|[TypeName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definiert die .NET-Typen, die diesen Eintrag, der Steuerelementdefinition der allgemeinen zu verwenden.|

## <a name="remarks"></a>Hinweise

Wenn Sie eine auswahlbedingung zu definieren, müssen die folgenden Richtlinien eingehalten werden:

- Die auswahlbedingung muss einen Namen für mindestens eine Eigenschaft oder ein Skriptblock angeben, aber nicht beides angeben.

- Geben Sie die auswahlbedingung kann eine beliebige Anzahl von Typen in .NET oder Auswahl festgelegt, aber nicht beides angeben.

Weitere Informationen wie auswahlbedingungen verwendet werden können, finden Sie unter [Definieren von Bedingungen für, wenn die Daten angezeigt werden](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[SelectionSetName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[TypeName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei](./writing-a-powershell-formatting-file.md)
