---
title: Validaterange-Attribut Deklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 560fa105ac3f93ae6334df0112f5290dfa20576c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692016"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="f9471-102">Attributdeklaration: ValidateRange</span><span class="sxs-lookup"><span data-stu-id="f9471-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="f9471-103">Das validaterange-Attribut gibt die minimalen und maximalen Werte (den Bereich) für das Cmdlet-Parameter Argument an.</span><span class="sxs-lookup"><span data-stu-id="f9471-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="f9471-104">Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f9471-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9471-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9471-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="f9471-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="f9471-106">Parameters</span></span>

<span data-ttu-id="f9471-107">`MinRange`([System. Object](/dotnet/api/system.object)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f9471-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="f9471-108">Gibt den zulässigen Mindestwert an.</span><span class="sxs-lookup"><span data-stu-id="f9471-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="f9471-109">`MaxRange`([System. Object](/dotnet/api/system.object)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f9471-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="f9471-110">Gibt den maximal zulässigen Wert an.</span><span class="sxs-lookup"><span data-stu-id="f9471-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9471-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f9471-111">Remarks</span></span>

- <span data-ttu-id="f9471-112">Die Windows PowerShell-Laufzeit löst einen Konstruktionsfehler aus, wenn der Wert des- `MinRange` Parameters größer als der Wert des- `MaxRange` Parameters ist.</span><span class="sxs-lookup"><span data-stu-id="f9471-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="f9471-113">Die Windows PowerShell-Laufzeit löst unter den folgenden Bedingungen einen Validierungs Fehler aus:</span><span class="sxs-lookup"><span data-stu-id="f9471-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="f9471-114">Wenn der Wert des Arguments kleiner als das `MinRange` Limit oder größer als das Limit ist `MaxRange` .</span><span class="sxs-lookup"><span data-stu-id="f9471-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="f9471-115">Wenn das Argument nicht vom gleichen Typ wie der `MinRange` und die Parameter ist `MaxRange` .</span><span class="sxs-lookup"><span data-stu-id="f9471-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="f9471-116">Das validaterange-Attribut wird von der [System. Management. Automation. validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) -Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="f9471-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9471-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f9471-117">See Also</span></span>

[<span data-ttu-id="f9471-118">System. Management. Automation. validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="f9471-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="f9471-119">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="f9471-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
