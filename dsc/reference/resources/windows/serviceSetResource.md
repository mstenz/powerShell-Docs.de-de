---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „ServiceSet“
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047267"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="e3cba-103">DSC-Ressource „ServiceSet“</span><span class="sxs-lookup"><span data-stu-id="e3cba-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="e3cba-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e3cba-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e3cba-105">Die Ressource **ServiceSet** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Diensten auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="e3cba-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="e3cba-106">Diese Ressource ist eine [zusammengesetzte Ressource](../../../resources/authoringResourceComposite.md), die die Ressource [Service](serviceResource.md) für jeden Dienst aufruft, der in der `Name`-Eigenschaft angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="e3cba-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="e3cba-107">Verwenden Sie diese Ressource, wenn Sie verschiedene Dienste mit demselben Status konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="e3cba-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3cba-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3cba-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="e3cba-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="e3cba-109">Properties</span></span>

|  <span data-ttu-id="e3cba-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e3cba-110">Property</span></span>  |  <span data-ttu-id="e3cba-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e3cba-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="e3cba-112">Name</span><span class="sxs-lookup"><span data-stu-id="e3cba-112">Name</span></span>| <span data-ttu-id="e3cba-113">Gibt den Namen des Diensts an.</span><span class="sxs-lookup"><span data-stu-id="e3cba-113">Indicates the service names.</span></span> <span data-ttu-id="e3cba-114">Beachten Sie, dass sich dieser mitunter vom Anzeigenamen unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="e3cba-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="e3cba-115">Mit dem Cmdlet [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) können Sie eine Liste der Dienste und ihren aktuellen Status abrufen.</span><span class="sxs-lookup"><span data-stu-id="e3cba-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="e3cba-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="e3cba-116">StartupType</span></span>| <span data-ttu-id="e3cba-117">Gibt den Starttyp für den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="e3cba-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="e3cba-118">Die für diese Eigenschaft zulässigen Werte lauten: **Automatische**, **deaktiviert**, und **manuell**</span><span class="sxs-lookup"><span data-stu-id="e3cba-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="e3cba-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="e3cba-119">BuiltInAccount</span></span>| <span data-ttu-id="e3cba-120">Gibt das zu verwendende Anmeldekonto für den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="e3cba-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="e3cba-121">Die für diese Eigenschaft zulässigen Werte lauten: **"LocalService"**, **"LocalSystem"**, und **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="e3cba-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="e3cba-122">Status</span><span class="sxs-lookup"><span data-stu-id="e3cba-122">State</span></span>| <span data-ttu-id="e3cba-123">Gibt den Status an, den Sie für den Dienst sicherstellen möchten. **Beendet** oder **ausführen**.</span><span class="sxs-lookup"><span data-stu-id="e3cba-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="e3cba-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="e3cba-124">Ensure</span></span>| <span data-ttu-id="e3cba-125">Gibt an, ob die Dienste auf dem System vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="e3cba-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="e3cba-126">Legen Sie diese Eigenschaft auf **Absent** fest, um sicherzustellen, dass die Dienste nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="e3cba-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="e3cba-127">Das Festlegen auf **Present** (den Standardwert) stellt sicher, dass Zieldienste vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="e3cba-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="e3cba-128">Credential</span><span class="sxs-lookup"><span data-stu-id="e3cba-128">Credential</span></span>| <span data-ttu-id="e3cba-129">Gibt die Anmeldeinformationen für das Konto an, unter dem die Dienstressource ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e3cba-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="e3cba-130">Diese Eigenschaft und die **BuiltinAccount**-Eigenschaft können nicht zusammen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e3cba-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="e3cba-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e3cba-131">DependsOn</span></span>| <span data-ttu-id="e3cba-132">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="e3cba-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e3cba-133">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, *ResourceName* und dessen Typ *ResourceType* ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e3cba-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="e3cba-134">Beispiel</span><span class="sxs-lookup"><span data-stu-id="e3cba-134">Example</span></span>

<span data-ttu-id="e3cba-135">Die folgende Konfiguration startet die Dienste „Windows-Audio“ und „Remotedesktopdienste“.</span><span class="sxs-lookup"><span data-stu-id="e3cba-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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
