---
title: Configuration-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363499"
---
# <a name="configuration-element-format"></a>Element „Configuration“ (Format)

Stellt das Element der obersten Ebene einer Formatierungs Datei dar.

Konfigurationselement

## <a name="syntax"></a>Syntax

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Configuration`-Elements beschrieben. Dieses Element muss das root-Element für jede Formatierungs Datei sein, und dieses Element muss mindestens ein untergeordnetes Element enthalten.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Controls-Element für Konfiguration (Format)](./controls-element-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die allgemeinen Steuerelemente, die von allen Ansichten der Formatierungs Datei verwendet werden können.|
|[DefaultSettings-Element (Format)](./defaultsettings-element-format.md)|Optionales Element.<br /><br /> Definiert allgemeine Einstellungen, die für alle Sichten der Formatierungs Datei gelten.|
|[Selectionsets-Element Format](./selectionsets-element-format.md)|Optionales Element.<br /><br /> Definiert die allgemeinen Sätze von .NET-Objekten, die von allen Sichten der Formatierungs Datei verwendet werden können.|
|[Viewdefinitions-Element (Format)](./viewdefinitions-element-format.md)|Optionales Element.<br /><br /> Definiert die Sichten, die zum Anzeigen von Objekten verwendet werden.|

### <a name="parent-elements"></a>Übergeordnete Elemente

Keine.

## <a name="remarks"></a>Hinweise

Formatieren von Dateien definieren, wie Objekte angezeigt werden. In den meisten Fällen enthält dieses root-Element ein [viewdefinitions](./viewdefinitions-element-format.md) -Element, das die Tabellen-, Listen-und breiten Ansichten der Formatierungs Datei definiert. Zusätzlich zu den Sicht Definitionen kann die Formatierungs Datei allgemeine Auswahl Sätze, Einstellungen und Steuerelemente definieren, die diese Sichten verwenden können.

## <a name="see-also"></a>Weitere Informationen

[Controls-Element für Konfiguration (Format)](./controls-element-for-configuration-format.md)

[DefaultSettings-Element (Format)](./defaultsettings-element-format.md)

[Selectionsets-Element (Format)](./selectionsets-element-format.md)

[Viewdefinitions-Element (Format)](./viewdefinitions-element-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
