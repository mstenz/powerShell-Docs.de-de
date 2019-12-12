---
title: Wideitem-Element für widecontrol (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361399"
---
# <a name="wideitem-element-for-widecontrol-format"></a>Element „WideItem“ für WideControl (Format)

Definiert die Eigenschaft oder das Skript, dessen Wert angezeigt wird.

Configuration-Element (Format) viewdefinitions-Element (Format) Ansichts Element (Format) widecontrol-Element (Format) wideentries-Element (Format) wideentry-Element (Format) wideitem-Element (Format)

## <a name="syntax"></a>Syntax

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `WideItem`-Elements beschrieben. Das `FormatString`-Element ist optional. Sie müssen jedoch eine `PropertyName` oder `ScriptBlock`-Element angeben, aber Sie können nicht beides angeben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[FormatString-Element für wideitem für widecontrol (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)|Optionales Element.<br /><br /> Gibt ein Format Muster an, das definiert, wie der Eigenschafts-oder Skript Wert in der Ansicht angezeigt wird.|
|[PropertyName-Element für wideitem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)|Gibt die-Eigenschaft des-Objekts an, dessen Wert in der breiten Ansicht angezeigt wird.|
|[ScriptBlock-Element für wideitem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|Gibt das Skript an, dessen Wert in der breiten Ansicht angezeigt wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Wideentry-Element (Format)](./wideentry-element-for-widecontrol-format.md)|Stellt eine Definition der breiten Ansicht bereit.|

## <a name="remarks"></a>Hinweise

Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Wide View](./creating-a-wide-view.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt ein `WideEntry`-Element, das ein einzelnes `WideItem` Element definiert. Das `WideItem`-Element definiert die Eigenschaft oder das Skript, dessen Wert in der Ansicht angezeigt wird.

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

Ein umfassendes Beispiel für eine breite Ansicht finden Sie unter [Wide View (Basic)](./wide-view-basic.md).

## <a name="see-also"></a>Weitere Informationen

[FormatString-Element für wideitem für widecontrol (Format)](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[PropertyName-Element für wideitem (Format)](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[ScriptBlock-Element für wideitem (Format)](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[Wideentry-Element (Format)](./wideentry-element-for-widecontrol-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
