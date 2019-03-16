---
title: ScriptBlock-Element für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054424"
---
# <a name="scriptblock-element-for-groupby-format"></a>Element „ScriptBlock“ für GroupBy (Format)

Gibt an, das Skript, das eine neue Gruppe wird gestartet, wenn sich der Wert ändert.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element GroupBy Konfigurationselement für Ansicht (Format)-ScriptBlock-Element für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ScriptBlock` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)|Definiert, wie eine Gruppe von .NET-Objekten angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie das Skript aus, das ausgewertet wird.

## <a name="remarks"></a>Hinweise

Windows PowerShell startet eine neue Gruppe aus, wenn der Wert dieses Skript ändert.

Wenn dieses Element angegeben ist, können Sie nicht angeben der [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) Element um eine neue Gruppe zu starten.

## <a name="see-also"></a>Weitere Informationen

[PropertyName-Element für GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[GroupBy-Element für die Ansicht (Format)](./groupby-element-for-view-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
