---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: ae31ac30c152c96707b764ddaf00c924806afcfc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678787"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0e816-103">GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="0e816-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0e816-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="0e816-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e816-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0e816-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="0e816-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="0e816-106">Parameters</span></span>

<span data-ttu-id="0e816-107">*configurationData* \[in\] Gibt die zu sendenden Konfigurationsdaten an.</span><span class="sxs-lookup"><span data-stu-id="0e816-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="0e816-108">*configurations* \[out\] Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0e816-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="0e816-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="0e816-109">Return value</span></span>

<span data-ttu-id="0e816-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="0e816-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e816-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0e816-111">Remarks</span></span>

<span data-ttu-id="0e816-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="0e816-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e816-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0e816-113">Requirements</span></span>

<span data-ttu-id="0e816-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0e816-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0e816-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0e816-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0e816-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0e816-116">See also</span></span>

[<span data-ttu-id="0e816-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="0e816-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)