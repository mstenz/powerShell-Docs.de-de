---
title: Customcontrolname-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368879"
---
# <a name="customcontrolname-element-for-groupby-format"></a>Element „CustomControlName“ für GroupBy (Format)

Gibt den Namen eines benutzerdefinierten Steuer Elements an, das zum Anzeigen der neuen Gruppe verwendet wird. Dieses Element wird verwendet, wenn eine Tabelle, eine Liste, eine Breite oder eine benutzerdefinierte Steuerelement Ansicht definiert wird.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) customcontrolname-Element von GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und die übergeordneten Elemente des `CustomControlName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)|Definiert, wie Windows PowerShell eine neue Gruppe von Objekten anzeigt.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des benutzerdefinierten Steuer Elements an, das verwendet wird, um eine neue Gruppe anzuzeigen.

## <a name="remarks"></a>Hinweise

Sie können allgemeine Steuerelemente erstellen, die von allen Ansichten einer Formatierungs Datei verwendet werden können, und Sie können Ansichts Steuerelemente erstellen, die von einer bestimmten Ansicht verwendet werden können. Die folgenden Elemente geben die Namen dieser benutzerdefinierten Steuerelemente an:

- [Name-Element für Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-Element für Steuerelemente für Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[GroupBy-Element für Ansicht (Format)](./groupby-element-for-view-format.md)

[Name-Element für Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-Element für Steuerelemente für Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
