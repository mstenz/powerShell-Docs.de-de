---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „WindowsFeatureSet“
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952957"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="61707-103">DSC-Ressource „WindowsFeatureSet“</span><span class="sxs-lookup"><span data-stu-id="61707-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="61707-104">Gilt für: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="61707-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="61707-105">Die Ressource **WindowsFeatureSet** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass Rollen und Features einem Zielknoten hinzugefügt oder von diesem entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="61707-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="61707-106">Diese Ressource ist eine [zusammengesetzte Ressource](../../../resources/authoringResourceComposite.md), die die Ressource [WindowsFeature](windowsfeatureResource.md) für jedes Feature aufruft, das in der **Name**-Eigenschaft angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="61707-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="61707-107">Verwenden Sie diese Ressource, wenn Sie verschiedene Windows-Features mit demselben Status konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="61707-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="61707-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="61707-108">Syntax</span></span>

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="61707-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="61707-109">Properties</span></span>

|  <span data-ttu-id="61707-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="61707-110">Property</span></span>  |  <span data-ttu-id="61707-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="61707-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="61707-112">Name</span><span class="sxs-lookup"><span data-stu-id="61707-112">Name</span></span> |<span data-ttu-id="61707-113">Die Namen der Rollen oder Features an, die hinzugefügt oder entfernt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="61707-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="61707-114">Dies ist identisch mit der **Name**-Eigenschaft des Cmdlets [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) und nicht mit dem Anzeigenamen der Rollen oder Features.</span><span class="sxs-lookup"><span data-stu-id="61707-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="61707-115">Source</span><span class="sxs-lookup"><span data-stu-id="61707-115">Source</span></span> |<span data-ttu-id="61707-116">Gibt bei Bedarf den Speicherort der Quelldatei an, die für die Installation verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="61707-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="61707-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="61707-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="61707-118">Legen Sie diese Eigenschaft auf `$true` fest, um alle erforderlichen Teilfeatures in die Features einzubeziehen, die Sie mit der **Name**-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="61707-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="61707-119">Credential</span><span class="sxs-lookup"><span data-stu-id="61707-119">Credential</span></span> |<span data-ttu-id="61707-120">Die Anmeldeinformationen zum Hinzufügen oder Entfernen der Rollen oder Features.</span><span class="sxs-lookup"><span data-stu-id="61707-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="61707-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="61707-121">LogPath</span></span> |<span data-ttu-id="61707-122">Der Pfad zu einer Protokolldatei, in der der Ressourcenanbieter den Vorgang protokollieren soll.</span><span class="sxs-lookup"><span data-stu-id="61707-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="61707-123">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="61707-123">Common properties</span></span>

|<span data-ttu-id="61707-124">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="61707-124">Property</span></span> |<span data-ttu-id="61707-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="61707-125">Description</span></span> |
|---|---|
|<span data-ttu-id="61707-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="61707-126">DependsOn</span></span> |<span data-ttu-id="61707-127">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="61707-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="61707-128">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="61707-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="61707-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="61707-129">Ensure</span></span> |<span data-ttu-id="61707-130">Gibt an, ob die Rollen oder Features hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="61707-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="61707-131">Um sicherzustellen, dass die Rollen oder Features hinzugefügt werden, legen Sie diese Eigenschaft auf **Present** fest.</span><span class="sxs-lookup"><span data-stu-id="61707-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="61707-132">Um sicherzustellen, dass die Rollen oder Features entfernt werden, legen Sie diese Eigenschaft auf **Absent** fest.</span><span class="sxs-lookup"><span data-stu-id="61707-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="61707-133">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="61707-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="61707-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="61707-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="61707-135">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="61707-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="61707-136">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="61707-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="61707-137">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="61707-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="61707-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="61707-138">Example</span></span>

<span data-ttu-id="61707-139">Mit der folgenden Konfiguration wird sichergestellt, dass die Features **Webserver** (IIS) und **SMTP-Server** sowie alle Teilfeatures installiert werden.</span><span class="sxs-lookup"><span data-stu-id="61707-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```