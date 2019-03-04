---
title: SelectionSetName-Element für ViewSelectedBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858336"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a>Element „SelectionSetName“ für ViewSelectedBy (Format)

Gibt einen Satz von .NET-Objekten, die von der Ansicht angezeigt werden.

-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element ViewSelectedBy-Element (Format) SelectionSetName Konfigurationselement für ViewSelectedBy (Format)

## <a name="syntax"></a>Syntax

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `SelectionSetName` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ViewSelectedBy-Element (Format)](./viewselectedby-element-format.md)|Definiert die .NET Objekte, die von der Ansicht angezeigt werden.|

## <a name="text-value"></a>Textwert

Geben Sie den Namen des Satzes Auswahl, die von definiert ist die `Name` -Element für den Auswahlsatz.

## <a name="remarks"></a>Hinweise

Sie können die Auswahl legt verwenden, bei einen Satz von verknüpften Objekten, die Sie verweisen, indem Sie ein einzelner Name sein, z. B. einen Satz von Objekten, die durch Vererbung verbunden werden möchten. Weitere Informationen zum Definieren und verweisen auf die von Auswahlgruppen finden Sie unter [legt der Objekte definieren](./defining-selection-sets.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie eine Auswahl, legen Sie für eine Listenansicht angeben. Das gleiche Schema wird für die Tabelle, Breite und benutzerdefinierte Ansichten verwendet.

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

[Auswahl definieren](./defining-selection-sets.md)

[ViewSelectedBy-Element (Format)](./viewselectedby-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
