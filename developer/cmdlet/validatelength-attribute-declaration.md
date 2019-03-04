---
title: ValidateLength auf Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858866"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="c0a1f-102">Attributdeklaration: ValidateLength</span><span class="sxs-lookup"><span data-stu-id="c0a1f-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="c0a1f-103">Die validateLength auf-Attribut gibt an, die minimale und maximale Anzahl von Zeichen für ein Cmdlet-Parameter-Argument.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="c0a1f-104">Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="c0a1f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c0a1f-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="c0a1f-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="c0a1f-106">Parameters</span></span>

<span data-ttu-id="c0a1f-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="c0a1f-108">Gibt die minimale Anzahl von Zeichen zulässig.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="c0a1f-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="c0a1f-110">Gibt die maximale Anzahl zulässiger Zeichen.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0a1f-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c0a1f-111">Remarks</span></span>

- <span data-ttu-id="c0a1f-112">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [wie Eingabe Validierungsregeln deklarieren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="c0a1f-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>
- <span data-ttu-id="c0a1f-113">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [wie Eingabe Validierungsregeln deklarieren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="c0a1f-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="c0a1f-114">Wenn dieses Attribut nicht verwendet wird, kann das entsprechende Parameterargument mit beliebiger Länge sein.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="c0a1f-115">Die Windows PowerShell-Laufzeit löst einen Fehler in den folgenden Situationen aus:</span><span class="sxs-lookup"><span data-stu-id="c0a1f-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="c0a1f-116">Bei den Wert des der `MaxLength` Attributparameter ist kleiner als der Wert, der die `MinLength` Attributparameter.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="c0a1f-117">Wenn die `MaxLength` Attributparameter auf 0 festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="c0a1f-118">Wenn das Argument keine Zeichenfolge ist.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-118">When the argument is not a string.</span></span>

- <span data-ttu-id="c0a1f-119">Das Attribut validateLength auf wird definiert, durch die [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) Klasse.</span><span class="sxs-lookup"><span data-stu-id="c0a1f-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0a1f-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c0a1f-120">See Also</span></span>

[<span data-ttu-id="c0a1f-121">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="c0a1f-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="c0a1f-122">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c0a1f-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
