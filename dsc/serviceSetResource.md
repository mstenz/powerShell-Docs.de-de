---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „ServiceSet“"
ms.openlocfilehash: 2488dda5212ccb717f7fd5d59ad62ec135ad13d5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="fec71-103">DSC-Ressource „ServiceSet“</span><span class="sxs-lookup"><span data-stu-id="fec71-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="fec71-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fec71-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="fec71-105">Die Ressource **ServiceSet** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Diensten auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="fec71-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="fec71-106">Diese Ressource ist eine [zusammengesetzte Ressource](authoringResourceComposite.md), die die Ressource [Service](serviceResource.md) für jeden Dienst aufruft, der in der `Name`-Eigenschaft angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="fec71-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="fec71-107">Verwenden Sie diese Ressource, wenn Sie verschiedene Dienste mit demselben Status konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="fec71-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="fec71-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="fec71-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="fec71-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="fec71-109">Properties</span></span>

|  <span data-ttu-id="fec71-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="fec71-110">Property</span></span>  |  <span data-ttu-id="fec71-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="fec71-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="fec71-112">Name</span><span class="sxs-lookup"><span data-stu-id="fec71-112">Name</span></span>| <span data-ttu-id="fec71-113">Gibt den Namen des Diensts an.</span><span class="sxs-lookup"><span data-stu-id="fec71-113">Indicates the service names.</span></span> <span data-ttu-id="fec71-114">Beachten Sie, dass sich dieser mitunter vom Anzeigenamen unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="fec71-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="fec71-115">Mit dem Cmdlet [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) können Sie eine Liste der Dienste und ihren aktuellen Status abrufen.</span><span class="sxs-lookup"><span data-stu-id="fec71-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="fec71-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="fec71-116">StartupType</span></span>| <span data-ttu-id="fec71-117">Gibt den Starttyp für den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="fec71-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="fec71-118">Die für diese Eigenschaft zulässigen Werte sind **Automatic**, **Disabled** und **Manual**.</span><span class="sxs-lookup"><span data-stu-id="fec71-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|  
| <span data-ttu-id="fec71-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="fec71-119">BuiltInAccount</span></span>| <span data-ttu-id="fec71-120">Gibt das zu verwendende Anmeldekonto für den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="fec71-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="fec71-121">Die für diese Eigenschaft zulässigen Werte sind **LocalService**, **LocalSystem** und **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="fec71-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>| 
| <span data-ttu-id="fec71-122">Status</span><span class="sxs-lookup"><span data-stu-id="fec71-122">State</span></span>| <span data-ttu-id="fec71-123">Gibt den Status an, den Sie für den Dienst sicherstellen möchten: **Stopped** oder **Running**.</span><span class="sxs-lookup"><span data-stu-id="fec71-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>| 
| <span data-ttu-id="fec71-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="fec71-124">Ensure</span></span>| <span data-ttu-id="fec71-125">Gibt an, ob die Dienste auf dem System vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="fec71-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="fec71-126">Legen Sie diese Eigenschaft auf **Absent** fest, um sicherzustellen, dass die Dienste nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="fec71-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="fec71-127">Das Festlegen auf **Present** (den Standardwert) stellt sicher, dass Zieldienste vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="fec71-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="fec71-128">Credential</span><span class="sxs-lookup"><span data-stu-id="fec71-128">Credential</span></span>| <span data-ttu-id="fec71-129">Gibt die Anmeldeinformationen für das Konto an, unter dem die Dienstressource ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="fec71-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="fec71-130">Diese Eigenschaft und die **BuiltinAccount**-Eigenschaft können nicht zusammen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="fec71-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>| 
| <span data-ttu-id="fec71-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fec71-131">DependsOn</span></span>| <span data-ttu-id="fec71-132">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="fec71-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fec71-133">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, *ResourceName* und dessen Typ *ResourceType* ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fec71-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 



## <a name="example"></a><span data-ttu-id="fec71-134">Beispiel</span><span class="sxs-lookup"><span data-stu-id="fec71-134">Example</span></span>

<span data-ttu-id="fec71-135">Die folgende Konfiguration startet die Dienste „Windows-Audio“ und „Remotedesktopdienste“.</span><span class="sxs-lookup"><span data-stu-id="fec71-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

