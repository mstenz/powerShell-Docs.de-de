---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9209e-103">ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="9209e-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9209e-104">Ruft direkt die **Get**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="9209e-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="9209e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9209e-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="9209e-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="9209e-106">Parameters</span></span>
----------

<span data-ttu-id="9209e-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9209e-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="9209e-108">Der Name der aufzurufenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="9209e-108">The name of the resource to call.</span></span>

<span data-ttu-id="9209e-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9209e-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="9209e-110">Der Name des Moduls, das die aufzurufende Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="9209e-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="9209e-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9209e-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="9209e-112">Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an.</span><span class="sxs-lookup"><span data-stu-id="9209e-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="9209e-113">Verwenden Sie das Cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) zum Ermitteln von Ressourceneigenschaften und deren Typen.</span><span class="sxs-lookup"><span data-stu-id="9209e-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="9209e-114">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="9209e-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="9209e-115">Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9209e-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="9209e-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="9209e-116">Return value</span></span>
------------

<span data-ttu-id="9209e-117">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="9209e-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9209e-118">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9209e-118">Remarks</span></span>

<span data-ttu-id="9209e-119">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="9209e-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9209e-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9209e-120">Requirements</span></span>
------------
><span data-ttu-id="9209e-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9209e-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9209e-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9209e-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9209e-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9209e-123">See also</span></span>


[<span data-ttu-id="9209e-124">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="9209e-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



