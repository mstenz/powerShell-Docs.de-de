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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853716"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="efc2a-102">Attributdeklaration: OutputType</span><span class="sxs-lookup"><span data-stu-id="efc2a-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="efc2a-103">Die `OutputType` Attribut identifiziert, die .NET Framework-Typen, die von einem Cmdlet, Funktion oder Skript zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="efc2a-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="efc2a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="efc2a-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="efc2a-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="efc2a-105">Parameters</span></span>

<span data-ttu-id="efc2a-106">Typ (`string[]` oder `Type[]`) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="efc2a-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="efc2a-107">Gibt die Typen, die von der Cmdlet-Funktion oder Skript zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="efc2a-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="efc2a-108">ParameterSetName (testeigenschaftentyp Optional.</span><span class="sxs-lookup"><span data-stu-id="efc2a-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="efc2a-109">Gibt an, der Parameter legt fest, die im angegebenen Typen zurückgeben der `type` Parameter.</span><span class="sxs-lookup"><span data-stu-id="efc2a-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="efc2a-110">ProviderCmdlet Optional.</span><span class="sxs-lookup"><span data-stu-id="efc2a-110">providerCmdlet Optional.</span></span> <span data-ttu-id="efc2a-111">Gibt an, das Anbieter-Cmdlet, das im angegebenen Typen gibt die `type` Parameter.</span><span class="sxs-lookup"><span data-stu-id="efc2a-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="efc2a-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="efc2a-112">See Also</span></span>

[<span data-ttu-id="efc2a-113">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="efc2a-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
