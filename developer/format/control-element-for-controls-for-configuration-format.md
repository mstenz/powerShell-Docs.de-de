---
title: Control-Element für Konfiguration (Format) für Steuerelemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066792"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Element „Control“ für Controls für Configuration (Format)

Definiert ein allgemeines Steuerelement, das von allen Ansichten die Formatierungsdatei und den Namen, der verwendet wird, verweisen auf das Steuerelement verwendet werden kann.

Konfigurationselement-Element (Format)-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für die Konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element für die `Control` Element. Sie müssen nur eine jedes untergeordneten Elements angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomControl-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Erforderliches Element.<br /><br /> Definiert das Steuerelement an.|
|[Name-Element für das Steuerelement für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)|Erforderliches Element.<br /><br /> Gibt den Namen verwendet, um das Steuerelement zu verweisen.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Controls-Element (Format)-Konfiguration](./controls-element-for-configuration-format.md)|Definiert die allgemeinen Steuerelemente, die von allen Ansichten des die Formatierungsdatei oder von anderen Steuerelementen verwendet werden können.|

## <a name="remarks"></a>Hinweise

Der Name für dieses Steuerelement kann in den folgenden Elementen verwiesen werden:

- [ExpressionBinding-Element für CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy-Element für View(Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[Controls-Element (Format)-Konfiguration](./controls-element-for-configuration-format.md)

[CustomControl-Element für das Steuerelement für die Konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding-Element für CustomItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy-Element für View(Format)](./groupby-element-for-view-format.md)

[Name-Element für das Steuerelement für die Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
