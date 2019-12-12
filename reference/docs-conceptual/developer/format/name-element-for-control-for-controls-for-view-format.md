---
title: Name-Element für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365099"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>Element „Name“ für Control für Controls für View (Format)

Gibt den Namen des Steuer Elements an.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) Steuerelemente Element (Format) Steuerelement für Steuerelemente für Ansicht (Format) namens Element für Steuerelement für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `Name`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Control-Element für Steuerelemente für View (Format)](./control-element-for-controls-for-view-format.md)|Definiert ein Steuerelement, das von der Ansicht verwendet werden kann, und den Namen, der verwendet wird, um auf das Steuerelement zu verweisen.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen an, der zum Verweisen auf das Steuerelement verwendet wird.

## <a name="remarks"></a>Hinweise

Der hier angegebene Name kann in den folgenden Elementen verwendet werden, um auf dieses Steuerelement zu verweisen.

- Beim Erstellen einer Tabelle, einer Liste, einer breiten oder einer benutzerdefinierten Steuerelement Ansicht kann das Steuerelement vom folgenden Element angegeben werden: [GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)

- Wenn Sie ein weiteres Steuerelement erstellen, das von einer Ansicht verwendet werden kann, kann dieses Steuerelement vom folgenden Element angegeben werden: [ExpressionBinding-Element für customItem für Steuerelemente für View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)

[ExpressionBinding-Element für customItem für Steuerelemente für Ansicht (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[Control-Element für Steuerelemente für View (Format)](./control-element-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
