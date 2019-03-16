---
title: DefaultSettings-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059064"
---
# <a name="defaultsettings-element-format"></a>Element „DefaultSettings“ (Format)

Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten. Allgemeine Einstellungen umfassen das Anzeigen von Fehlern, Umbrechen von Text in Tabellen, die definieren, wie Sammlungen erweitert werden, und vieles mehr.

-Element (Format) DefaultSettings Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `DefaultSettings` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[DisplayError-Element (Format)](./displayerror-element-format.md)|Optionales Element.<br /><br /> Gibt an, dass die Zeichenfolge #ERR angezeigt wird, tritt ein Fehler beim Anzeigen eines Datenelements.|
|[EnumerableExpansions-Element (Format)](./enumerableexpansions-element-format.md)|Optionales Element.<br /><br /> Definiert die verschiedenen Möglichkeiten, in der .NET Objekte erweitert werden, wenn sie in einer Ansicht angezeigt werden.|
|[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)|Optionales Element.<br /><br /> Gibt die minimale Anzahl von Eigenschaften, die ein Objekt benötigen, um das Objekt in einer Tabellenansicht anzuzeigen.|
|[ShowError-Element (Format)](./showerror-element-format.md)|Optionales Element.<br /><br /> Gibt an, dass es sich bei der vollständigen Fehlerdatensatz angezeigt wird, tritt ein Fehler beim Anzeigen eines Datenelements.|
|[WrapTables-Element (Format)](./wraptables-element-format.md)|Optionales Element.<br /><br /> Gibt an, dass die Daten in einer Tabelle in der nächsten Zeile verschoben werden, wenn es sich nicht in die Breite der Spalte passt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Konfigurationselement](./configuration-element-format.md)|Das Element das obersten Ebene eine Formatierungsdatei darstellt.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[Konfigurationselement](./configuration-element-format.md)

[DisplayError-Element (Format)](./displayerror-element-format.md)

[EnumerableExpansions-Element (Format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)

[ShowError-Element (Format)](./showerror-element-format.md)

[WrapTables-Element (Format)](./wraptables-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
