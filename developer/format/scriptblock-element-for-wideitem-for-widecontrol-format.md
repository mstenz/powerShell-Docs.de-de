---
title: ScriptBlock-Element für WideItem für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858026"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Element „ScriptBlock“ für WideItem für WideControl (Format)

Gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry-Element (Format) WideItem-Element (Format) "scriptblock" Konfigurationselement für WideItem (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ScriptBlock` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[WideItem-Element (Format)](./wideitem-element-for-widecontrol-format.md)|Definiert die Eigenschaft oder ein Skript-Block, dessen Wert in der breiten Ansicht angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie das Skript, dessen Wert angezeigt wird.

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `WideItem` Element, das ein Skript definiert, deren Wert in der Ansicht angezeigt wird.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Weitere Informationen

[WideItem-Element (Format)](./wideitem-element-for-widecontrol-format.md)

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
