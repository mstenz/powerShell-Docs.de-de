---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „Service“
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953047"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="3a013-103">DSC-Ressource „Service“</span><span class="sxs-lookup"><span data-stu-id="3a013-103">DSC Service Resource</span></span>

> <span data-ttu-id="3a013-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="3a013-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="3a013-105">Die Ressource **Service** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Diensten auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="3a013-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3a013-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a013-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="3a013-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="3a013-107">Properties</span></span>

|<span data-ttu-id="3a013-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3a013-108">Property</span></span> |<span data-ttu-id="3a013-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="3a013-109">Description</span></span> |
|---|---|
|<span data-ttu-id="3a013-110">Name</span><span class="sxs-lookup"><span data-stu-id="3a013-110">Name</span></span> |<span data-ttu-id="3a013-111">Gibt den Namen des Diensts an.</span><span class="sxs-lookup"><span data-stu-id="3a013-111">Indicates the service name.</span></span> <span data-ttu-id="3a013-112">Beachten Sie, dass sich dieser mitunter vom Anzeigenamen unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="3a013-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="3a013-113">Mit dem Cmdlet `Get-Service` können Sie eine Liste der Dienste und ihren aktuellen Status abrufen.</span><span class="sxs-lookup"><span data-stu-id="3a013-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="3a013-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="3a013-114">BuiltInAccount</span></span> |<span data-ttu-id="3a013-115">Gibt das zu verwendende Anmeldekonto für den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="3a013-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="3a013-116">Die für diese Eigenschaft zulässigen Werte sind: **LocalService**, **LocalSystem** und **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="3a013-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="3a013-117">Anmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="3a013-117">Credential</span></span> |<span data-ttu-id="3a013-118">Gibt die Anmeldeinformationen für das Konto an, unter dem der Dienst ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3a013-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="3a013-119">Diese Eigenschaft und die **BuiltinAccount**-Eigenschaft können nicht zusammen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3a013-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="3a013-120">StartupType</span><span class="sxs-lookup"><span data-stu-id="3a013-120">StartupType</span></span> |<span data-ttu-id="3a013-121">Gibt den Starttyp für den Dienst an.</span><span class="sxs-lookup"><span data-stu-id="3a013-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="3a013-122">Die für diese Eigenschaft zulässigen Werte sind: **Automatic**, **Disabled** und **Manual**.</span><span class="sxs-lookup"><span data-stu-id="3a013-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="3a013-123">State</span><span class="sxs-lookup"><span data-stu-id="3a013-123">State</span></span> |<span data-ttu-id="3a013-124">Gibt den Status an, den Sie für den Dienst sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="3a013-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="3a013-125">Die Werte sind: **Running** oder **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="3a013-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="3a013-126">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="3a013-126">Description</span></span> |<span data-ttu-id="3a013-127">Gibt die Beschreibung des Zieldiensts an.</span><span class="sxs-lookup"><span data-stu-id="3a013-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="3a013-128">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3a013-128">DisplayName</span></span> |<span data-ttu-id="3a013-129">Gibt den Anzeigenamen des Zieldiensts an.</span><span class="sxs-lookup"><span data-stu-id="3a013-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="3a013-130">`Path`</span><span class="sxs-lookup"><span data-stu-id="3a013-130">Path</span></span> |<span data-ttu-id="3a013-131">Gibt den Pfad zur Binärdatei eines neuen Diensts an.</span><span class="sxs-lookup"><span data-stu-id="3a013-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="3a013-132">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="3a013-132">Common properties</span></span>

|<span data-ttu-id="3a013-133">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3a013-133">Property</span></span> |<span data-ttu-id="3a013-134">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="3a013-134">Description</span></span> |
|---|---|
|<span data-ttu-id="3a013-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3a013-135">DependsOn</span></span> |<span data-ttu-id="3a013-136">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="3a013-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3a013-137">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3a013-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="3a013-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="3a013-138">Ensure</span></span> |<span data-ttu-id="3a013-139">Gibt an, ob der Zieldienst auf dem System vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3a013-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="3a013-140">Legen Sie diese Eigenschaft auf **Absent** fest, um sicherzustellen, dass der Zieldienst nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3a013-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="3a013-141">Das Festlegen auf **Present** stellt sicher, dass der Zieldienst vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="3a013-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="3a013-142">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="3a013-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="3a013-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="3a013-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="3a013-144">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="3a013-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="3a013-145">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="3a013-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="3a013-146">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="3a013-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="3a013-147">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3a013-147">Example</span></span>

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