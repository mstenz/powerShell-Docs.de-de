---
title: Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f23ef405-0f1e-4607-b3f4-4017b7ead106
caps.latest.revision: 7
ms.openlocfilehash: a5098da55d0a63272a121b973cb05e26dc47e3e1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368449"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a>Element „SelectionCondition“ für EntrySelectedBy für Controls für Configuration (Format)

Definiert eine Bedingung, die vorhanden sein muss, damit eine allgemeine Steuerelement Definition verwendet werden muss. Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.

Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl für Steuerelemente Configuration (Format) customentry-Element für CustomControl für Steuerelemente für das Configuration (Format) entryselectedby-Element für customentry für Steuerelemente für Configuration (Format) selectioncondition-Element für entryselectedby für customentry für Konfiguration (Format)

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

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `SelectionCondition`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[PropertyName-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt eine .net-Eigenschaft an, die die Bedingung auslöst.|
|[ScriptBlock-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das die Bedingung auslöst.|
|[Selectionsetname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt den Satz von .NET-Typen an, der die Bedingung auslöst.|
|[Typname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ an, der die Bedingung auslöst.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Definiert die .NET-Typen, die diesen Eintrag der allgemeinen Steuerelement Definition verwenden.|

## <a name="remarks"></a>Hinweise

Die folgenden Richtlinien müssen befolgt werden, wenn eine Auswahlbedingung definiert wird:

- Die Auswahlbedingung muss mindestens einen Eigenschaften Namen oder einen Skriptblock angeben, kann jedoch nicht beides angeben.

- Die Auswahlbedingung kann eine beliebige Anzahl von .NET-Typen oder-Auswahl Sätzen angeben, kann jedoch nicht beides angeben.

Weitere Informationen zur Verwendung von Auswahl Bedingungen finden Sie unter [Definieren von Bedingungen für die Anzeige von Daten](./defining-conditions-for-displaying-data.md).

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[ScriptBlock-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Selectionsetname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Typname-Element für selectioncondition für Steuerelemente für die Konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei](./writing-a-powershell-formatting-file.md)
