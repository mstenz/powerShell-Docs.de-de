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
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369959"
---
# <a name="cmdlet-attributes"></a>Cmdlet-Attribute

Windows PowerShell definiert mehrere Attribute, die Sie verwenden können, um Ihren Cmdlets allgemeine Funktionen hinzuzufügen, ohne diese Funktionalität in Ihrem eigenen Code implementieren zu müssen. Dies schließt das Cmdlet-Attribut ein, das eine Microsoft .NET Framework-Klasse als Cmdlet-Klasse identifiziert, das OutputType-Attribut, das die vom Cmdlet zurückgegebenen .NET Framework Typen angibt, das Parameter Attribut, das öffentliche Eigenschaften als Cmdlet identifiziert. und mehr.

## <a name="in-this-section"></a>In diesem Abschnitt

[Attribute im Cmdlet-Code](./attributes-in-cmdlet-code.md) Beschreibt den Vorteil der Verwendung von Attributen in Cmdlet-Code.

[Attributtypen](./attribute-types.md) Beschreibt die unterschiedlichen Attribute, die eine Cmdlet-Klasse ergänzen können.

[Alias Attribut Deklaration](./alias-attribute-declaration.md) Beschreibt, wie Aliase für einen Cmdlet-Parameternamen definiert werden.

[Cmdlet-Attribut Deklaration](./cmdlet-attribute-declaration.md) Beschreibt, wie eine .NET Framework Klasse als Cmdlet definiert wird.

[Deklaration der Credential-Attribute](./credential-attribute-declaration.md) Beschreibt das Hinzufügen von Unterstützung für das konvertiert von Zeichen folgen Eingaben in ein [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -Objekt.

[OutputType-Attribut Deklaration](./outputtype-attribute-declaration.md) Beschreibt, wie die vom Cmdlet zurückgegebenen .NET Framework Typen angegeben werden.

[Parameter Attribut Deklaration](./parameter-attribute-declaration.md) Beschreibt, wie die Parameter eines Cmdlets definiert werden.

[Validatecount-Attribut Deklaration](./validatecount-attribute-declaration.md) Beschreibt, wie Sie definieren, wie viele Argumente für einen Parameter zulässig sind.

[ValidateLength-Attribut Deklaration](./validatelength-attribute-declaration.md) Beschreibt, wie die Länge (in Zeichen) eines Parameter Arguments definiert wird.

[Validatepattern-Attribut Deklaration](./validatepattern-attribute-declaration.md) Beschreibt, wie die gültigen Muster für ein Parameter Argument definiert werden.

[Validaterange-Attribut Deklaration](./validaterange-attribute-declaration.md) Beschreibt, wie der gültige Bereich für ein Parameter Argument definiert wird.

[Validateset-Attribut Deklaration](./validateset-attribute-declaration.md) Beschreibt, wie die möglichen Werte für ein Parameter Argument definiert werden.

## <a name="reference"></a>Verweis

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
