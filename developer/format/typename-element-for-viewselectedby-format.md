---
title: TypeName-Element für ViewSelectedBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083755"
---
# <a name="typename-element-for-viewselectedby-format"></a>Element „TypeName“ für ViewSelectedBy (Format)

Gibt ein .NET-Objekt, das von der Ansicht angezeigt wird.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ViewSelectedBy-Element (Format) TypeName Konfigurationselement für ViewSelectedBy (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente der `TypeName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ViewSelectedBy-Element (Format)](./viewselectedby-element-format.md)|Definiert die .NET Objekte, die von der Ansicht angezeigt werden.|

## <a name="text-value"></a>Textwert

Geben Sie den vollqualifizierten Namen des .NET-Typs, z. B. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Hinweise

Weitere Informationen zur Verwendung dieses Elements in verschiedenen Ansichten finden Sie unter [erstellen eine Tabellensicht](./creating-a-table-view.md), [Erstellen einer Listenansicht](./creating-a-list-view.md), [erstellen eine Breite Ansicht](./creating-a-wide-view.md), und [ Benutzerdefinierte Ansichtskomponenten](./creating-custom-controls.md).

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

[ViewSelectedBy-Element (Format)](./viewselectedby-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
