---
title: CustomEntries-Element für CustomControl für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066582"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Element „CustomEntries“ für CustomControl für Controls für View (Format)

Enthält die Definitionen für das Steuerelement an. Dieses Element wird verwendet, wenn Steuerelemente definieren, die von einer Ansicht verwendet werden kann.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Steuerelemente-Element (Format) Control-Element für Steuerelemente für die Ansicht (Format) CustomControl-Element für das Steuerelement für die Steuerelemente für Ansicht (Format) CustomEntries-Element für CustomControl für Steuerelemente für die Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente von der `CustomEntries` Element. Es ist nicht begrenzt auf die Anzahl der untergeordneten Elemente, die angegeben werden können.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Erforderliches Element.<br /><br /> Stellt eine Definition des Steuerelements.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Definiert das Steuerelement, das von der Ansicht verwendet.|

## <a name="remarks"></a>Hinweise

In den meisten Fällen hat ein Steuerelement nur eine Definition, die in einem einzelnen angegeben wird `CustomEntry` Element. Allerdings ist es möglich, mehrere Definitionen bereitzustellen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen. In diesen Fällen können Sie definieren eine `CustomEntry` -Element für jedes Objekt oder eine Gruppe von Objekten.

## <a name="see-also"></a>Weitere Informationen

[CustomEntry-Element für CustomEntries für Steuerelemente für die Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
