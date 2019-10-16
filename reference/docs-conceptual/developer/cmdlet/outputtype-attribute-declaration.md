---
title: OutputType-Attribut Deklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365339"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="c5cd5-102">Attributdeklaration: OutputType</span><span class="sxs-lookup"><span data-stu-id="c5cd5-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="c5cd5-103">Das `OutputType`-Attribut identifiziert die .NET Framework Typen, die von einem Cmdlet, einer Funktion oder einem Skript zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c5cd5-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5cd5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c5cd5-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="c5cd5-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="c5cd5-105">Parameters</span></span>

<span data-ttu-id="c5cd5-106">Der Typ (`string[]` oder `Type[]`) ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c5cd5-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="c5cd5-107">Gibt die Typen an, die von der Cmdlet-Funktion oder dem Skript zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c5cd5-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="c5cd5-108">Parametersetname (String []) ist optional.</span><span class="sxs-lookup"><span data-stu-id="c5cd5-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="c5cd5-109">Gibt die Parametersätze an, die die im `type`-Parameter angegebenen Typen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="c5cd5-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="c5cd5-110">providercmdlet ist optional.</span><span class="sxs-lookup"><span data-stu-id="c5cd5-110">providerCmdlet Optional.</span></span> <span data-ttu-id="c5cd5-111">Gibt das Anbieter-Cmdlet an, das die im `type`-Parameter angegebenen Typen zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="c5cd5-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5cd5-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c5cd5-112">See Also</span></span>

[<span data-ttu-id="c5cd5-113">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c5cd5-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
