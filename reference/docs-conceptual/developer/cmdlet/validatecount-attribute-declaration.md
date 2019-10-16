---
title: Validatecount-Attribut Deklaration | Microsoft-Dokumentation
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369229"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="b60f3-102">Attributdeklaration: ValidateCount</span><span class="sxs-lookup"><span data-stu-id="b60f3-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="b60f3-103">Das validatecount-Attribut gibt die minimale und maximale Anzahl von Argumenten an, die für einen Cmdlet-Parameter zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="b60f3-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b60f3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b60f3-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="b60f3-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="b60f3-105">Parameters</span></span>

<span data-ttu-id="b60f3-106">`MinLength` ([System. Int32][]) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b60f3-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="b60f3-107">Gibt die Mindestanzahl von Argumenten an.</span><span class="sxs-lookup"><span data-stu-id="b60f3-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="b60f3-108">`MaxLength` ([System. Int32][]) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b60f3-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="b60f3-109">Gibt die maximale Anzahl von Argumenten an.</span><span class="sxs-lookup"><span data-stu-id="b60f3-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="b60f3-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b60f3-110">Remarks</span></span>

- <span data-ttu-id="b60f3-111">Weitere Informationen zum Deklarieren dieses Attributs finden Sie unter [Validieren einer Argument Anzahl][].</span><span class="sxs-lookup"><span data-stu-id="b60f3-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="b60f3-112">Wenn dieses Attribut nicht aufgerufen wird, kann der entsprechende Cmdlet-Parameter über eine beliebige Anzahl von Argumenten verfügen.</span><span class="sxs-lookup"><span data-stu-id="b60f3-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="b60f3-113">Die Windows PowerShell-Laufzeit löst unter den folgenden Bedingungen einen Fehler aus:</span><span class="sxs-lookup"><span data-stu-id="b60f3-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="b60f3-114">Die Attribute "`MinLength`" und "`MaxLength`" sind nicht vom Typ " [System. Int32][]".</span><span class="sxs-lookup"><span data-stu-id="b60f3-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="b60f3-115">Der Wert des `MaxLength`-Attribut Parameters ist kleiner als der Wert des Attributs "`MinLength`".</span><span class="sxs-lookup"><span data-stu-id="b60f3-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="b60f3-116">Das validatecount-Attribut wird von der [System. Management. Automation. validatezähltattribute][] -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="b60f3-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b60f3-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b60f3-117">See Also</span></span>

<span data-ttu-id="b60f3-118">[System. Management. Automation. validatezähltattribute][]</span><span class="sxs-lookup"><span data-stu-id="b60f3-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="b60f3-119">[Validieren einer Argument Anzahl][]</span><span class="sxs-lookup"><span data-stu-id="b60f3-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="b60f3-120">[Schreiben eines Windows PowerShell-Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="b60f3-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Validieren einer Argument Anzahl]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Schreiben eines Windows PowerShell-Cmdlets]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. validatezähltattribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
