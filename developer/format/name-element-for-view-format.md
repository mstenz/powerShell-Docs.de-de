---
title: Nennen Sie Element anzeigen (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065069"
---
# <a name="name-element-for-view-format"></a>Element „Name“ für View (Format)

Gibt den Namen, der verwendet wird, um die Ansicht zu identifizieren.

Konfiguration-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element Name-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `Name` Element. Nur ein `Name` Element ist für jede Ansicht zulässig.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die verwendet wird, um die Mitglieder von .NET-Objekten für eine oder mehrere anzuzeigen.|

## <a name="text-value"></a>Textwert

Geben Sie einen eindeutigen Anzeigenamen für die Ansicht ein. Dieser Name kann einen Verweis auf den Typ der Ansicht (z. B. eine Tabelle oder Ansicht), welches Objekt oder ein Satz von Objekten verwenden Sie die Ansicht, welcher Befehl gibt zurück, die Objekte oder eine Kombination aus diesen enthalten.

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den verschiedenen Typen von Ansichten finden Sie unter den folgenden Themen: [Tabellenansicht](./creating-a-table-view.md), [Listenansicht](./creating-a-list-view.md), [Breite Ansicht](./creating-a-wide-view.md), und [benutzerdefinierte Ansicht](./creating-custom-controls.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine `View` Element, das eine Tabellenansicht für definiert die [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) Objekt. Der Name der Ansicht lautet "Service".

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a>Weitere Informationen

[Erstellen einer Listenansicht](./creating-a-list-view.md)

[Erstellen einer Tabellenansicht](./creating-a-table-view.md)

[Erstellen eine Breite Ansicht](./creating-a-wide-view.md)

[Erstellen von benutzerdefinierten Steuerelementen](./creating-custom-controls.md)

[View-Element (Format)](./view-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
