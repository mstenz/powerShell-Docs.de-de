---
title: FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f489720-11f6-4019-940e-07f423d4278d
caps.latest.revision: 6
ms.openlocfilehash: c5b2d971fe1590116f96b024ae8769334768acf2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363119"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>Element „FirstLineIndent“ für Frame für Controls für Configuration (Format)

Gibt an, wie viele Zeichen die erste Zeile der Daten nach rechts verschoben wird. Dieses Element wird verwendet, wenn ein gemeinsames Steuerelement definiert wird, das von allen Sichten in der Formatierungs Datei verwendet werden kann.

Konfigurationselement (Format) steuert Element des Konfigurations Elements (Format) Steuerelement für Steuerelemente für Konfiguration (Format) CustomControl-Element für Steuerelement für Configuration (Format) customentries-Element für CustomControl for Configuration ( Format) customentry-Element für CustomControl für Steuerelemente für Configuration (Format) customItem-Element für customentry für Steuerelemente für das Configuration Frame-Element für customItem für Steuerelemente für Configuration (Format) FirstLineIndent-Element für Frame für Steuerelemente für die Konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `FirstLineIndent`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Frame-Element für customItem für Steuerelemente für die Konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|Definiert, wie die Daten angezeigt werden, z. b. das Verschieben der Daten nach links oder rechts.|

## <a name="text-value"></a>Textwert

Geben Sie die Anzahl der Zeichen an, die Sie in die erste Zeile der Daten verschieben möchten.

## <a name="remarks"></a>Hinweise

Wenn dieses Element angegeben ist, können Sie das [firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) -Element nicht angeben.

## <a name="see-also"></a>Weitere Informationen

[Firstlinehanging-Element für Frame für Steuerelemente für die Konfiguration (Format)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Frame-Element für customItem für Steuerelemente für die Konfiguration (Format)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
