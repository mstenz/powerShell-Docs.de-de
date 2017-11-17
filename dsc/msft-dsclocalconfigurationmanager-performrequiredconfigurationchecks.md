---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="32bd4-103">PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="32bd4-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="32bd4-104">Startet eine Konsistenzprüfung unter Verwendung des Taskplaners.</span><span class="sxs-lookup"><span data-stu-id="32bd4-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="32bd4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="32bd4-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="32bd4-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="32bd4-106">Parameters</span></span>
----------

<span data-ttu-id="32bd4-107">*Flags* \[in\]</span><span class="sxs-lookup"><span data-stu-id="32bd4-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="32bd4-108">Eine Bitmaske, die den Typ der auszuführenden Konsistenzprüfung angibt.</span><span class="sxs-lookup"><span data-stu-id="32bd4-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="32bd4-109">Die folgenden Werte sind gültig und können mit einem bitweisen **ODER**-Vorgang kombiniert werden:</span><span class="sxs-lookup"><span data-stu-id="32bd4-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="32bd4-110">Wert</span><span class="sxs-lookup"><span data-stu-id="32bd4-110">Value</span></span> |<span data-ttu-id="32bd4-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="32bd4-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="32bd4-112">**1**</span><span class="sxs-lookup"><span data-stu-id="32bd4-112">**1**</span></span> | <span data-ttu-id="32bd4-113">Eine normale Konsistenzprüfung.</span><span class="sxs-lookup"><span data-stu-id="32bd4-113">A normal consistency check.</span></span> |
|<span data-ttu-id="32bd4-114">**2**</span><span class="sxs-lookup"><span data-stu-id="32bd4-114">**2**</span></span> | <span data-ttu-id="32bd4-115">Die Fortsetzung einer Konsistenzprüfung nach einem Neustart.</span><span class="sxs-lookup"><span data-stu-id="32bd4-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="32bd4-116">Dieser Wert sollte nicht mit anderen Werten kombiniert werden.</span><span class="sxs-lookup"><span data-stu-id="32bd4-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="32bd4-117">**4**</span><span class="sxs-lookup"><span data-stu-id="32bd4-117">**4**</span></span> | <span data-ttu-id="32bd4-118">Die Konfiguration sollte von dem Pull-Server abgerufen werden, der in der Metakonfiguration für den Knoten angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="32bd4-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="32bd4-119">Dieser Wert sollte immer mit **1** kombiniert werden, um einen Wert von **5** zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="32bd4-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="32bd4-120">**8**</span><span class="sxs-lookup"><span data-stu-id="32bd4-120">**8**</span></span> | <span data-ttu-id="32bd4-121">Senden des Status an den Berichtsserver.</span><span class="sxs-lookup"><span data-stu-id="32bd4-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="32bd4-122">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="32bd4-122">Return value</span></span>
------------

<span data-ttu-id="32bd4-123">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="32bd4-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="32bd4-124">Hinweise</span><span class="sxs-lookup"><span data-stu-id="32bd4-124">Remarks</span></span>

<span data-ttu-id="32bd4-125">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="32bd4-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="32bd4-126">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="32bd4-126">Requirements</span></span>
------------
><span data-ttu-id="32bd4-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="32bd4-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="32bd4-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="32bd4-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="32bd4-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="32bd4-129">See also</span></span>


[<span data-ttu-id="32bd4-130">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="32bd4-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



