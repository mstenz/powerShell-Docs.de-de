---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: TestConfiguration-Methode
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954867"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="1cfe2-103">TestConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="1cfe2-103">TestConfiguration method</span></span>

<span data-ttu-id="1cfe2-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und überprüft die aktuelle Konfiguration anhand dieses Dokuments.</span><span class="sxs-lookup"><span data-stu-id="1cfe2-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="1cfe2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1cfe2-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="1cfe2-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="1cfe2-106">Parameters</span></span>

<span data-ttu-id="1cfe2-107">*configurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="1cfe2-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="1cfe2-108">*InDesiredState* \[out\] Gibt bei der Rückgabe an, ob sich der verwaltete Knoten im vom Konfigurationsdokument angegebenen Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="1cfe2-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="1cfe2-109">*ResourcesInDesiredState* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceInDesiredState**-Klasse, die Ressourcen angibt, die sich im gewünschten Zustand befinden.</span><span class="sxs-lookup"><span data-stu-id="1cfe2-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="1cfe2-110">*ResourcesNotInDesiredState* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceNotInDesiredState**-Klasse, die Ressourcen angibt, die sich nicht im gewünschten Zustand befinden.</span><span class="sxs-lookup"><span data-stu-id="1cfe2-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="1cfe2-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1cfe2-111">Return value</span></span>

<span data-ttu-id="1cfe2-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="1cfe2-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1cfe2-113">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1cfe2-113">Remarks</span></span>

<span data-ttu-id="1cfe2-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="1cfe2-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1cfe2-115">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="1cfe2-115">Requirements</span></span>

<span data-ttu-id="1cfe2-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1cfe2-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1cfe2-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1cfe2-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1cfe2-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1cfe2-118">See also</span></span>

[<span data-ttu-id="1cfe2-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="1cfe2-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
