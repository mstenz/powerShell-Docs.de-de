---
title: CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066497"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>Element „CustomEntry“ für CustomEntries für Controls für View (Format)

Stellt eine Definition des Steuerelements. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)

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
|[EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|Optionales Element.<br /><br /> Definiert die .NET-Typen, die die Definition dieses Steuerelements oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|
|[CustomItem-Element für CustomEntry für Steuerelemente für die Ansicht (Format)](./customitem-element-for-customentry-for-controls-for-view-format.md)|Erforderliches Element.<br /><br /> Definiert, wie das Steuerelement für die Daten anzeigt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Enthält die Definitionen für das Steuerelement an.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[CustomEntries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
