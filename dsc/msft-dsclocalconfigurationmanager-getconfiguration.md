---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="76e14-103">GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="76e14-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="76e14-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="76e14-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="76e14-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="76e14-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="76e14-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="76e14-106">Parameters</span></span>
----------

<span data-ttu-id="76e14-107">*configurationData* \[in\] Gibt die zu sendenden Konfigurationsdaten an.</span><span class="sxs-lookup"><span data-stu-id="76e14-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="76e14-108">*configurations* \[out\] Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="76e14-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="76e14-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="76e14-109">Return value</span></span>
------------

<span data-ttu-id="76e14-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="76e14-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="76e14-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="76e14-111">Remarks</span></span>

<span data-ttu-id="76e14-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="76e14-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="76e14-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="76e14-113">Requirements</span></span>
------------
><span data-ttu-id="76e14-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="76e14-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="76e14-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="76e14-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="76e14-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="76e14-116">See also</span></span>


[<span data-ttu-id="76e14-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="76e14-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)