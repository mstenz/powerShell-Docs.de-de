---
title: Benennen Sie Element für das Steuerelement für Steuerelemente für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065100"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Element „Name“ für Control für Controls für View (Format)

Gibt den Namen des Steuerelements.

-Element (Format) ViewDefinitions-Element (Format) Ansicht Konfigurationselement (Format) steuert Elementen (-Format)-Steuerelement für Steuerelemente für die Name-Anzeigeelement (Format) für Steuerelement für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>ControlName</Name>
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
|[Control-Element für Controls für Ansicht (Format)](./control-element-for-controls-for-view-format.md)|Definiert ein Steuerelement, das von der Ansicht und der Name, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen, der verwendet wird, um das Steuerelement zu verweisen.

## <a name="remarks"></a>Hinweise

Der hier angegebene Name kann in den folgenden Elementen verwendet werden, um auf um dieses Steuerelement zu verweisen.

- Beim Erstellen einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen, kann das Steuerelement vom folgenden Element angegeben werden: [GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

- Wenn Sie ein anderes Steuerelement erstellen, die von einer Ansicht verwendet werden kann, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

[ExpressionBinding-Element für CustomItem für Steuerelemente für die Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Control-Element für Controls für Ansicht (Format)](./control-element-for-controls-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
