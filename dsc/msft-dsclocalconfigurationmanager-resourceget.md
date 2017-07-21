---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="23470-103">ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="23470-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="23470-104">Ruft direkt die **Get**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="23470-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="23470-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="23470-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="23470-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="23470-106">Parameters</span></span>
----------

<span data-ttu-id="23470-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="23470-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="23470-108">Der Name der aufzurufenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="23470-108">The name of the resource to call.</span></span>

<span data-ttu-id="23470-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="23470-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="23470-110">Der Name des Moduls, das die aufzurufende Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="23470-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="23470-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="23470-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="23470-112">Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an.</span><span class="sxs-lookup"><span data-stu-id="23470-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="23470-113">Verwenden Sie das Cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) zum Ermitteln von Ressourceneigenschaften und deren Typen.</span><span class="sxs-lookup"><span data-stu-id="23470-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="23470-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="23470-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="23470-115">Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="23470-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="23470-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="23470-116">Return value</span></span>
------------

<span data-ttu-id="23470-117">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="23470-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="23470-118">Hinweise</span><span class="sxs-lookup"><span data-stu-id="23470-118">Remarks</span></span>

<span data-ttu-id="23470-119">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="23470-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="23470-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="23470-120">Requirements</span></span>
------------
><span data-ttu-id="23470-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="23470-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="23470-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="23470-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="23470-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="23470-123">See also</span></span>


[<span data-ttu-id="23470-124">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="23470-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



