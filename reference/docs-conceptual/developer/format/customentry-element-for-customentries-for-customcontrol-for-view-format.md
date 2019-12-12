---
title: Customentry-Element für customentries für CustomControl für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364019"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>Element „CustomEntry“ für CustomEntries für CustomControl für View (Format)

Stellt eine Definition der benutzerdefinierten Steuerelement Ansicht bereit.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format) customentries-Element für CustomControl für View (Format) customentry-Element für customentries for View (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomEntry`-Elements beschrieben. Sie müssen die Elemente angeben, die in der Definition angezeigt werden.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Entryselectedby-Element für customentry für View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|Optionales Element.<br /><br /> Definiert die .NET-Typen, die die Definition der benutzerdefinierten Steuerelement Ansicht oder die Bedingung verwenden, die für die Verwendung dieser Definition vorhanden sein muss.|
|[CustomItem-Element für customentry für View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|Definiert ein Steuerelement für die benutzerdefinierte Steuerelement Definition.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Stellt die Definitionen der benutzerdefinierten Steuerelement Ansicht bereit. Die benutzerdefinierte Steuerelement Ansicht muss mindestens eine Definition angeben.|

## <a name="remarks"></a>Hinweise

In den meisten Fällen ist nur eine Definition für jede benutzerdefinierte Steuerelement Ansicht erforderlich, aber es ist möglich, mehrere Definitionen zu verwenden, wenn Sie dieselbe Ansicht verwenden möchten, um unterschiedliche .NET-Objekte anzuzeigen. In diesen Fällen können Sie eine separate Definition für jedes Objekt oder jede Gruppe von Objekten bereitstellen.

## <a name="see-also"></a>Weitere Informationen

[CustomControl-Element für Ansicht (Format)](./customcontrol-element-for-view-format.md)

[CustomItem-Element für customentry für View (Format)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[Entryselectedby-Element für customentry für View (Format)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
