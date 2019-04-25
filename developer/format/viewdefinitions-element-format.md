---
title: ViewDefinitions-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083704"
---
# <a name="viewdefinitions-element-format"></a>Element „ViewDefinitions“ (Format)

Definiert die Ansichten, die zum Anzeigen von .NET Objekten verwendet. Diese Sichten können die Eigenschaften und das Skriptwerte eines Objekts in ein Tabellenformat, Listenformat, Breiten Format und Format des benutzerdefinierten Steuerelements anzeigen.

ViewDefinitions (XML-Format) von Konfigurationselement-Element (Format)

## <a name="syntax"></a>Syntax

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ViewDefinitions` Element. Es gibt keine Beschränkung der Anzahl der Sichten, die in einer Formatierungsdatei definiert werden können, und sie können in beliebiger Reihenfolge hinzugefügt werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die verwendet wird, um eine oder mehrere .NET Objekte anzuzeigen.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Konfigurationselement (Format)](./configuration-element-format.md)|Das Element das obersten Ebene eine Formatierungsdatei darstellt.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten der verschiedenen Typen von Sichten finden Sie unter den folgenden Themen:

- [Erstellen einer Tabellenansicht](./creating-a-table-view.md)

- [Erstellen einer Listenansicht](./creating-a-list-view.md)

- [Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

- [Benutzerdefinierte Steuerelemente](./creating-custom-controls.md)

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `ViewDefinitions` Element, das die übergeordneten Elemente für eine Tabelle und einer Listenansicht enthält.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a>Weitere Informationen

[Konfigurationselement (Format)](./configuration-element-format.md)

[View-Element (Format)](./view-element-format.md)

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Benutzerdefinierte Steuerelemente](./creating-custom-controls.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
