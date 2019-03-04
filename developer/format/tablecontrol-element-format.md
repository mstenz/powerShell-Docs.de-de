---
title: TableControl-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858916"
---
# <a name="tablecontrol-element-format"></a>Element „TableControl“ (Format)

Definiert ein Table-Format für eine Sicht.

ViewDefinitions-Element (Format) anzeigen (Format) TableControl-Elementen (-Format)

## <a name="syntax"></a>Syntax

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `TableControl` Element. Sie müssen die Zeilen der Tabelle angeben. Alle anderen untergeordneten Elemente sind optional.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[AutoSize-Element für TableControl (Format)](./autosize-element-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt an, ob die Größe der Spalte und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.|
|[HideTableHeaders-Element für TableControl (Format)](./hidetableheaders-element-format.md)|Optionales Element.<br /><br /> Gibt an, ob die Kopfzeile der Tabelle nicht angezeigt wird.|
|[TableHeaders-Element für TableControl (Format)](./tableheaders-element-format.md)|Erforderliches Element.<br /><br /> Definiert die Bezeichnungen, die Breite und die Ausrichtung der Daten für die Spalten der Tabelle an.|
|[TableRowEntries-Element für TableCotrol (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Enthält die Definitionen der Tabellenansicht.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die verwendet wird, um die Mitglieder von ein oder mehrere Objekte anzuzeigen.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten der eine Tabellenansicht, finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine `TableControl` -Element, das verwendet wird, zum Anzeigen der Eigenschaften der [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[View-Element (Format)](./view-element-format.md)

[AutoSize-Element für TableControl (Format)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders-Element (Format)](./hidetableheaders-element-format.md)

[TableHeaders-Element (Format)](./tableheaders-element-format.md)

[TableRowEntries-Element (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
