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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365339"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="befde-102">Attributdeklaration: OutputType</span><span class="sxs-lookup"><span data-stu-id="befde-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="befde-103">Das `OutputType`-Attribut identifiziert die .NET Framework Typen, die von einem Cmdlet, einer Funktion oder einem Skript zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="befde-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="befde-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="befde-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="befde-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="befde-105">Parameters</span></span>

<span data-ttu-id="befde-106">Der Typ (`string[]` oder `Type[]`) ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="befde-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="befde-107">Gibt die Typen an, die von der Cmdlet-Funktion oder dem Skript zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="befde-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="befde-108">Parametersetname (String []) ist optional.</span><span class="sxs-lookup"><span data-stu-id="befde-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="befde-109">Gibt die Parametersätze an, die die im `type`-Parameter angegebenen Typen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="befde-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="befde-110">providercmdlet ist optional.</span><span class="sxs-lookup"><span data-stu-id="befde-110">providerCmdlet Optional.</span></span> <span data-ttu-id="befde-111">Gibt das Anbieter-Cmdlet an, das die im `type`-Parameter angegebenen Typen zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="befde-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="befde-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="befde-112">See Also</span></span>

[<span data-ttu-id="befde-113">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="befde-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
