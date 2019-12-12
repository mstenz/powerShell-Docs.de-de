---
title: Customentry-Element für CustomControl für GroupBy (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364059"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>Element „CustomEntry“ für CustomControl für GroupBy (Format)

Stellt eine Definition des-Steuer Elements bereit. Dieses Element wird verwendet, wenn definiert wird, wie eine neue Gruppe von Objekten angezeigt wird.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für View (Format) CustomControl-Element für GroupBy (Format) customentries-Element für CustomControl für GroupBy (Format) customentry-Element für CustomControl für GroupBy (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und die übergeordneten Elemente des `CustomEntry`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Entryselectedby-Element für customentry für GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert die .NET-Typen, die diese Steuerelement Definition verwenden, oder die Bedingung, die vorhanden sein muss, damit diese Definition verwendet werden muss.|
|[CustomItem-Element für customentry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)|Erforderliches Element.<br /><br /> Definiert, wie das-Steuerelement die Daten anzeigt.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentries-Element für CustomControl für GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)|Stellt die Definitionen für das-Steuerelement bereit.|

## <a name="remarks"></a>Hinweise

## <a name="see-also"></a>Weitere Informationen

[Entryselectedby-Element für customentry für GroupBy (Format)](./entryselectedby-element-for-customentry-for-groupby-format.md)

[CustomItem-Element für customentry für GroupBy (Format)](./customitem-element-for-customentry-for-groupby-format.md)

[Customentries-Element für CustomControl für GroupBy (Format)](./customentries-element-for-customcontrol-for-groupby-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
