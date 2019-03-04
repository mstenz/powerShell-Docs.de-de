---
title: ValidateSet Attributdeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateSet
- ValidateSet attribute, described
- ValidateSet attribute
ms.assetid: 4a6f97ab-45b2-4f3d-84d4-30acf8e074d0
caps.latest.revision: 12
ms.openlocfilehash: b036f39cd01ffe4b4ce7db9627cb6da0d5327190
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861206"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="531fe-102">Attributdeklaration: ValidateSet</span><span class="sxs-lookup"><span data-stu-id="531fe-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="531fe-103">Die ValidateSetAttribute-Attribut gibt an, einen Satz möglicher Werte für ein Cmdlet-Parameter-Argument.</span><span class="sxs-lookup"><span data-stu-id="531fe-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="531fe-104">Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="531fe-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="531fe-105">Wenn dieses Attribut angegeben wird, bestimmt die Windows PowerShell-Laufzeit an, ob das angegebene Argument für die Cmdlet-Parameter ein Element in der Gruppe angegebenen Element entspricht.</span><span class="sxs-lookup"><span data-stu-id="531fe-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="531fe-106">Das Cmdlet ausgeführt wird, nur dann, wenn das Parameterargument ein Element in der Gruppe entspricht.</span><span class="sxs-lookup"><span data-stu-id="531fe-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="531fe-107">Wenn keine Übereinstimmung gefunden wird, wird ein Fehler von der Windows PowerShell-Laufzeit ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="531fe-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="531fe-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="531fe-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="531fe-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="531fe-109">Parameters</span></span>

<span data-ttu-id="531fe-110">`ValidValues` ([System.String](/dotnet/api/System.String)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="531fe-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="531fe-111">Gibt die gültigen Parameterwerte des Elements an.</span><span class="sxs-lookup"><span data-stu-id="531fe-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="531fe-112">Das folgende Beispiel zeigt, wie Sie ein Element oder mehrere Elemente angeben.</span><span class="sxs-lookup"><span data-stu-id="531fe-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="531fe-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional benannter Parameter.</span><span class="sxs-lookup"><span data-stu-id="531fe-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="531fe-114">Der Standardwert von `true` gibt an, dass die Groß-/Kleinschreibung ignoriert wird.</span><span class="sxs-lookup"><span data-stu-id="531fe-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="531fe-115">Der Wert `false` macht das Cmdlet Groß-/Kleinschreibung beachtet.</span><span class="sxs-lookup"><span data-stu-id="531fe-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="531fe-116">Hinweise</span><span class="sxs-lookup"><span data-stu-id="531fe-116">Remarks</span></span>

- <span data-ttu-id="531fe-117">Dieses Attribut kann nur einmal pro Parameter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="531fe-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="531fe-118">Wenn der Wert des Parameters ein Array ist, muss jedes Element des Arrays ein Element von dem festgelegten Attribut übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="531fe-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="531fe-119">Das ValidateSetAttribute-Attribut definiert ist, indem die [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) Klasse.</span><span class="sxs-lookup"><span data-stu-id="531fe-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="531fe-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="531fe-120">See Also</span></span>

[<span data-ttu-id="531fe-121">System.Management.Automation.Validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="531fe-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="531fe-122">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="531fe-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
