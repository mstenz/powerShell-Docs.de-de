---
title: Customentries-Element für CustomControl für Steuerelemente für Ansicht (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368809"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>Element „CustomEntries“ für CustomControl für Controls für View (Format)

Stellt die Definitionen für das-Steuerelement bereit. Dieses Element wird beim Definieren von Steuerelementen verwendet, die von einer Ansicht verwendet werden können.

Konfigurationselement (Format) viewdefinitions-Element (Format) Ansichts Element (Format) steuert Element (Format) Steuerelement (Format) Steuerelement für Steuerelemente für Ansicht (Format) CustomControl-Element für Steuerelement für Steuerelemente für Ansicht (Format) customentries-Element für CustomControl für Steuerelemente für Ansicht (Format)

## <a name="syntax"></a>Syntax

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente des `CustomEntries`-Elements beschrieben. Es gibt keine maximale Beschränkung für die Anzahl der untergeordneten Elemente, die angegeben werden können.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Customentry-Element für customentries für Steuerelemente für Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)|Erforderliches Element.<br /><br /> Stellt eine Definition des-Steuer Elements bereit.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[CustomControl-Element für Steuerelemente für Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)|Definiert das Steuerelement, das von der Ansicht verwendet wird.|

## <a name="remarks"></a>Hinweise

In den meisten Fällen verfügt ein Steuerelement nur über eine Definition, die in einem einzelnen `CustomEntry`-Element angegeben wird. Es ist jedoch möglich, mehrere Definitionen bereitzustellen, wenn Sie das gleiche Steuerelement zum Anzeigen verschiedener .NET-Objekte verwenden möchten. In diesen Fällen können Sie ein `CustomEntry`-Element für jedes Objekt oder jede Gruppe von Objekten definieren.

## <a name="see-also"></a>Weitere Informationen

[Customentry-Element für customentries für Steuerelemente für Ansicht (Format)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[CustomControl-Element für Steuerelemente für Ansicht (Format)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
