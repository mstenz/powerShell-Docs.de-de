---
title: Customcontrolname-Element für ExpressionBinding für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364109"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a>Element „CustomControlName“ für ExpressionBinding für CustomControl für View (Format)

Gibt den Namen eines allgemeinen Steuer Elements oder eines Ansichts Steuer Elements an. Dieses Element wird beim Definieren einer benutzerdefinierten Steuerelement Ansicht verwendet.

Konfigurationselement (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element für View (Format) customentries-Element für CustomControl for View (Format) customentry-Element für customentries for View (Format) customItem -Element für customentry für das View (Format) ExpressionBinding-Element für das customItem (Format) customcontrolname-Element für die Ausdrucks Bindung für customItem (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomControlName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ExpressionBinding-Element für customItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|Definiert die Daten, die vom-Steuerelement angezeigt werden.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Steuer Elements an.

## <a name="remarks"></a>Hinweise

Sie können allgemeine Steuerelemente erstellen, die von allen Ansichten einer Formatierungs Datei verwendet werden können, und Sie können Ansichts Steuerelemente erstellen, die von einer bestimmten Ansicht verwendet werden können. Die Namen dieser Steuerelemente werden durch die folgenden Elemente angegeben.

- [Name-Element für Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

- [Name-Element für Steuerelemente für Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>Weitere Informationen

[Name-Element für Steuerelemente für die Konfiguration (Format)](./name-element-for-control-for-controls-for-configuration-format.md)

[Name-Element für Steuerelemente für Ansicht (Format)](./name-element-for-control-for-controls-for-view-format.md)

[ExpressionBinding-Element für customItem (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
