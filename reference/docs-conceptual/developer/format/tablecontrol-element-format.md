---
title: Tablecontrol-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368199"
---
# <a name="tablecontrol-element-format"></a>Element „TableControl“ (Format)

Definiert ein Tabellenformat für eine Sicht.

Viewdefinitions-Element (Format) View-Element (Format) tablecontrol-Element (Format)

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

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `TableControl`-Elements beschrieben. Sie müssen die Zeilen der Tabelle angeben. Alle anderen untergeordneten Elemente sind optional.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[AutoSize-Element für tablecontrol (Format)](./autosize-element-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Gibt an, ob die Spaltengröße und die Anzahl der Spalten basierend auf der Größe der Daten angepasst werden.|
|[Hidetableheaders-Element für tablecontrol (Format)](./hidetableheaders-element-format.md)|Optionales Element.<br /><br /> Gibt an, ob der Header der Tabelle nicht angezeigt wird.|
|[TableHeaders-Element für tablecontrol (Format)](./tableheaders-element-format.md)|Erforderliches Element.<br /><br /> Definiert die Bezeichnungen, die Breite und die Ausrichtung der Daten für die Spalten der Tabellenansicht.|
|[Tablerowentries-Element für tablecontrol (Format)](./tablerowentries-element-for-tablecontrol-format.md)|Optionales Element.<br /><br /> Stellt die Definitionen der Tabellenansicht bereit.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die zum Anzeigen der Member von einem oder mehreren-Objekten verwendet wird.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten einer Tabellenansicht finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt ein `TableControl`-Element, das verwendet wird, um die Eigenschaften des [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekts anzuzeigen.

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

[AutoSize-Element für tablecontrol (Format)](./autosize-element-for-tablecontrol-format.md)

[Hidetableheaders-Element (Format)](./hidetableheaders-element-format.md)

[TableHeaders-Element (Format)](./tableheaders-element-format.md)

[Tablerowentries-Element (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
