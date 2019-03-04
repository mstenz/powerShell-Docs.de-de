---
title: GroupBy-Element für die Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859526"
---
# <a name="groupby-element-for-view-format"></a>Element „GroupBy“ für View (Format)

Definiert, wie eine neue Gruppe von Objekten angezeigt wird. Dieses Element wird verwendet, bei der Definition einer Tabelle, Liste, breit oder benutzerdefiniertes Steuerelement anzeigen.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomControl-Element für GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert das benutzerdefinierte Steuerelement, in denen neue Gruppen angezeigt.|
|[CustomControlName-Element für GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines Steuerelements, die verwendet wird, um die neue Gruppe anzuzeigen.|
|[Label-Element für die GroupBy (Format)](./label-element-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt eine Bezeichnung, die angezeigt wird, wenn eine neue Gruppe gefunden wird.|
|[PropertyName-Element für GroupBy (Format)](./propertyname-element-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt an, die .NET-Eigenschaft der beginnt eine neue Gruppe, wenn sich der Wert ändert.|
|[ScriptBlock-Element für GroupBy (Format)](./scriptblock-element-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, in dem ein oder mehrere .NET Objekte angezeigt.|

## <a name="remarks"></a>Hinweise

Wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird, müssen Sie angeben, die Eigenschaft oder ein Skript, das die neue Gruppe gestartet wird; Sie können nicht jedoch beides angeben.

## <a name="see-also"></a>Weitere Informationen

[CustomControlName-Element für GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

[Label-Element für die GroupBy (Format)](./label-element-for-groupby-format.md)

[PropertyName-Element für GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[ScriptBlock-Element für GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[View-Element (Format)](./view-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
