---
title: TypeName-Element für EntrySelectedBy für CustomEntry für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083976"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a>Element „TypeName“ für EntrySelectedBy für CustomEntry für View (Format)

Gibt einen .NET-Typ, ein, der dieser Definition der Sicht benutzerdefiniertes Steuerelement verwendet. Es gibt keine Beschränkung der Anzahl von Typen, die für eine Definition angegeben werden können.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) EntrySelectedBy -Element für CustomEntry für Ansicht (Format) TypeName-Element für EntrySelectedBy für CustomEntry für Ansicht (Format)

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
|[EntrySelectedBy-Element für CustomEntry für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Definiert .NET Typen, die dieser Definition des benutzerdefinierten Steuerelements anzeigen oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|

## <a name="text-value"></a>Textwert

Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Hinweise

Jede Definition des benutzerdefinierten Steuerelements anzeigen muss mindestens ein Typname, Auswahlsatz oder auswahlbedingung definiert haben.

Weitere Informationen zu den Komponenten einer Ansicht des benutzerdefinierten Steuerelements finden Sie unter [Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md)

[EntrySelectedBy-Element für CustomEntry für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
