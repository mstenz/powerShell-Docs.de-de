---
title: ViewSelectedBy-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083823"
---
# <a name="viewselectedby-element-format"></a>Element „ViewSelectedBy“ (Format)

Definiert die .NET Objekte, die von der Ansicht angezeigt werden. Jede Sicht muss mindestens ein .NET Objekt angeben.

ViewDefinitions-Element (Format) anzeigen (Format) ViewSelectedBy Elementen (-Format)

## <a name="syntax"></a>Syntax

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden die Attribute, untergeordnete Elemente und übergeordnete Element des Elements der `ViewSelectedBy` Element. Dieses Element muss mindestens einen enthalten `TypeName` oder `SelectionSetName` untergeordnetes Element. Es gibt keine Beschränkung der Anzahl der untergeordneten Elemente, die angegeben werden können, noch ist die Reihenfolge von Bedeutung.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TypeName-Element für ViewSelectedBy (Format)](./typename-element-for-viewselectedby-format.md)|Optionales Element.<br /><br /> Gibt ein .NET-Objekt, das von der Ansicht angezeigt wird.|
|[SelectionSetName-Element für ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)|Optionales Element.<br /><br /> Gibt einen Satz von .NET-Objekten, die von der Ansicht angezeigt werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, in dem ein oder mehrere .NET Objekte angezeigt.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zur Verwendung dieses Elements in verschiedenen Ansichten finden Sie unter [Tabelle Ansichtskomponenten](./creating-a-table-view.md), [Liste Ansichtskomponenten](./creating-a-list-view.md), [Wide Ansichtskomponenten](./creating-a-wide-view.md), und [Benutzerdefinierte Steuerelementkomponenten](./creating-custom-controls.md).

Die `SelectionSetName` Element wird verwendet, wenn die Formatierungsdatei einen Satz von Objekten definiert, die von mehreren Ansichten angezeigt werden. Weitere Informationen wie Auswahl legt definiert, und auf die verwiesen wird, finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt für eine Listenansicht. Das gleiche Schema wird für die Tabelle, Breite und benutzerdefinierte Ansichten verwendet.

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

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md)

[Auswahl definieren](./defining-selection-sets.md)

[SelectionSetName-Element für ViewSelectedBy (Format)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName-Element (Format)](./typename-element-for-viewselectedby-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
