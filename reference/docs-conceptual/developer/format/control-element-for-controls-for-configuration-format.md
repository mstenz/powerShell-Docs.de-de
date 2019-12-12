---
title: Control-Element für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369009"
---
# <a name="control-element-for-controls-for-configuration-format"></a>Element „Control“ für Controls für Configuration (Format)

Definiert ein gängiges Steuerelement, das von allen Ansichten der Formatierungs Datei und dem Namen, der zum Verweisen auf das Steuerelement verwendet wird, verwendet werden kann.

Configuration-Element (Format) Controls-Element des Configuration (Format)-Steuer Elements für Steuerelemente für die Konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete-Element für das `Control`-Element beschrieben. Sie müssen nur eines der einzelnen untergeordneten Elemente angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element für Steuerelemente für die Konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Erforderliches Element.<br /><br /> Definiert das Steuerelement.|
|[Name-Element für das Steuer Element für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)|Erforderliches Element.<br /><br /> Gibt den Namen an, mit dem auf das Steuerelement verwiesen wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Controls-Element der Konfiguration (Format)](./controls-element-for-configuration-format.md)|Definiert die allgemeinen Steuerelemente, die von allen Ansichten der Formatierungs Datei oder von anderen Steuerelementen verwendet werden können.|

## <a name="remarks"></a>Hinweise

Auf den Namen, den dieses Steuerelement erhält, kann in den folgenden Elementen verwiesen werden:

- [ExpressionBinding-Element für customItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[Controls-Element der Konfiguration (Format)](./controls-element-for-configuration-format.md)

[CustomControl-Element für das Steuerelement für die Konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[ExpressionBinding-Element für customItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)

[Name-Element für Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
