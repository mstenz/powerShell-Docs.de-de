---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047283"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1b4b9-103">EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="1b4b9-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1b4b9-104">Aktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="1b4b9-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b4b9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b4b9-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="1b4b9-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="1b4b9-106">Parameters</span></span>

<span data-ttu-id="1b4b9-107">*BreakAll* \[in\] Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.</span><span class="sxs-lookup"><span data-stu-id="1b4b9-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="1b4b9-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1b4b9-108">Return value</span></span>

<span data-ttu-id="1b4b9-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="1b4b9-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b4b9-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1b4b9-110">Remarks</span></span>

<span data-ttu-id="1b4b9-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="1b4b9-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b4b9-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1b4b9-112">Requirements</span></span>

<span data-ttu-id="1b4b9-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1b4b9-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1b4b9-114">\*\*Namespace: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1b4b9-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1b4b9-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1b4b9-115">See also</span></span>

[<span data-ttu-id="1b4b9-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="1b4b9-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)