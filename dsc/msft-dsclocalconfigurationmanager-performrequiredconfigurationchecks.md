---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cf3ff-103">PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="cf3ff-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cf3ff-104">Startet eine Konsistenzprüfung unter Verwendung des Taskplaners.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="cf3ff-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cf3ff-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="cf3ff-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="cf3ff-106">Parameters</span></span>
----------

<span data-ttu-id="cf3ff-107">*Flags* \[in\]</span><span class="sxs-lookup"><span data-stu-id="cf3ff-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="cf3ff-108">Eine Bitmaske, die den Typ der auszuführenden Konsistenzprüfung angibt.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="cf3ff-109">Die folgenden Werte sind gültig und können mit einem bitweisen **ODER**-Vorgang kombiniert werden:</span><span class="sxs-lookup"><span data-stu-id="cf3ff-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="cf3ff-110">Wert</span><span class="sxs-lookup"><span data-stu-id="cf3ff-110">Value</span></span> |<span data-ttu-id="cf3ff-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cf3ff-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="cf3ff-112">**1**</span><span class="sxs-lookup"><span data-stu-id="cf3ff-112">**1**</span></span> | <span data-ttu-id="cf3ff-113">Eine normale Konsistenzprüfung.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-113">A normal consistency check.</span></span> |
|<span data-ttu-id="cf3ff-114">**2**</span><span class="sxs-lookup"><span data-stu-id="cf3ff-114">**2**</span></span> | <span data-ttu-id="cf3ff-115">Die Fortsetzung einer Konsistenzprüfung nach einem Neustart.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="cf3ff-116">Dieser Wert sollte nicht mit anderen Werten kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="cf3ff-117">**4**</span><span class="sxs-lookup"><span data-stu-id="cf3ff-117">**4**</span></span> | <span data-ttu-id="cf3ff-118">Die Konfiguration sollte von dem Pull-Server abgerufen werden, der in der Metakonfiguration für den Knoten angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="cf3ff-119">Dieser Wert sollte immer mit **1** kombiniert werden, um einen Wert von **5** zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="cf3ff-120">**8**</span><span class="sxs-lookup"><span data-stu-id="cf3ff-120">**8**</span></span> | <span data-ttu-id="cf3ff-121">Senden des Status an den Berichtsserver.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="cf3ff-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="cf3ff-122">Return value</span></span>
------------

<span data-ttu-id="cf3ff-123">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf3ff-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cf3ff-124">Remarks</span></span>

<span data-ttu-id="cf3ff-125">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="cf3ff-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cf3ff-126">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="cf3ff-126">Requirements</span></span>
------------
><span data-ttu-id="cf3ff-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cf3ff-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cf3ff-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf3ff-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cf3ff-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cf3ff-129">See also</span></span>


[<span data-ttu-id="cf3ff-130">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="cf3ff-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



