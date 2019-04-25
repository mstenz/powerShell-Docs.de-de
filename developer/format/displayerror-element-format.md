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
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066259"
---
# <a name="displayerror-element-format"></a>Element „DisplayError“ (Format)

Gibt an, dass die Zeichenfolge #ERR angezeigt wird, wenn ein Fehler auftritt, Anzeigen von Daten.

-Element (Format) DefaultSettings-Element (Format) DisplayError Konfigurationselement (Format)

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
