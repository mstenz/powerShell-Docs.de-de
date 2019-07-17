---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration-Methode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734386"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="c83e0-103">RemoveConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="c83e0-103">RemoveConfiguration method</span></span>

<span data-ttu-id="c83e0-104">Entfernt die Konfigurationsdateien.</span><span class="sxs-lookup"><span data-stu-id="c83e0-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="c83e0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c83e0-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="c83e0-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="c83e0-106">Parameters</span></span>

<span data-ttu-id="c83e0-107">*Stage* \[in\] Gibt an, welches Konfigurationsdokument entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c83e0-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="c83e0-108">Die folgenden Werte sind gültig:</span><span class="sxs-lookup"><span data-stu-id="c83e0-108">The following values are valid:</span></span>

|<span data-ttu-id="c83e0-109">Wert</span><span class="sxs-lookup"><span data-stu-id="c83e0-109">Value</span></span> |<span data-ttu-id="c83e0-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c83e0-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="c83e0-111">**1**</span><span class="sxs-lookup"><span data-stu-id="c83e0-111">**1**</span></span> | <span data-ttu-id="c83e0-112">Das **aktuelle** (Current) Konfigurationsdokument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="c83e0-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="c83e0-113">**2**</span><span class="sxs-lookup"><span data-stu-id="c83e0-113">**2**</span></span> | <span data-ttu-id="c83e0-114">Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="c83e0-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="c83e0-115">**4**</span><span class="sxs-lookup"><span data-stu-id="c83e0-115">**4**</span></span> | <span data-ttu-id="c83e0-116">Das **vorherige** (Previous) Konfigurationsdokument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="c83e0-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="c83e0-117">*Force* \[in\] **true**, um das Entfernen der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="c83e0-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c83e0-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c83e0-118">Return value</span></span>

<span data-ttu-id="c83e0-119">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="c83e0-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c83e0-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c83e0-120">Remarks</span></span>

<span data-ttu-id="c83e0-121">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="c83e0-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c83e0-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c83e0-122">Requirements</span></span>

<span data-ttu-id="c83e0-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c83e0-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c83e0-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c83e0-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c83e0-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c83e0-125">See also</span></span>

[<span data-ttu-id="c83e0-126">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="c83e0-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
