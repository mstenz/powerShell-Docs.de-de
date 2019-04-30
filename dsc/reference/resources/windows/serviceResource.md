---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Service“
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076893"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="a02d9-103">DSC-Ressource „Service“</span><span class="sxs-lookup"><span data-stu-id="a02d9-103">DSC Service Resource</span></span>

> <span data-ttu-id="a02d9-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a02d9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="a02d9-105">Die Ressource **Service** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Diensten auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="a02d9-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="a02d9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a02d9-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="a02d9-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a02d9-107">Properties</span></span>

|  <span data-ttu-id="a02d9-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a02d9-108">Property</span></span>  |  <span data-ttu-id="a02d9-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a02d9-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="a02d9-110">Name</span><span class="sxs-lookup"><span data-stu-id="a02d9-110">Name</span></span>| <span data-ttu-id="a02d9-111">Gibt den Namen des Diensts an.</span><span class="sxs-lookup"><span data-stu-id="a02d9-111">Indicates the service name.</span></span> <span data-ttu-id="a02d9-112">Beachten Sie, dass sich dieser mitunter vom Anzeigenamen unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="a02d9-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="a02d9-113">Mit dem Cmdlet „Get-Service“ können Sie eine Liste der Dienste und ihren aktuellen Status abrufen.</span><span class="sxs-lookup"><span data-stu-id="a02d9-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="a02d9-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="a02d9-114">BuiltInAccount</span></span>| <span data-ttu-id="a02d9-115">Gibt das zu verwendende Anmeldekonto für den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="a02d9-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="a02d9-116">Die für diese Eigenschaft zulässigen Werte sind: **LocalService**, **LocalSystem** und **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="a02d9-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="a02d9-117">Credential</span><span class="sxs-lookup"><span data-stu-id="a02d9-117">Credential</span></span>| <span data-ttu-id="a02d9-118">Gibt die Anmeldeinformationen für das Konto an, unter dem der Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a02d9-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="a02d9-119">Diese Eigenschaft und die __BuiltinAccount__-Eigenschaft können nicht zusammen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a02d9-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="a02d9-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a02d9-120">DependsOn</span></span>| <span data-ttu-id="a02d9-121">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="a02d9-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a02d9-122">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="a02d9-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="a02d9-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="a02d9-123">StartupType</span></span>| <span data-ttu-id="a02d9-124">Gibt den Starttyp für den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="a02d9-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="a02d9-125">Die für diese Eigenschaft zulässigen Werte sind: **Automatic**, **Disabled** und **Manual**.</span><span class="sxs-lookup"><span data-stu-id="a02d9-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="a02d9-126">Status</span><span class="sxs-lookup"><span data-stu-id="a02d9-126">State</span></span>| <span data-ttu-id="a02d9-127">Gibt den Status an, den Sie für den Dienst sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="a02d9-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="a02d9-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a02d9-128">Description</span></span> | <span data-ttu-id="a02d9-129">Gibt die Beschreibung des Zieldiensts an.</span><span class="sxs-lookup"><span data-stu-id="a02d9-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="a02d9-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a02d9-130">DisplayName</span></span> | <span data-ttu-id="a02d9-131">Gibt den Anzeigenamen des Zieldiensts an.</span><span class="sxs-lookup"><span data-stu-id="a02d9-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="a02d9-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="a02d9-132">Ensure</span></span> | <span data-ttu-id="a02d9-133">Gibt an, ob der Zieldienst auf dem System vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a02d9-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="a02d9-134">Legen Sie diese Eigenschaft auf **Absent** fest, um sicherzustellen, dass der Zieldienst nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a02d9-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="a02d9-135">Das Festlegen auf **Present** (den Standardwert) stellt sicher, dass der Zieldienst vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="a02d9-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="a02d9-136">Pfad</span><span class="sxs-lookup"><span data-stu-id="a02d9-136">Path</span></span> | <span data-ttu-id="a02d9-137">Gibt den Pfad zur Binärdatei eines neuen Diensts an.</span><span class="sxs-lookup"><span data-stu-id="a02d9-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="a02d9-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a02d9-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```