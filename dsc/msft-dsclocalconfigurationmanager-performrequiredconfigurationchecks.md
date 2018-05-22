---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="70492-103">PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="70492-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="70492-104">Startet eine Konsistenzprüfung unter Verwendung des Taskplaners.</span><span class="sxs-lookup"><span data-stu-id="70492-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="70492-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="70492-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="70492-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="70492-106">Parameters</span></span>
----------

<span data-ttu-id="70492-107">*Flags* \[in\] Eine Bitmaske, die den Typ der auszuführenden Konsistenzprüfung angibt.</span><span class="sxs-lookup"><span data-stu-id="70492-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="70492-108">Die folgenden Werte sind gültig und können mit einem bitweisen **ODER**-Vorgang kombiniert werden:</span><span class="sxs-lookup"><span data-stu-id="70492-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="70492-109">Wert</span><span class="sxs-lookup"><span data-stu-id="70492-109">Value</span></span> |<span data-ttu-id="70492-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="70492-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="70492-111">**1**</span><span class="sxs-lookup"><span data-stu-id="70492-111">**1**</span></span> | <span data-ttu-id="70492-112">Eine normale Konsistenzprüfung.</span><span class="sxs-lookup"><span data-stu-id="70492-112">A normal consistency check.</span></span> |
|<span data-ttu-id="70492-113">**2**</span><span class="sxs-lookup"><span data-stu-id="70492-113">**2**</span></span> | <span data-ttu-id="70492-114">Die Fortsetzung einer Konsistenzprüfung nach einem Neustart.</span><span class="sxs-lookup"><span data-stu-id="70492-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="70492-115">Dieser Wert sollte nicht mit anderen Werten kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="70492-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="70492-116">**4**</span><span class="sxs-lookup"><span data-stu-id="70492-116">**4**</span></span> | <span data-ttu-id="70492-117">Die Konfiguration sollte von dem Pull-Server abgerufen werden, der in der Metakonfiguration für den Knoten angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="70492-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="70492-118">Dieser Wert sollte immer mit **1** kombiniert werden, um einen Wert von **5** zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="70492-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="70492-119">**8**</span><span class="sxs-lookup"><span data-stu-id="70492-119">**8**</span></span> | <span data-ttu-id="70492-120">Senden des Status an den Berichtsserver.</span><span class="sxs-lookup"><span data-stu-id="70492-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="70492-121">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="70492-121">Return value</span></span>
------------

<span data-ttu-id="70492-122">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="70492-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="70492-123">Hinweise</span><span class="sxs-lookup"><span data-stu-id="70492-123">Remarks</span></span>

<span data-ttu-id="70492-124">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="70492-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="70492-125">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="70492-125">Requirements</span></span>
------------
><span data-ttu-id="70492-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="70492-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="70492-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="70492-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="70492-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="70492-128">See also</span></span>


[<span data-ttu-id="70492-129">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="70492-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)