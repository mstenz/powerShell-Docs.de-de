---
title: ValidateRange Attributdeklaration | Microsoft-Dokumentation
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
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067109"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="91b7d-102">Attributdeklaration: ValidateRange</span><span class="sxs-lookup"><span data-stu-id="91b7d-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="91b7d-103">Die ValidateRange-Attribut gibt an, die minimalen und maximalen Werte (Bereich) für das Argument der Cmdlet-Parameter.</span><span class="sxs-lookup"><span data-stu-id="91b7d-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="91b7d-104">Dieses Attribut kann auch von Windows PowerShell-Funktionen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="91b7d-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="91b7d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="91b7d-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="91b7d-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="91b7d-106">Parameters</span></span>

<span data-ttu-id="91b7d-107">`MinRange` (["System.Object"](/dotnet/api/system.object)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="91b7d-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="91b7d-108">Gibt an, der zulässige Mindestwert.</span><span class="sxs-lookup"><span data-stu-id="91b7d-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="91b7d-109">`MaxRange` (["System.Object"](/dotnet/api/system.object)) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="91b7d-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="91b7d-110">Gibt den zulässigen Höchstwert an.</span><span class="sxs-lookup"><span data-stu-id="91b7d-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="91b7d-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="91b7d-111">Remarks</span></span>

- <span data-ttu-id="91b7d-112">Die Windows PowerShell-Laufzeit löst einen Fehler für die Erstellung bei den Wert des der `MinRange` -Parameter ist größer als der Wert von der `MaxRange` Parameter.</span><span class="sxs-lookup"><span data-stu-id="91b7d-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="91b7d-113">Die Windows PowerShell-Laufzeit löst einen Validierungsfehler in den folgenden Situationen aus:</span><span class="sxs-lookup"><span data-stu-id="91b7d-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="91b7d-114">Wenn der Wert des Arguments ist kleiner als der `MinRange` Grenzwert oder größer als die `MaxRange` Grenzwert.</span><span class="sxs-lookup"><span data-stu-id="91b7d-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="91b7d-115">Wenn das Argument ist nicht vom gleichen Typ wie die `MinRange` und `MaxRange` Parameter.</span><span class="sxs-lookup"><span data-stu-id="91b7d-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="91b7d-116">Das ValidateRange-Attribut definiert ist, indem die [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) Klasse.</span><span class="sxs-lookup"><span data-stu-id="91b7d-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="91b7d-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="91b7d-117">See Also</span></span>

[<span data-ttu-id="91b7d-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="91b7d-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="91b7d-119">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="91b7d-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
