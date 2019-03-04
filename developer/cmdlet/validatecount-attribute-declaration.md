---
title: ValidateCount Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859156"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="aaf14-102">Attributdeklaration: ValidateCount</span><span class="sxs-lookup"><span data-stu-id="aaf14-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="aaf14-103">Die ValidateCount-Attribut gibt an, die minimale und maximale Anzahl von Argumenten, die für ein Cmdlet-Parameter zulässig.</span><span class="sxs-lookup"><span data-stu-id="aaf14-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="aaf14-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="aaf14-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="aaf14-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="aaf14-105">Parameters</span></span>

<span data-ttu-id="aaf14-106">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="aaf14-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="aaf14-107">Gibt die minimale Anzahl von Argumenten an.</span><span class="sxs-lookup"><span data-stu-id="aaf14-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="aaf14-108">`MaxLength`([System. Int32](/dotnet/api/System.Int32)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="aaf14-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="aaf14-109">Gibt die maximale Anzahl von Argumenten an.</span><span class="sxs-lookup"><span data-stu-id="aaf14-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="aaf14-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="aaf14-110">Remarks</span></span>

- <span data-ttu-id="aaf14-111">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [wie Eingabe Validierungsregeln deklarieren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="aaf14-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="aaf14-112">Wenn dieses Attribut nicht aufgerufen wird, kann der entsprechende Cmdlet-Parameter eine beliebige Anzahl von Argumenten verfügen.</span><span class="sxs-lookup"><span data-stu-id="aaf14-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="aaf14-113">Die Windows PowerShell-Laufzeit löst einen Fehler in den folgenden Situationen aus:</span><span class="sxs-lookup"><span data-stu-id="aaf14-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="aaf14-114">Die `MinLength` und `MaxLength` Parameter sind nicht vom Typ [System. Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="aaf14-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="aaf14-115">Der Wert des der `MaxLength` Attributparameter ist kleiner als der Wert, der die `MinLength` Attributparameter.</span><span class="sxs-lookup"><span data-stu-id="aaf14-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="aaf14-116">Das ValidateCount-Attribut definiert ist, indem die [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) Klasse.</span><span class="sxs-lookup"><span data-stu-id="aaf14-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="aaf14-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aaf14-117">See Also</span></span>

[<span data-ttu-id="aaf14-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="aaf14-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="aaf14-119">Gewusst wie: Deklarieren Sie die Überprüfung der Eingabe-Regeln</span><span class="sxs-lookup"><span data-stu-id="aaf14-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="aaf14-120">Gewusst wie: Deklarieren Sie die Überprüfung der Eingabe-Regeln</span><span class="sxs-lookup"><span data-stu-id="aaf14-120">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="aaf14-121">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="aaf14-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
