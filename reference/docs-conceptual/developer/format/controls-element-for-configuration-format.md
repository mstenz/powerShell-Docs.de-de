---
title: Controls-Element für Konfiguration (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368999"
---
# <a name="controls-element-for-configuration-format"></a>Element „Controls“ für Configuration (Format)

Definiert die allgemeinen Steuerelemente, die von allen Ansichten der Formatierungs Datei verwendet werden können.

Configuration-Element (Format) steuert Element der Konfiguration (Format)

## <a name="syntax"></a>Syntax

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

In den folgenden Abschnitten werden die Attribute, untergeordneten Elemente und das übergeordnete Element des `Controls`-Elements beschrieben.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Control-Element für Steuerelemente für die Konfiguration (Format)](./control-element-for-controls-for-configuration-format.md)|Erforderliches Element.<br /><br /> Definiert ein gängiges Steuerelement, das von allen Ansichten der Formatierungs Datei verwendet werden kann.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Description|
|-------------|-----------------|
|[Configuration-Element (Format)](./configuration-element-format.md)|Stellt das Element der obersten Ebene einer Formatierungs Datei dar.|

## <a name="remarks"></a>Hinweise

Sie können eine beliebige Anzahl von allgemeinen Steuerelementen erstellen. Für jedes Steuerelement müssen Sie den Namen angeben, der zum Verweisen auf das Steuerelement und die Komponenten des Steuer Elements verwendet wird.

## <a name="see-also"></a>Weitere Informationen

[Configuration-Element (Format)](./configuration-element-format.md)

[Control-Element für Steuerelemente für die Konfiguration (Format)](./control-element-for-controls-for-configuration-format.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
