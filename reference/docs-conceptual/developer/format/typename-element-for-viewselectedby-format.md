---
title: Tyname-Element für viewselectedby (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361439"
---
# <a name="typename-element-for-viewselectedby-format"></a>Element „TypeName“ für ViewSelectedBy (Format)

Gibt ein .NET-Objekt an, das von der Ansicht angezeigt wird.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) viewselectedby-Element (Format) Typname-Element für viewselectedby (Format)

## <a name="syntax"></a>Syntax

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente des `TypeName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Viewselectedby-Element (Format)](./viewselectedby-element-format.md)|Definiert die .NET-Objekte, die von der Ansicht angezeigt werden.|

## <a name="text-value"></a>Textwert

Geben Sie den voll qualifizierten Namen des .net-Typs an, z. b. `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Hinweise

Weitere Informationen zur Verwendung dieses Elements in verschiedenen Ansichten finden Sie unter [Erstellen einer Tabellen Sicht](./creating-a-table-view.md), [Erstellen einer Listenansicht](./creating-a-list-view.md), [Erstellen einer breiten Ansicht](./creating-a-wide-view.md)und [benutzerdefinierte Ansichts Komponenten](./creating-custom-controls.md).

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

[Viewselectedby-Element (Format)](./viewselectedby-element-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
