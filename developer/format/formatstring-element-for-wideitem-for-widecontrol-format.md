---
title: FormatString-Element für WideItem für WideControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065681"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a>Element „FormatString“ für WideItem für WideControl (Format)

Gibt ein Formatmuster, das definiert, wie der Wert der Eigenschaft oder ein Skript in der Ansicht angezeigt wird.

Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element WideControl-Element (Format) WideEntries-Element (Format) WideEntry Konfigurationselement für WideControl (Format) WideItem-Element für WideControl (Format) FormatString-Element für WideItem für WideControl (Format)

## <a name="syntax"></a>Syntax

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `FormatString` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[WideItem-Element für WideControl (Format)](./wideitem-element-for-widecontrol-format.md)|Definiert die Eigenschaft oder ein Skript, dessen Wert in einer Zeile in der Listenansicht angezeigt wird.|

## <a name="text-value"></a>Textwert

Geben Sie das Muster, das zum Formatieren der Daten verwendet wird. Sie können z. B. dieses Muster verwenden, zum Formatieren des Werts einer Eigenschaft, die vom Typ [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0: TT} {0:HH}: {0:mm}.

## <a name="remarks"></a>Hinweise

Formatzeichenfolgen können verwendet werden, wenn Sie Tabellenansichten, Listenansichten, Breiten Ansichten oder benutzerdefinierte Ansichten erstellen. Weitere Informationen zum Formatieren eines Wert in einer Ansicht angezeigt, finden Sie unter [Formatieren von angezeigten Daten](./formatting-displayed-data.md).

Weitere Informationen zur Verwendung von Formatzeichenfolgen in breiten Ansichten finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie definieren eine Formatierungszeichenfolge für den Wert des der `StartTime` Eigenschaft.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[WideItem-Element für WideControl (Format)](./wideitem-element-for-widecontrol-format.md)

[Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei](./writing-a-powershell-formatting-file.md)
