---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Ressource „nxSshAuthorizedKeys“
ms.openlocfilehash: 6e008efcbff2e679650d0bc3d5b8b573f6ef83e0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953257"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="ed655-103">DSC für Linux-Ressource „nxSshAuthorizedKeys“</span><span class="sxs-lookup"><span data-stu-id="ed655-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="ed655-104">Die Ressource **nxAuthorizedKeys** in PowerShell DSC bietet ein Mechanismus zum Verwalten autorisierter SSH-Schlüssel für einen angegebenen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ed655-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed655-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ed655-105">Syntax</span></span>

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="ed655-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ed655-106">Properties</span></span>

|<span data-ttu-id="ed655-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ed655-107">Property</span></span> |<span data-ttu-id="ed655-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ed655-108">Description</span></span> |
|---|---|
|<span data-ttu-id="ed655-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="ed655-109">KeyComment</span></span> |<span data-ttu-id="ed655-110">Ein eindeutiger Kommentar für den Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="ed655-110">A unique comment for the key.</span></span> <span data-ttu-id="ed655-111">Dieser wird verwendet, um Schlüssel eindeutig zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="ed655-111">This is used to uniquely identify keys.</span></span> |
|<span data-ttu-id="ed655-112">Username</span><span class="sxs-lookup"><span data-stu-id="ed655-112">Username</span></span> |<span data-ttu-id="ed655-113">Der Benutzername, für den die autorisierten SSH-Schlüssel verwaltet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ed655-113">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="ed655-114">Falls nicht definiert, ist der Standardbenutzer **root**.</span><span class="sxs-lookup"><span data-stu-id="ed655-114">If not defined, the default user is **root**.</span></span> |
|<span data-ttu-id="ed655-115">Key</span><span class="sxs-lookup"><span data-stu-id="ed655-115">Key</span></span> |<span data-ttu-id="ed655-116">Der Inhalt des Schlüssels.</span><span class="sxs-lookup"><span data-stu-id="ed655-116">The contents of the key.</span></span> <span data-ttu-id="ed655-117">Ist erforderlich, wenn **Ensure** auf **Present** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="ed655-117">This is required if **Ensure** is set to **Present**.</span></span>|

## <a name="common-properties"></a><span data-ttu-id="ed655-118">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="ed655-118">Common properties</span></span>

|<span data-ttu-id="ed655-119">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="ed655-119">Property</span></span> |<span data-ttu-id="ed655-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ed655-120">Description</span></span> |
|---|---|
|<span data-ttu-id="ed655-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ed655-121">DependsOn</span></span> |<span data-ttu-id="ed655-122">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="ed655-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ed655-123">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ed655-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ed655-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="ed655-124">Ensure</span></span> |<span data-ttu-id="ed655-125">Gibt an, ob der Schlüssel definiert ist.</span><span class="sxs-lookup"><span data-stu-id="ed655-125">Specifies whether the key is defined.</span></span> <span data-ttu-id="ed655-126">Legen Sie diese Eigenschaft auf **Absent** fest, um sicherzustellen, dass der Schlüssel nicht in der Datei mit den autorisierten Schlüsseln des Benutzers vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="ed655-126">Set this property to **Absent** to ensure the key does not exist in the user's authorized keys file.</span></span> <span data-ttu-id="ed655-127">Legen Sie sie auf **Present** fest, um sicherzustellen, dass der Schlüssel in der autorisierten Schlüsseldatei des Benutzers definiert ist.</span><span class="sxs-lookup"><span data-stu-id="ed655-127">Set it to **Present** to ensure the key is defined in the user's authorized key file.</span></span> |

## <a name="example"></a><span data-ttu-id="ed655-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ed655-128">Example</span></span>

<span data-ttu-id="ed655-129">Das folgende Beispiel definiert einen öffentlichen autorisierten SSH-Schlüssel für den Benutzer „monuser“.</span><span class="sxs-lookup"><span data-stu-id="ed655-129">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```