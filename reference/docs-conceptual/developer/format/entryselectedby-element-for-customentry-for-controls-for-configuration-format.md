---
title: Entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368769"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a>Element „EntrySelectedBy“ für CustomEntry für Controls für Configuration (Format)

Definiert die .NET-Typen, die die Definition des allgemeinen Steuer Elements oder die Bedingung verwenden, die für die Verwendung dieses Steuer Elements vorhanden sein muss. Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.

Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für das Configuration (Format) entryselectedby-Element für customentry für Steuerelemente für die Konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
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
|[Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die Bedingung, die vorhanden sein muss, damit die allgemeine Steuerelement Definition verwendet werden muss.|
|[Selectionsetname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Typen an, die diese Definition des allgemeinen Steuer Elements verwenden.|
|[Typname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Gibt einen .NET-Typ an, der diese Definition des allgemeinen Steuer Elements verwendet.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Stellt eine Definition des allgemeinen Steuer Elements bereit.|

## <a name="remarks"></a>Hinweise

Für jede Definition muss mindestens ein .NET-Typ, ein Auswahl Satz oder eine Auswahlbedingung angegeben werden. Es gibt keine maximale Beschränkung für die Anzahl von Typen, Auswahl Sätzen oder Auswahl Bedingungen, die Sie angeben können.

## <a name="see-also"></a>Weitere Informationen

[Selectioncondition-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Selectionsetname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Customentry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Typname-Element für entryselectedby für Steuerelemente für die Konfiguration (Format)](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
