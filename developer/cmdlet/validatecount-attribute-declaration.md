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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067177"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="fc661-102">Attributdeklaration: ValidateCount</span><span class="sxs-lookup"><span data-stu-id="fc661-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="fc661-103">Die ValidateCount-Attribut gibt an, die minimale und maximale Anzahl von Argumenten, die für ein Cmdlet-Parameter zulässig.</span><span class="sxs-lookup"><span data-stu-id="fc661-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc661-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc661-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="fc661-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="fc661-105">Parameters</span></span>

<span data-ttu-id="fc661-106">`MinLength` ([System.Int32][]) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fc661-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="fc661-107">Gibt die minimale Anzahl von Argumenten an.</span><span class="sxs-lookup"><span data-stu-id="fc661-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="fc661-108">`MaxLength`([System.Int32][]) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="fc661-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="fc661-109">Gibt die maximale Anzahl von Argumenten an.</span><span class="sxs-lookup"><span data-stu-id="fc661-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc661-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fc661-110">Remarks</span></span>

- <span data-ttu-id="fc661-111">Weitere Informationen dazu, wie Sie dieses Attribut zu deklarieren, finden Sie unter [Wie Sie eine Anzahl an Argumenten überprüfen][].</span><span class="sxs-lookup"><span data-stu-id="fc661-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="fc661-112">Wenn dieses Attribut nicht aufgerufen wird, kann der entsprechende Cmdlet-Parameter eine beliebige Anzahl von Argumenten verfügen.</span><span class="sxs-lookup"><span data-stu-id="fc661-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="fc661-113">Die Windows PowerShell-Laufzeit löst einen Fehler in den folgenden Situationen aus:</span><span class="sxs-lookup"><span data-stu-id="fc661-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="fc661-114">Die `MinLength` und `MaxLength` Parameter sind nicht vom Typ [System.Int32][].</span><span class="sxs-lookup"><span data-stu-id="fc661-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="fc661-115">Der Wert des der `MaxLength` Attributparameter ist kleiner als der Wert, der die `MinLength` Attributparameter.</span><span class="sxs-lookup"><span data-stu-id="fc661-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="fc661-116">Das ValidateCount-Attribut definiert ist, indem die [System.Management.Automation.ValidateCountAttribute][] Klasse.</span><span class="sxs-lookup"><span data-stu-id="fc661-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc661-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fc661-117">See Also</span></span>

<span data-ttu-id="fc661-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="fc661-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="fc661-119">[Wie Sie eine Anzahl an Argumenten überprüfen][]</span><span class="sxs-lookup"><span data-stu-id="fc661-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="fc661-120">[Schreiben eines Windows PowerShell-Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="fc661-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Wie Sie eine Anzahl an Argumenten überprüfen]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Schreiben eines Windows PowerShell-Cmdlets]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
