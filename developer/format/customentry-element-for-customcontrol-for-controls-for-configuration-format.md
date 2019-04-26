---
title: CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066469"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Element „CustomEntry“ für CustomControl für Controls für Configuration (Format)

Stellt eine Definition des allgemeinen-Steuerelements. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)-Format)

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
|[EntrySelectedBy-Element für CustomEntry für Steuerelemente für die Konfiguration (Format)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die Typen von .NET, mit denen die Definition eines allgemeinen Steuerelement oder die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.|
|[CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|Erforderliches Element.<br /><br /> Definiert, welche Daten vom Steuerelement angezeigt werden und wie diese angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntries-Element für CustomControl für Konfiguration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|Enthält die Definitionen des allgemeinen-Steuerelements.|

## <a name="remarks"></a>Hinweise

Klicken Sie in den meisten Fällen nur eine Definition für die einzelnen common benutzerdefinierten Steuerelemente erforderlich ist, aber es ist möglich, mehrere Definitionen zu besitzen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen. In diesen Fällen können Sie eine separate Definition für jedes Objekt bzw. den Satz von Objekten bereitstellen.

## <a name="see-also"></a>Weitere Informationen

[CustomEntries-Element für CustomControl für Konfiguration (Format)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[CustomItem-Element für CustomEntry für Steuerelemente für die Konfiguration](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
