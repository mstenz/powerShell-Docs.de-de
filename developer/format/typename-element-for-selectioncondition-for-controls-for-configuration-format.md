---
title: TypeName-Element für SelectionCondition für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083942"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>Element „TypeName“ für SelectionCondition für Controls für Configuration (Format)

Gibt einen .NET-Typ, der die Bedingung auslöst. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement-Element (Format)-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Steuerelemente für (-Format) CustomEntry Konfigurationselement für CustomControl für Steuerelemente für (Format) EntrySelectedBy Konfigurationselement für CustomEntry für Steuerelemente für (Format) SelectionCondition Konfigurationselement für EntrySelectedBy für CustomEntry für (-Format) TypeName Konfigurationselement für SelectionCondition für Steuerelemente für die Konfiguration (Format)

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
|[SelectionCondition-Element für EntrySelectedBy für CustomEntry für Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|Definiert eine Bedingung, die vorhanden sein muss, für die Definition des Steuerelements verwendet werden.|

## <a name="text-value"></a>Textwert

Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[SelectionCondition-Element für EntrySelectedBy für CustomEntry für Konfiguration (Format)](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
