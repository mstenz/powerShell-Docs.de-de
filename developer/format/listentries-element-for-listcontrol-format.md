---
title: ListEntries-Element für ListControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856786"
---
# <a name="listentries-element-for-listcontrol-format"></a>Element „ListEntries“ für ListControl (Format)

Enthält die Definitionen der Listenansicht angezeigt. Eine oder mehrere Definitionen muss die Listenansicht angegeben werden.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl-Element (Format) ListEntries Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `ListEntries` Element. Mindestens ein untergeordnetes Element muss angegeben werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListEntry-Element (Format)](./listentry-element-for-listcontrol-format.md)|Stellt eine Definition der Listenansicht angezeigt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListControl-Element (Format)](./listcontrol-element-format.md)|Definiert eine Listenformat für die Ansicht.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu Ansichten aufzulisten, finden Sie unter [Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt die XML-Elemente, die definieren, die Listenansicht die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Weitere Informationen

[ListControl-Element (Format)](./listcontrol-element-format.md)

[ListEntry-Element (Format)](./listentry-element-for-listcontrol-format.md)

[Listenansicht](./creating-a-list-view.md)

[Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei](./writing-a-powershell-formatting-file.md)
