---
title: CustomEntry-Element für CustomControl für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860366"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Element „CustomEntry“ für CustomControl für GroupBy (Format)

Stellt eine Definition des Steuerelements. Dieses Element wird verwendet, wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für (Format) CustomControl Ansichtselement für GroupBy (Format) CustomEntries-Element für CustomControl für GroupBy (Format) CustomEntry-Element für CustomControl für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente der `CustomEntry` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für CustomEntry für GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|
|[CustomItem-Element für CustomEntry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Erforderliches Element.<br /><br /> Definiert, wie das Steuerelement für die Daten anzeigt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntries-Element für CustomControl für GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Enthält die Definitionen für das Steuerelement an.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[EntrySelectedBy-Element für CustomEntry für GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[CustomItem-Element für CustomEntry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[CustomEntries-Element für CustomControl für GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
