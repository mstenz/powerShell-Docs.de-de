---
title: ScriptBlock-Element für ItemSelectionCondition für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064406"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a>Element „ScriptBlock“ für ItemSeclectionCondition für ListControl (Format)

Gibt das Skript an, das die Bedingung auslöst. Wenn dieses Skript ergab `true`, die Bedingung erfüllt ist und das Element der Liste wird verwendet. Dieses Element wird verwendet, wenn Sie eine Ansicht zu definieren.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement für ListEntry-Element für ListEntries für ListControl (Format) ListItems-Element für ListEntry ListControl (Format) für ListControl (Format) ListItem-Element für ListItems für Liste (Format) ItemSelectionCondition Steuerelement für den ListItem für ListControl (Format)-ScriptBlock-Element für ItemSelectionCondition für ListControl (Format)

## <a name="syntax"></a>Syntax

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente der `ScriptBlock` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ItemSelectionCondition-Element für den ListItem für ListControl (Format)](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|Definiert die Bedingung, die für dieses Listenelement zu verwendende vorhanden sein muss.|

## <a name="text-value"></a>Textwert

Geben Sie das Skript aus, das ausgewertet wird.

## <a name="remarks"></a>Hinweise

Wenn dieses Element verwendet wird, Sie können nicht angeben, die `PropertyName` -Element, wenn die auswahlbedingung zu definieren.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
