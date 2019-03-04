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
# <a name="cmdlet-attributes"></a><span data-ttu-id="463e0-102">Cmdlet-Attribute</span><span class="sxs-lookup"><span data-stu-id="463e0-102">Cmdlet Attributes</span></span>

<span data-ttu-id="463e0-103">Windows PowerShell definiert mehrere Attribute, die Sie verwenden können, Ihre Cmdlets allgemeine Funktionen hinzu, ohne diese Funktionalität in Ihren eigenen Code implementieren zu müssen.</span><span class="sxs-lookup"><span data-stu-id="463e0-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="463e0-104">Dies schließt die Cmdlet-Attribut, das Microsoft .NET Framework-Klasse als eine Cmdlet-Klasse, die OutputType-Attribut identifiziert, der angibt, die .NET Framework-Datentypen zurückgegeben, die vom-Cmdlet, das Parameter-Attribut, die öffentliche Eigenschaften als Cmdlet zu identifizieren Parameter und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="463e0-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="463e0-105">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="463e0-105">In This Section</span></span>

<span data-ttu-id="463e0-106">[Attribute in der Cmdlet-Code](./attributes-in-cmdlet-code.md) den Vorteil der Verwendung von Attributen in der Cmdlet-Code beschreibt.</span><span class="sxs-lookup"><span data-stu-id="463e0-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="463e0-107">[Attributtypen](./attribute-types.md) beschreibt die verschiedenen Attribute, die eine Cmdlet-Klasse ergänzen können.</span><span class="sxs-lookup"><span data-stu-id="463e0-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="463e0-108">[Alias-Attributdeklaration](./alias-attribute-declaration.md) wird beschrieben, wie Aliase für einen Cmdlet-Parameternamen definieren.</span><span class="sxs-lookup"><span data-stu-id="463e0-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="463e0-109">[-Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md) beschreibt, wie Sie .NET Framework-Klasse als ein Cmdlet definieren.</span><span class="sxs-lookup"><span data-stu-id="463e0-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="463e0-110">[Anmeldeinformationen Attributdeklaration](./credential-attribute-declaration.md) beschreibt das Hinzufügen von Unterstützung für das Konvertieren der Zeichenfolgeneingabe in eine [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) Objekt.</span><span class="sxs-lookup"><span data-stu-id="463e0-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="463e0-111">[OutputType-Attribut Deklaration](./outputtype-attribute-declaration.md) beschreibt, wie die .NET Framework-Typen, die vom Cmdlet zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="463e0-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="463e0-112">[Parameter-Attributdeklaration](./parameter-attribute-declaration.md) beschreibt, wie Sie die Parameter eines Cmdlets zu definieren.</span><span class="sxs-lookup"><span data-stu-id="463e0-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="463e0-113">[ValidateCount Attributdeklaration](./validatecount-attribute-declaration.md) wird beschrieben, wie Sie definieren, wie viele Argumente für einen Parameter zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="463e0-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="463e0-114">[ValidateLength auf Attributdeklaration](./validatelength-attribute-declaration.md) wird beschrieben, wie die Länge (in Zeichen) eines Parameters-Arguments definieren.</span><span class="sxs-lookup"><span data-stu-id="463e0-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="463e0-115">[ValidatePattern Attributdeklaration](./validatepattern-attribute-declaration.md) wird beschrieben, wie die gültigen Muster für ein Parameterargument zu definieren.</span><span class="sxs-lookup"><span data-stu-id="463e0-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="463e0-116">[ValidateRange Attributdeklaration](./validaterange-attribute-declaration.md) wird beschrieben, wie den gültigen Bereich für ein Parameterargument zu definieren.</span><span class="sxs-lookup"><span data-stu-id="463e0-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="463e0-117">[ValidateSet Attributdeklaration](./validateset-attribute-declaration.md) beschreibt, wie Sie die möglichen Werte für ein Parameterargument zu definieren.</span><span class="sxs-lookup"><span data-stu-id="463e0-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="463e0-118">Verweis</span><span class="sxs-lookup"><span data-stu-id="463e0-118">Reference</span></span>

[<span data-ttu-id="463e0-119">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="463e0-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
