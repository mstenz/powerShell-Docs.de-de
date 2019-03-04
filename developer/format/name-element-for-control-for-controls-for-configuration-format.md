---
title: Benennen Sie Element für das Steuerelement für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860086"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Element „Name“ für Control für Controls für Configuration (Format)

Gibt den Namen des Steuerelements. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement-Element (Format)-Steuerelemente des Steuerelements für Konfiguration (Format) für die Steuerelemente für die Konfiguration (Format)-Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Name` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Control-Element für Controls für Konfiguration (Format)](./control-element-for-controls-for-configuration-format.md)|Definiert ein allgemeines Steuerelement, das von allen Ansichten die Formatierungsdatei und den Namen, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen, der verwendet wird, um auf dieses Steuerelement zu verweisen.

## <a name="remarks"></a>Hinweise

Der hier angegebene Name kann in den folgenden Elementen verwendet werden, um auf um dieses Steuerelement zu verweisen.

- Beim Erstellen einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen, kann das Steuerelement vom folgenden Element angegeben werden: [GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

- Wenn Sie einen anderen allgemeinen Steuerelements erstellen zu können, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- Beim Erstellen eines Steuerelements, die von einer Ansicht verwendet werden kann, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[Control-Element für Controls für Konfiguration (Format)](./control-element-for-controls-for-configuration-format.md)

[ExpressionBinding-Element für CustomItem für Steuerelemente für die Konfiguration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
