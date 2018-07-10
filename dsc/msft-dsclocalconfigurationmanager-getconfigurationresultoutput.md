---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893942"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bda3f-103">GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="bda3f-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bda3f-104">Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.</span><span class="sxs-lookup"><span data-stu-id="bda3f-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="bda3f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bda3f-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="bda3f-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="bda3f-106">Parameters</span></span>

<span data-ttu-id="bda3f-107">*jobId* \[in\] Die ID des Auftrags, für den Ausgabedaten abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bda3f-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="bda3f-108">*resumeOutputBookmark* \[in\] Gibt an, dass die Ausgabe eine Fortsetzung eines vorherigen Lesezeichens sein soll.</span><span class="sxs-lookup"><span data-stu-id="bda3f-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="bda3f-109">*output* \[out\] Die Ausgabe für den angegebenen Auftrag.</span><span class="sxs-lookup"><span data-stu-id="bda3f-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="bda3f-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="bda3f-110">Return value</span></span>

<span data-ttu-id="bda3f-111">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="bda3f-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bda3f-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bda3f-112">Remarks</span></span>

<span data-ttu-id="bda3f-113">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="bda3f-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bda3f-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="bda3f-114">Requirements</span></span>

<span data-ttu-id="bda3f-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bda3f-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bda3f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bda3f-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bda3f-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bda3f-117">See also</span></span>

[<span data-ttu-id="bda3f-118">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="bda3f-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)