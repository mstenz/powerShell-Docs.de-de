---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f7f5e-103">ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f7f5e-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f7f5e-104">Ruft direkt die **Test**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="f7f5e-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="f7f5e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7f5e-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="f7f5e-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="f7f5e-106">Parameters</span></span>
----------

<span data-ttu-id="f7f5e-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f7f5e-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="f7f5e-108">Der Name der aufzurufenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="f7f5e-108">The name of the resource to call.</span></span>

<span data-ttu-id="f7f5e-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f7f5e-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="f7f5e-110">Der Name des Moduls, das die aufzurufende Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="f7f5e-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f7f5e-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f7f5e-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="f7f5e-112">Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an.</span><span class="sxs-lookup"><span data-stu-id="f7f5e-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f7f5e-113">Verwenden Sie das Cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) zum Ermitteln von Ressourceneigenschaften und deren Typen.</span><span class="sxs-lookup"><span data-stu-id="f7f5e-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f7f5e-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="f7f5e-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="f7f5e-115">Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn sich der Zielknoten im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="f7f5e-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="f7f5e-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f7f5e-116">Return value</span></span>
------------

<span data-ttu-id="f7f5e-117">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="f7f5e-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7f5e-118">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f7f5e-118">Remarks</span></span>

<span data-ttu-id="f7f5e-119">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="f7f5e-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f7f5e-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f7f5e-120">Requirements</span></span>
------------
><span data-ttu-id="f7f5e-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f7f5e-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f7f5e-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7f5e-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f7f5e-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f7f5e-123">See also</span></span>


[<span data-ttu-id="f7f5e-124">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="f7f5e-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



