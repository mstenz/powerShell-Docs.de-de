---
title: SelectionSets-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853566"
---
# <a name="selectionsets-element-format"></a>Element „SelectionSets“ (Format)

Definiert die allgemeine Sätze von .NET-Objekten, die von allen Ansichten des die Formatierungsdatei verwendet werden können. Die Ansichten und die Steuerelemente die Formatierungsdatei können den vollständigen Satz von Objekten mit nur den Namen des Satzes Auswahl verweisen.

Configuration Element SelectionSets-Elementformat

## <a name="syntax"></a>Syntax

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `SelectionSets` Element. Jedes untergeordnete Element definiert einen Satz von Objekten, die durch den Namen des Satzes verwiesen werden kann. Die Reihenfolge der untergeordneten Elemente ist nicht wichtig.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SelectionSet-Element (Format)](./selectionset-element-format.md)|Erforderliches Element.<br /><br /> Definiert einen Satz von .NET-Objekten, die durch den Namen des Satzes verwiesen werden kann.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Konfigurationselement](./configuration-element-format.md)|Das Element das obersten Ebene eine Formatierungsdatei darstellt.|

## <a name="remarks"></a>Hinweise

Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten. Wenn Sie Ihre Ansichten definieren, können Sie den Satz von Objekten angeben, mit dem Namen der Markierung anstelle Auflisten aller Objekte in jeder Ansicht festgelegt.

Typische Auswahl Sets werden anhand ihres Namens angegeben, bei der Definition der Ansichten die Formatierungsdatei oder die Definitionen der Ansichten. In diesen Fällen die `SelectionSetName` untergeordnetes Element von der `ViewSelectedBy` und `EntrySelectedBy` Elemente gibt den Satz verwendet werden. Weitere Informationen zu Auswahl, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).

## <a name="see-also"></a>Weitere Informationen

[Konfigurationselement](./configuration-element-format.md)

[Auswahl definieren](./defining-selection-sets.md)

[SelectionSet-Element (Format)](./selectionset-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
