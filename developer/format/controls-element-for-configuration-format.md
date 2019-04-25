---
title: Controls-Element für Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066871"
---
# <a name="controls-element-for-configuration-format"></a>Element „Controls“ für Configuration (Format)

Definiert die allgemeinen Steuerelemente, die von allen Ansichten des die Formatierungsdatei verwendet werden können.

Konfiguration-Element (Format)-Controls-Element (Format)-Konfiguration

## <a name="syntax"></a>Syntax

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Controls` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Control-Element für Controls für Konfiguration (Format)](./control-element-for-controls-for-configuration-format.md)|Erforderliches Element.<br /><br /> Definiert ein allgemeines Steuerelement, das von allen Ansichten des die Formatierungsdatei verwendet werden kann.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Konfigurationselement (Format)](./configuration-element-format.md)|Das Element das obersten Ebene eine Formatierungsdatei darstellt.|

## <a name="remarks"></a>Hinweise

Sie können eine beliebige Anzahl von allgemeinen Steuerelementen erstellen. Für jedes Steuerelement müssen Sie den Namen angeben, der zum Verweisen auf das Steuerelement und die Komponenten des Steuerelements verwendet wird.

## <a name="see-also"></a>Weitere Informationen

[Konfigurationselement (Format)](./configuration-element-format.md)

[Control-Element für Controls für Konfiguration (Format)](./control-element-for-controls-for-configuration-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
