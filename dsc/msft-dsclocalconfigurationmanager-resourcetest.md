---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b42b4-103">ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="b42b4-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b42b4-104">Ruft direkt die **Test**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="b42b4-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="b42b4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b42b4-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="b42b4-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="b42b4-106">Parameters</span></span>
----------

<span data-ttu-id="b42b4-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b42b4-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="b42b4-108">Der Name der aufzurufenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="b42b4-108">The name of the resource to call.</span></span>

<span data-ttu-id="b42b4-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b42b4-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="b42b4-110">Der Name des Moduls, das die aufzurufende Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="b42b4-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b42b4-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b42b4-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="b42b4-112">Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an.</span><span class="sxs-lookup"><span data-stu-id="b42b4-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b42b4-113">Verwenden Sie das Cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) zum Ermitteln von Ressourceneigenschaften und deren Typen.</span><span class="sxs-lookup"><span data-stu-id="b42b4-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b42b4-114">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="b42b4-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="b42b4-115">Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn sich der Zielknoten im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="b42b4-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="b42b4-116">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b42b4-116">Return value</span></span>
------------

<span data-ttu-id="b42b4-117">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="b42b4-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b42b4-118">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b42b4-118">Remarks</span></span>

<span data-ttu-id="b42b4-119">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="b42b4-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b42b4-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b42b4-120">Requirements</span></span>
------------
><span data-ttu-id="b42b4-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b42b4-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b42b4-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b42b4-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b42b4-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b42b4-123">See also</span></span>


[<span data-ttu-id="b42b4-124">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="b42b4-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



