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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362779"
---
# <a name="listcontrol-element-format"></a>Element „ListControl“ (Format)

Definiert ein Listenformat für die Sicht.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) ListControl-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `ListControl`-Elements beschrieben. Dieses Element darf nur ein einzelnes untergeordnetes Element enthalten.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[ListEntries-Element (Format)](./listentries-element-for-listcontrol-format.md)|Erforderliches Element.<br /><br /> Stellt die Definitionen der Listenansicht bereit.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die zum Anzeigen der Member von einem oder mehreren-Objekten verwendet wird.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zum Erstellen einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt eine Listenansicht für das [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt.

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

[Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei](./writing-a-powershell-formatting-file.md)
