---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078689"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="79dff-103">RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="79dff-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="79dff-104">Entfernt die Konfigurationsdateien.</span><span class="sxs-lookup"><span data-stu-id="79dff-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="79dff-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="79dff-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="79dff-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="79dff-106">Parameters</span></span>

<span data-ttu-id="79dff-107">*Stage* \[in\] Gibt an, welches Konfigurationsdokument entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="79dff-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="79dff-108">Die folgenden Werte sind gültig:</span><span class="sxs-lookup"><span data-stu-id="79dff-108">The following values are valid:</span></span>

|<span data-ttu-id="79dff-109">Wert</span><span class="sxs-lookup"><span data-stu-id="79dff-109">Value</span></span> |<span data-ttu-id="79dff-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="79dff-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="79dff-111">**1**</span><span class="sxs-lookup"><span data-stu-id="79dff-111">**1**</span></span> | <span data-ttu-id="79dff-112">Das **aktuelle** (Current) Konfigurationsdokument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="79dff-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="79dff-113">**2**</span><span class="sxs-lookup"><span data-stu-id="79dff-113">**2**</span></span> | <span data-ttu-id="79dff-114">Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="79dff-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="79dff-115">**4**</span><span class="sxs-lookup"><span data-stu-id="79dff-115">**4**</span></span> | <span data-ttu-id="79dff-116">Das **vorherige** (Previous) Konfigurationsdokument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="79dff-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="79dff-117">*Force* \[in\] **true**, um das Entfernen der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="79dff-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="79dff-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="79dff-118">Return value</span></span>

<span data-ttu-id="79dff-119">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="79dff-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="79dff-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="79dff-120">Remarks</span></span>

<span data-ttu-id="79dff-121">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="79dff-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="79dff-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="79dff-122">Requirements</span></span>

<span data-ttu-id="79dff-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="79dff-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="79dff-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="79dff-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="79dff-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="79dff-125">See also</span></span>

[<span data-ttu-id="79dff-126">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="79dff-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)