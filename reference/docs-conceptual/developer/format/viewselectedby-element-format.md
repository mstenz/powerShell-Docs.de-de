---
title: Viewselectedby-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367969"
---
# <a name="viewselectedby-element-format"></a>Element „ViewSelectedBy“ (Format)

Definiert die .NET-Objekte, die von der Ansicht angezeigt werden. Jede Ansicht muss mindestens ein .NET-Objekt angeben.

Viewdefinitions-Element (Format) View-Element (Format) viewselectedby-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, die untergeordneten Elemente und das übergeordnete Element des `ViewSelectedBy`-Elements beschrieben. Dieses Element muss mindestens ein untergeordnetes `TypeName`-oder `SelectionSetName`-Element enthalten. Es gibt keine Beschränkung für die Anzahl der untergeordneten Elemente, die angegeben werden können, und ihre Reihenfolge ist nicht signifikant.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Tyname-Element für viewselectedby (Format)](./typename-element-for-viewselectedby-format.md)|Optionales Element.<br /><br /> Gibt ein .NET-Objekt an, das von der Ansicht angezeigt wird.|
|[Selectionsetname-Element für viewselectedby (Format)](./selectionsetname-element-for-viewselectedby-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Objekten an, die von der Sicht angezeigt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, in der ein oder mehrere .NET-Objekte angezeigt werden.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zur Verwendung dieses Elements in verschiedenen Ansichten finden Sie unter [Tabellen Ansichts Komponenten](./creating-a-table-view.md), [Listen Ansichts Komponenten](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md)und [Custom Control Components](./creating-custom-controls.md).

Das `SelectionSetName`-Element wird verwendet, wenn die Formatierungs Datei eine Gruppe von Objekten definiert, die von mehreren Ansichten angezeigt werden. Weitere Informationen zum Definieren und referenziert von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie das [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt für eine Listenansicht angegeben wird. Das gleiche Schema wird für Tabellen-, breiten-und benutzerdefinierte Sichten verwendet.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Erstellen einer breiten Ansicht](./creating-a-wide-view.md)

[Erstellen benutzerdefinierter Steuerelemente](./creating-custom-controls.md)

[Definieren von Auswahl Sätzen](./defining-selection-sets.md)

[Selectionsetname-Element für viewselectedby (Format)](./selectionsetname-element-for-viewselectedby-format.md)

[Tyname-Element (Format)](./typename-element-for-viewselectedby-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
