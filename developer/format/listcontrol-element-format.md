---
title: ListControl-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857456"
---
# <a name="listcontrol-element-format"></a>Element „ListControl“ (Format)

Definiert eine Listenformat für die Ansicht.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ListControl Konfigurationselement (Format)

## <a name="syntax"></a>Syntax

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `ListControl` Element. Dieses Element muss nur ein einzelnes untergeordnetes Element enthalten.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ListEntries-Element (Format)](./listentries-element-for-listcontrol-format.md)|Erforderliches Element.<br /><br /> Enthält die Definitionen der Listenansicht angezeigt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die verwendet wird, um die Mitglieder von ein oder mehrere Objekte anzuzeigen.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zum Erstellen einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine Ansicht für die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt.

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>Weitere Informationen

[View-Element (Format)](./view-element-format.md)

[ListEntries-Element (Format)](./listentries-element-for-listcontrol-format.md)

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei](./writing-a-powershell-formatting-file.md)
