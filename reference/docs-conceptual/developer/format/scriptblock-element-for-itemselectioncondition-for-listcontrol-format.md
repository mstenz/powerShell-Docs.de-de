---
title: ScriptBlock-Element für itemselectioncondition für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362099"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>Element „ScriptBlock“ für ItemSeclectionCondition für ListControl (Format)

Gibt das Skript an, das die Bedingung auslöst. Wenn dieses Skript zum `true`ausgewertet wird, wird die Bedingung erfüllt, und das Listenelement wird verwendet. Dieses Element wird beim Definieren einer Listenansicht verwendet.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) ListControl-Element (Format) ListEntries-Element für ListControl (Format) ListEntry-Element für ListEntries für ListControl (Format) ListItems-Element für ListEntry for ListControl (Format) ListItem-Element für ListItems für das Listen Steuerelement (Format) itemselectioncondition-Element für ListItem für ListControl (Format) ScriptBlock-Element für itemselectioncondition für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente des `ScriptBlock`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Itemselectioncondition-Element für ListItem für ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Definiert die Bedingung, die vorhanden sein muss, damit dieses Listenelement verwendet werden muss.|

## <a name="text-value"></a>Textwert

Geben Sie das auszuwertende Skript an.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, können Sie das `PropertyName`-Element beim Definieren der Auswahlbedingung nicht angeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
