---
title: CustomEntries-Element für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066514"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>Element „CustomEntries“ für CustomControl für View (Format)

Enthält die Definitionen der benutzerdefinierten Steuerelements an. Die Ansicht benutzerdefiniertes Steuerelement muss eine oder mehrere Definitionen angegeben werden.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomControlEntries` Element. Sie müssen eine oder mehrere untergeordnete Elemente angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomEntries für Ansicht (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|Erforderliches Element.<br /><br /> Stellt eine Definition der benutzerdefinierten Steuerelements an.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomControl-Element für die Ansicht (Format)](./customcontrol-element-for-view-format.md)|Erforderliches Element.<br /><br /> Definiert ein benutzerdefiniertes Steuerelement-Format für die Ansicht.|

## <a name="remarks"></a>Hinweise

In den meisten Fällen ein Steuerelement verfügt über nur eine Definition, die in einem einzelnen definiert ist `CustomEntry` Element. So ist es jedoch möglich, mehrere Definitionen zu besitzen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen. In diesen Fällen können Sie definieren eine `CustomEntry` -Element für jedes Objekt oder eine Gruppe von Objekten.

## <a name="see-also"></a>Weitere Informationen

[CustomControl-Element für die Ansicht (Format)](./customcontrol-element-for-view-format.md)

[CustomEntry-Element für CustomEntries für Ansicht (Format)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
