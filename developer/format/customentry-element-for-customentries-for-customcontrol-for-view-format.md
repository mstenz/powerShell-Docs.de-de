---
title: CustomEntry-Element für CustomEntries für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861816"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Element „CustomEntry“ für CustomEntries für CustomControl für View (Format)

Stellt eine Definition der benutzerdefinierten Steuerelements an.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomEntry` Element. Sie müssen die durch die Definition der angezeigten Elemente angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[EntrySelectedBy-Element für CustomEntry für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Definiert die Typen von .NET, mit denen die Definition der benutzerdefinierten Steuerelementansicht oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden.|
|[CustomItem-Element für CustomEntry für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definiert ein Steuerelement für die Definition des benutzerdefinierten Steuerelements.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Enthält die Definitionen der benutzerdefinierten Steuerelements an. Die Ansicht benutzerdefiniertes Steuerelement muss eine oder mehrere Definitionen angegeben werden.|

## <a name="remarks"></a>Hinweise

Klicken Sie in den meisten Fällen nur eine Definition für jede Ansicht benutzerdefiniertes Steuerelement erforderlich ist, aber es ist möglich, mehrere Definitionen zu besitzen, sollten Sie die gleiche Ansicht zu verwenden, um verschiedene .NET Objekte anzuzeigen. In diesen Fällen können Sie eine separate Definition für jedes Objekt bzw. den Satz von Objekten bereitstellen.

## <a name="see-also"></a>Weitere Informationen

[CustomControl-Element für die Ansicht (Format)](./customcontrol-element-for-view-format.md)

[CustomItem-Element für CustomEntry für Ansicht (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[EntrySelectedBy-Element für CustomEntry für Ansicht (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
