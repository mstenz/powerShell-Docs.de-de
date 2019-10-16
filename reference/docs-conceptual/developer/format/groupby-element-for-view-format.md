---
title: GroupBy-Element für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363629"
---
# <a name="groupby-element-for-view-format"></a>Element „GroupBy“ für View (Format)

Definiert, wie eine neue Gruppe von Objekten angezeigt wird. Dieses Element wird verwendet, wenn eine Tabelle, eine Liste, eine Breite oder eine benutzerdefinierte Steuerelement Ansicht definiert wird.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) GroupBy-Element für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element für GroupBy (Format)](./customcontrol-element-for-groupby-format.md)|Optionales Element.<br /><br /> Definiert das benutzerdefinierte Steuerelement, das neue Gruppen anzeigt.|
|[Customcontrolname-Element für GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt den Namen eines Steuer Elements an, das zum Anzeigen der neuen Gruppe verwendet wird.|
|[Label-Element für GroupBy (Format)](./label-element-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt eine Bezeichnung an, die beim Auftreten einer neuen Gruppe angezeigt wird.|
|[PropertyName-Element für GroupBy (Format)](./propertyname-element-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt an, dass die .net-Eigenschaft eine neue Gruppe startet, wenn sich der Wert ändert.|
|[ScriptBlock-Element für GroupBy (Format)](./scriptblock-element-for-groupby-format.md)|Optionales Element.<br /><br /> Gibt das Skript an, das eine neue Gruppe startet, wenn sich der Wert ändert.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[View-Element (Format)](./view-element-format.md)|Definiert eine Ansicht, in der ein oder mehrere .NET-Objekte angezeigt werden.|

## <a name="remarks"></a>Hinweise

Wenn Sie definieren, wie eine neue Gruppe von Objekten angezeigt wird, müssen Sie die Eigenschaft oder das Skript angeben, mit der die neue Gruppe gestartet wird. Es ist jedoch nicht möglich, beides anzugeben.

## <a name="see-also"></a>Weitere Informationen

[Customcontrolname-Element für GroupBy (Format)](./customcontrolname-element-for-groupby-format.md)

[Label-Element für GroupBy (Format)](./label-element-for-groupby-format.md)

[PropertyName-Element für GroupBy (Format)](./propertyname-element-for-groupby-format.md)

[ScriptBlock-Element für GroupBy (Format)](./scriptblock-element-for-groupby-format.md)

[View-Element (Format)](./view-element-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
