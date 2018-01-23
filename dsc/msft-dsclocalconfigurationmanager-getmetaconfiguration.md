---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 695be4ee6490567295fda0cc44635870362d24b8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5bcd4-103">GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="5bcd4-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5bcd4-104">Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5bcd4-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="5bcd4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5bcd4-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="5bcd4-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="5bcd4-106">Parameters</span></span>
----------

<span data-ttu-id="5bcd4-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5bcd4-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="5bcd4-108">Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCMetaConfiguration**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="5bcd4-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="5bcd4-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5bcd4-109">Return value</span></span>
------------

<span data-ttu-id="5bcd4-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="5bcd4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5bcd4-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5bcd4-111">Remarks</span></span>

<span data-ttu-id="5bcd4-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="5bcd4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5bcd4-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5bcd4-113">Requirements</span></span>
------------
><span data-ttu-id="5bcd4-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5bcd4-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5bcd4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5bcd4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5bcd4-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5bcd4-116">See also</span></span>


[<span data-ttu-id="5bcd4-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="5bcd4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



