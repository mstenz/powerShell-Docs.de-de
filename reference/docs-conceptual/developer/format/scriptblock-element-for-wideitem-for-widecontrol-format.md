---
title: ScriptBlock-Element für wideitem für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362029"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a>Element „ScriptBlock“ für WideItem für WideControl (Format)

Gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) wideitem-Element (Format) ScriptBlock-Element für wideitem (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `ScriptBlock`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Wideitem-Element (Format)](./wideitem-element-for-widecontrol-format.md)|Definiert den Eigenschafts-oder Skriptblock, dessen Wert in der breiten Ansicht angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie das Skript an, dessen Wert angezeigt wird.

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein `WideItem`-Element, das ein Skript definiert, dessen Wert in der Ansicht angezeigt wird.

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a>Weitere Informationen

[Wideitem-Element (Format)](./wideitem-element-for-widecontrol-format.md)

[Erstellen einer breiten Ansicht](./creating-a-wide-view.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
