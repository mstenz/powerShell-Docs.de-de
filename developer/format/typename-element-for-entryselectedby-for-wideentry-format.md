---
title: TypeName-Element für EntrySelectedBy für WideEntry (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083925"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>Element „TypeName“ für EntrySelectedBy für WideEntry (Format)

Gibt einen Typ .NET für die Definition. Die Definition wird verwendet, wenn dieses Objekt angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) Ansicht Element (Format) WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) EntrySelectedBy Konfigurationselement für TypeName-Element für WideEntry (WideEntry (Format) -Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `TypeName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)|Definiert die .NET-Typen, die dieser breiten Eintrag oder die Bedingung, die für diesen Eintrag zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Hinweise

Jeder Eintrag Breite muss angeben, einen oder mehrere Typen von .NET, einen Auswahlsatz oder die auswahlbedingung, die die Definition der zu verwendenden vorhanden sein muss.

Weitere Informationen zu weiteren Komponenten, der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

## <a name="see-also"></a>Weitere Informationen

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[EntrySelectedBy-Element für WideEntry (Format)](./entryselectedby-element-for-wideentry-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
