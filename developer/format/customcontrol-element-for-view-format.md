---
title: CustomControl-Element für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861256"
---
# <a name="customcontrol-element-for-view-format"></a>Element „CustomControl“ für View (Format)

Definiert ein benutzerdefiniertes Steuerelement-Format für die Ansicht.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomControl` Element. Sie müssen ein untergeordnetes Element angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Erforderliches Element.<br /><br /> Enthält die Definitionen der benutzerdefinierten Steuerelements an.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die verwendet wird, um eine oder mehrere .NET Objekte anzuzeigen.|

## <a name="remarks"></a>Hinweise

Klicken Sie in den meisten Fällen nur eine Definition für jede Ansicht des Steuerelement erforderlich ist, aber es ist möglich, mehrere Definitionen bereitstellen, sollten Sie die gleiche Ansicht zu verwenden, um verschiedene .NET Objekte anzuzeigen. In diesen Fällen können Sie eine separate Definition für jedes Objekt bzw. den Satz von Objekten bereitstellen.

## <a name="see-also"></a>Weitere Informationen

[CustomEntries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[View-Element (Format)](./view-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
