---
title: Konfigurationselement (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066820"
---
# <a name="configuration-element-format"></a>Element „Configuration“ (Format)

Das Element das obersten Ebene eine Formatierungsdatei darstellt.

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

Die folgenden Abschnitte beschreiben die Attribute, untergeordnete Elemente und das übergeordnete Element des der `Configuration` Element. Dieses Element muss das Stammelement für jede Formatierungsdatei, und dieses Element muss mindestens ein untergeordnetes Element enthalten.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Controls-Element für Konfiguration (Format)](./controls-element-for-configuration-format.md)|Optionales Element.<br /><br /> Definiert die allgemeinen Steuerelemente, die von allen Ansichten des die Formatierungsdatei verwendet werden können.|
|[DefaultSettings-Element (Format)](./defaultsettings-element-format.md)|Optionales Element.<br /><br /> Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten.|
|[Format des SelectionSets](./selectionsets-element-format.md)|Optionales Element.<br /><br /> Definiert die allgemeine Sätze von .NET-Objekten, die von allen Ansichten des die Formatierungsdatei verwendet werden können.|
|[ViewDefinitions-Element (Format)](./viewdefinitions-element-format.md)|Optionales Element.<br /><br /> Definiert die Ansichten verwendet, um die Objekte anzuzeigen.|

### <a name="parent-elements"></a>Übergeordnete Elemente

Keine.

## <a name="remarks"></a>Hinweise

Formatierungsdateien definieren, wie die Objekte angezeigt werden. In den meisten Fällen dieses Root-Element enthält eine [ViewDefinitions](./viewdefinitions-element-format.md) Element, das die Tabelle, Liste und Breiten Ansichten der formatierungs-Datei definiert. Zusätzlich zu den Definitionen anzeigen kann die Formatierungsdatei definieren, allgemeine Auswahl legt, Einstellungen und Steuerelemente, die diese Sichten verwenden können.

## <a name="see-also"></a>Weitere Informationen

[Controls-Element für Konfiguration (Format)](./controls-element-for-configuration-format.md)

[DefaultSettings-Element (Format)](./defaultsettings-element-format.md)

[SelectionSets-Element (Format)](./selectionsets-element-format.md)

[ViewDefinitions-Element (Format)](./viewdefinitions-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
