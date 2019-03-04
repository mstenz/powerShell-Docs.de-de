---
title: Cmdlet-Attribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853916"
---
# <a name="cmdlet-attributes"></a>Cmdlet-Attribute

Windows PowerShell definiert mehrere Attribute, die Sie verwenden können, Ihre Cmdlets allgemeine Funktionen hinzu, ohne diese Funktionalität in Ihren eigenen Code implementieren zu müssen. Dies schließt die Cmdlet-Attribut, das Microsoft .NET Framework-Klasse als eine Cmdlet-Klasse, die OutputType-Attribut identifiziert, der angibt, die .NET Framework-Datentypen zurückgegeben, die vom-Cmdlet, das Parameter-Attribut, die öffentliche Eigenschaften als Cmdlet zu identifizieren Parameter und vieles mehr.

## <a name="in-this-section"></a>In diesem Abschnitt

[Attribute in der Cmdlet-Code](./attributes-in-cmdlet-code.md) den Vorteil der Verwendung von Attributen in der Cmdlet-Code beschreibt.

[Attributtypen](./attribute-types.md) beschreibt die verschiedenen Attribute, die eine Cmdlet-Klasse ergänzen können.

[Alias-Attributdeklaration](./alias-attribute-declaration.md) wird beschrieben, wie Aliase für einen Cmdlet-Parameternamen definieren.

[-Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md) beschreibt, wie Sie .NET Framework-Klasse als ein Cmdlet definieren.

[Anmeldeinformationen Attributdeklaration](./credential-attribute-declaration.md) beschreibt das Hinzufügen von Unterstützung für das Konvertieren der Zeichenfolgeneingabe in eine [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) Objekt.

[OutputType-Attribut Deklaration](./outputtype-attribute-declaration.md) beschreibt, wie die .NET Framework-Typen, die vom Cmdlet zurückgegeben.

[Parameter-Attributdeklaration](./parameter-attribute-declaration.md) beschreibt, wie Sie die Parameter eines Cmdlets zu definieren.

[ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md) wird beschrieben, wie Sie definieren, wie viele Argumente für einen Parameter zulässig sind.

[ValidateLength auf Attributdeklaration](./validatelength-attribute-declaration.md) wird beschrieben, wie die Länge (in Zeichen) eines Parameters-Arguments definieren.

[ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md) wird beschrieben, wie die gültigen Muster für ein Parameterargument zu definieren.

[ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md) wird beschrieben, wie den gültigen Bereich für ein Parameterargument zu definieren.

[ValidateSet Attributdeklaration](./validateset-attribute-declaration.md) beschreibt, wie Sie die möglichen Werte für ein Parameterargument zu definieren.

## <a name="reference"></a>Verweis

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
