---
title: Selectionsetname-Element für viewselectedby (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368259"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Element „SelectionSetName“ für ViewSelectedBy (Format)

Gibt einen Satz von .NET-Objekten an, die von der Sicht angezeigt werden.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) viewselectedby-Element (Format) selectionsetname-Element für viewselectedby (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `SelectionSetName`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Viewselectedby-Element (Format)](./viewselectedby-element-format.md)|Definiert die .NET-Objekte, die von der Ansicht angezeigt werden.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Auswahl Satzes an, der vom `Name`-Element für den Auswahl Satz definiert wird.

## <a name="remarks"></a>Hinweise

Sie können Auswahl Sätze verwenden, wenn Sie über einen Satz verwandter Objekte verfügen, auf die Sie verweisen möchten, indem Sie einen einzelnen Namen verwenden, z. b. eine Gruppe von Objekten, die durch Vererbung verknüpft sind. Weitere Informationen zum Definieren und referenzieren von Auswahl Sätzen finden Sie unter [Definieren von Objekt Sätzen](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie Sie einen Auswahl Satz für eine Listenansicht angeben. Das gleiche Schema wird für Tabellen-, breiten-und benutzerdefinierte Sichten verwendet.

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>Weitere Informationen

[Definieren von Auswahl Sätzen](./defining-selection-sets.md)

[Viewselectedby-Element (Format)](./viewselectedby-element-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
