---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="eafde-103">SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="eafde-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="eafde-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.</span><span class="sxs-lookup"><span data-stu-id="eafde-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="eafde-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="eafde-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="eafde-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="eafde-106">Parameters</span></span>
----------

<span data-ttu-id="eafde-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="eafde-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="eafde-108">Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="eafde-108">The environment data for the configuration.</span></span>

<span data-ttu-id="eafde-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="eafde-109">*force* \[in\]</span></span>  
<span data-ttu-id="eafde-110">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="eafde-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="eafde-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="eafde-111">Return value</span></span>
------------

<span data-ttu-id="eafde-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="eafde-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="eafde-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="eafde-113">Remarks</span></span>

<span data-ttu-id="eafde-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="eafde-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="eafde-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="eafde-115">Requirements</span></span>
------------
><span data-ttu-id="eafde-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="eafde-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="eafde-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="eafde-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="eafde-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="eafde-118">See also</span></span>


[<span data-ttu-id="eafde-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="eafde-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



