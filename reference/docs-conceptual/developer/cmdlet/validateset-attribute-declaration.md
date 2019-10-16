---
title: Validateset-Attribut Deklaration | Microsoft-Dokumentation
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364279"
---
# <a name="validateset-attribute-declaration"></a><span data-ttu-id="f09fb-102">Attributdeklaration: ValidateSet</span><span class="sxs-lookup"><span data-stu-id="f09fb-102">ValidateSet Attribute Declaration</span></span>

<span data-ttu-id="f09fb-103">Das validatesetattribute-Attribut gibt einen Satz möglicher Werte für ein Cmdlet-Parameter Argument an.</span><span class="sxs-lookup"><span data-stu-id="f09fb-103">The ValidateSetAttribute attribute specifies a set of possible values for a cmdlet parameter argument.</span></span> <span data-ttu-id="f09fb-104">Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f09fb-104">This attribute can also be used by Windows PowerShell functions.</span></span>

<span data-ttu-id="f09fb-105">Wenn dieses Attribut angegeben wird, bestimmt die Windows PowerShell-Laufzeit, ob das angegebene Argument für den Cmdlet-Parameter mit einem Element im angegebenen Element Satz übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="f09fb-105">When this attribute is specified, the Windows PowerShell runtime determines whether the supplied argument for the cmdlet parameter matches an element in the supplied element set.</span></span> <span data-ttu-id="f09fb-106">Das-Cmdlet wird nur ausgeführt, wenn das Parameter Argument mit einem Element im Satz übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="f09fb-106">The cmdlet is run only if the parameter argument matches an element in the set.</span></span> <span data-ttu-id="f09fb-107">Wenn keine Entsprechung gefunden wird, wird von der Windows PowerShell-Laufzeit ein Fehler ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="f09fb-107">If no match is found, an error is thrown by the Windows PowerShell runtime.</span></span>

## <a name="syntax"></a><span data-ttu-id="f09fb-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="f09fb-108">Syntax</span></span>

```csharp
[ValidateSetAttribute(params string[] validValues)]
[ValidateSetAttribute(params string[] validValues, Named Parameters)]
```

#### <a name="parameters"></a><span data-ttu-id="f09fb-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="f09fb-109">Parameters</span></span>

<span data-ttu-id="f09fb-110">`ValidValues` ([System. String](/dotnet/api/System.String)) ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f09fb-110">`ValidValues` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="f09fb-111">Gibt die gültigen Parameter Element Werte an.</span><span class="sxs-lookup"><span data-stu-id="f09fb-111">Specifies the valid parameter element values.</span></span> <span data-ttu-id="f09fb-112">Im folgenden Beispiel wird gezeigt, wie ein-Element oder mehrere-Elemente angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f09fb-112">The following sample shows how to specify one element or multiple elements.</span></span>

```csharp
[ValidateSetAttribute("Steve")]
[ValidateSetAttribute("Steve","Mary")]
```

<span data-ttu-id="f09fb-113">der optionale benannte Parameter `IgnoreCase` ([System. Boolean](/dotnet/api/System.Boolean)).</span><span class="sxs-lookup"><span data-stu-id="f09fb-113">`IgnoreCase` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="f09fb-114">Der Standardwert `true` gibt an, dass der Fall ignoriert wird.</span><span class="sxs-lookup"><span data-stu-id="f09fb-114">The default value of `true` indicates that case is ignored.</span></span> <span data-ttu-id="f09fb-115">Bei einem Wert von "`false`" wird die Groß-/Kleinschreibung berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="f09fb-115">A value of `false` makes the cmdlet case-sensitive.</span></span>

## <a name="remarks"></a><span data-ttu-id="f09fb-116">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f09fb-116">Remarks</span></span>

- <span data-ttu-id="f09fb-117">Dieses Attribut kann nur einmal pro Parameter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f09fb-117">This attribute can be used only once per parameter.</span></span>

- <span data-ttu-id="f09fb-118">Wenn der Parameterwert ein Array ist, muss jedes Element des Arrays mit einem Element des Attribut Satzes identisch sein.</span><span class="sxs-lookup"><span data-stu-id="f09fb-118">If the parameter value is an array, every element of the array must match an element of the attribute set.</span></span>

- <span data-ttu-id="f09fb-119">Das validatesetattribute-Attribut wird von der [System. Management. Automation. validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="f09fb-119">The ValidateSetAttribute attribute is defined by the [System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f09fb-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f09fb-120">See Also</span></span>

[<span data-ttu-id="f09fb-121">System. Management. Automation. validatesetattribute</span><span class="sxs-lookup"><span data-stu-id="f09fb-121">System.Management.Automation.Validatesetattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[<span data-ttu-id="f09fb-122">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f09fb-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
