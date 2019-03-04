---
title: CustomControlName-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860306"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Element „CustomControlName“ für GroupBy (Format)

Gibt den Namen eines benutzerdefinierten Steuerelements, die verwendet wird, um die neue Gruppe anzuzeigen. Dieses Element wird verwendet, bei der Definition einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Anzeigeelement (Format) CustomControlName GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Elemente von der `CustomControlName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)|Definiert, wie Windows PowerShell eine neue Gruppe von Objekten angezeigt.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des benutzerdefinierten Steuerelements, die verwendet wird, um eine neue Gruppe anzuzeigen.

## <a name="remarks"></a>Hinweise

Sie können allgemeine Steuerelemente, die von allen Ansichten des eine Formatierungsdatei verwendet werden können erstellen und Sie können Steuerelemente, die von einer bestimmten Ansicht verwendet werden können erstellen. Die folgenden Elemente geben Sie die Namen dieser benutzerdefinierten Steuerelemente:

- [Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

[Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-Element für das Steuerelement für die Steuerelemente für die Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
