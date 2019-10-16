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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363869"
---
# <a name="defaultsettings-element-format"></a>Element „DefaultSettings“ (Format)

Definiert allgemeine Einstellungen, die für alle Sichten der Formatierungs Datei gelten. Zu den allgemeinen Einstellungen gehören das Anzeigen von Fehlern, das umschließen von Text in Tabellen, das Definieren der Erweiterung von Sammlungen und vieles mehr.

Configuration-Element (Format) DefaultSettings-Element (Format)

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

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `DefaultSettings`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Display Error-Element (Format)](./displayerror-element-format.md)|Optionales Element.<br /><br /> Gibt an, dass die Zeichenfolge #Err angezeigt wird, wenn ein Fehler auftritt, während ein Datenelement angezeigt wird.|
|[Enumerableexpansions-Element (Format)](./enumerableexpansions-element-format.md)|Optionales Element.<br /><br /> Definiert die verschiedenen Möglichkeiten, wie .NET-Objekte erweitert werden, wenn Sie in einer Ansicht angezeigt werden.|
|[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)|Optionales Element.<br /><br /> Gibt die Mindestanzahl von Eigenschaften an, die ein Objekt besitzen muss, um das Objekt in einer Tabellenansicht anzuzeigen.|
|[ShowError-Element (Format)](./showerror-element-format.md)|Optionales Element.<br /><br /> Gibt an, dass der vollständige Fehler Daten Satz angezeigt wird, wenn ein Fehler auftritt, während ein Datenelement angezeigt wird.|
|[Wraptables-Element (Format)](./wraptables-element-format.md)|Optionales Element.<br /><br /> Gibt an, dass Daten in einer Tabelle in die nächste Zeile verschoben werden, wenn Sie nicht in die Spaltenbreite passt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Configuration-Element](./configuration-element-format.md)|Stellt das Element der obersten Ebene einer Formatierungs Datei dar.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[Configuration-Element](./configuration-element-format.md)

[Display Error-Element (Format)](./displayerror-element-format.md)

[Enumerableexpansions-Element (Format)](./enumerableexpansions-element-format.md)

[PropertyCountForTable (Format)](./propertycountfortable-element-format.md)

[ShowError-Element (Format)](./showerror-element-format.md)

[Wraptables-Element (Format)](./wraptables-element-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
