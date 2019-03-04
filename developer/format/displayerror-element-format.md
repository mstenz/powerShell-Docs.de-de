---
title: DisplayError-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854916"
---
# <a name="displayerror-element-format"></a>Element „DisplayError“ (Format)

Gibt an, dass die Zeichenfolge #ERR angezeigt wird, wenn ein Fehler auftritt, Anzeigen von Daten.

-Element (Format) DefaultSettings-Element (Format) DisplayError Konfigurationselement (Frmat)

## <a name="syntax"></a>Syntax

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente

Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `DisplayError` Element.

### <a name="attributes"></a>Attributes

Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[DefaultSettings-Element (Format)](./defaultsettings-element-format.md)|Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten.|

## <a name="remarks"></a>Hinweise

Standardmäßig tritt ein Fehler beim Versuch, ein Datenelement, angezeigt wird der Speicherort der Daten leer gelassen. Wenn dieses Element die #ERR-Zeichenfolge "true" festgelegt ist, wird angezeigt.

## <a name="see-also"></a>Weitere Informationen

[DefaultSettings-Element (Format)](./defaultsettings-element-format.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
