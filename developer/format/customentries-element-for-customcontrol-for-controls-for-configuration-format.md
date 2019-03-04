---
title: CustomEntries-Element für CustomControl für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856306"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a>Element „CustomEntries“ für CustomControl für Controls für Configuration (Format)

Enthält die Definitionen von einem allgemeinen Steuerelement an. Dieses Element wird verwendet, wenn ein allgemeines Steuerelement zu definieren, das von allen Ansichten im die Formatierungsdatei verwendet werden kann.

Konfigurationselement (Format)-Element-Steuerelemente (Format)-Steuerelement Konfigurationselements für Steuerelemente für (Format) CustomControl Konfigurationselement für Steuerelement (Format) CustomEntries Konfigurationselement für CustomControl für Konfiguration ( -Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `CustomEntries` Element. Sie müssen eine oder mehrere untergeordnete Elemente angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|Stellt eine Definition des allgemeinen-Steuerelements.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomControl-Element für das Steuerelement für die Konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|Das allgemeine Steuerelement definiert.|

## <a name="remarks"></a>Hinweise

In den meisten Fällen ein Steuerelement verfügt über nur eine Definition, die in einem einzelnen definiert ist `CustomEntry` Element. So ist es jedoch möglich, mehrere Definitionen zu besitzen, wenn das Steuerelement zu verwenden, um verschiedene .NET Objekte angezeigt werden sollen. In diesen Fällen können Sie definieren eine `CustomEntry` -Element für jedes Objekt oder eine Gruppe von Objekten.

## <a name="see-also"></a>Weitere Informationen

[CustomControl-Element für das Steuerelement für die Konfiguration (Format)](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[CustomEntry-Element für CustomControl für Steuerelemente für die Konfiguration (Format)](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
