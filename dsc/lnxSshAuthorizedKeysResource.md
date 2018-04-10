---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Ressource „nxSshAuthorizedKeys“
ms.openlocfilehash: a36d158735839727e98893ce9fce174a0f37f764
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="4d70b-103">DSC für Linux-Ressource „nxSshAuthorizedKeys“</span><span class="sxs-lookup"><span data-stu-id="4d70b-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="4d70b-104">Die Ressource **nxAuthorizedKeys** in PowerShell DSC bietet ein Mechanismus zum Verwalten autorisierter SSH-Schlüssel für einen angegebenen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="4d70b-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d70b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4d70b-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="4d70b-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="4d70b-106">Properties</span></span>

|  <span data-ttu-id="4d70b-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="4d70b-107">Property</span></span> |  <span data-ttu-id="4d70b-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4d70b-108">Description</span></span> |
|---|---|
| <span data-ttu-id="4d70b-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="4d70b-109">KeyComment</span></span>| <span data-ttu-id="4d70b-110">Ein eindeutiger Kommentar für den Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="4d70b-110">A unique comment for the key.</span></span> <span data-ttu-id="4d70b-111">Dieser wird verwendet, um Schlüssel eindeutig zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="4d70b-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="4d70b-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="4d70b-112">Ensure</span></span>| <span data-ttu-id="4d70b-113">Gibt an, ob der Schlüssel definiert ist.</span><span class="sxs-lookup"><span data-stu-id="4d70b-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="4d70b-114">Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass der Schlüssel nicht in der Datei mit den autorisierten Schlüsseln des Benutzers vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="4d70b-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="4d70b-115">Legen Sie sie auf „Present“ fest, um sicherzustellen, dass der Schlüssel in der autorisierten Schlüsseldatei des Benutzers definiert ist.</span><span class="sxs-lookup"><span data-stu-id="4d70b-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="4d70b-116">Username</span><span class="sxs-lookup"><span data-stu-id="4d70b-116">Username</span></span>| <span data-ttu-id="4d70b-117">Der Benutzername, für den die autorisierten SSH-Schlüssel verwaltet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="4d70b-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="4d70b-118">Falls nicht definiert, ist der Standardbenutzer „root“.</span><span class="sxs-lookup"><span data-stu-id="4d70b-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="4d70b-119">Key</span><span class="sxs-lookup"><span data-stu-id="4d70b-119">Key</span></span>| <span data-ttu-id="4d70b-120">Der Inhalt des Schlüssels.</span><span class="sxs-lookup"><span data-stu-id="4d70b-120">The contents of the key.</span></span> <span data-ttu-id="4d70b-121">Ist erforderlich, wenn **Ensure** auf „Present“ festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="4d70b-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="4d70b-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4d70b-122">DependsOn</span></span> | <span data-ttu-id="4d70b-123">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="4d70b-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4d70b-124">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4d70b-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="4d70b-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4d70b-125">Example</span></span>

<span data-ttu-id="4d70b-126">Das folgende Beispiel definiert einen öffentlichen autorisierten SSH-Schlüssel für den Benutzer „monuser“.</span><span class="sxs-lookup"><span data-stu-id="4d70b-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```