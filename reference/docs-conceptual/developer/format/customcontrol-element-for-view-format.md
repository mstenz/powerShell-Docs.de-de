---
title: CustomControl-Element für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363359"
---
# <a name="customcontrol-element-for-view-format"></a>Element „CustomControl“ für View (Format)

Definiert ein benutzerdefiniertes Steuerelement Format für die Ansicht.

Configuration-Element (Format) viewdefinitions-Element (Format) View-Element (Format) CustomControl-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des `CustomControl`-Elements beschrieben. Sie müssen ein untergeordnetes Element angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md)|Erforderliches Element.<br /><br /> Stellt die Definitionen der benutzerdefinierten Steuerelement Ansicht bereit.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, die verwendet wird, um ein oder mehrere .NET-Objekte anzuzeigen.|

## <a name="remarks"></a>Hinweise

In den meisten Fällen ist nur eine Definition für jede Steuerelement Ansicht erforderlich, aber es ist möglich, mehrere Definitionen bereitzustellen, wenn Sie die gleiche Ansicht verwenden möchten, um unterschiedliche .NET-Objekte anzuzeigen. In diesen Fällen können Sie eine separate Definition für jedes Objekt oder jede Gruppe von Objekten bereitstellen.

## <a name="see-also"></a>Weitere Informationen

[Customentries-Element für CustomControl für Ansicht (Format)](./customentries-element-for-customcontrol-for-view-format.md)

[View-Element (Format)](./view-element-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
