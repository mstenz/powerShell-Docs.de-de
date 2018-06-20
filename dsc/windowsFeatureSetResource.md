---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „WindowsFeatureSet“
ms.openlocfilehash: 582f9b1f439056118680f6f814d2c202d0e823be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186727"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="70973-103">DSC-Ressource „WindowsFeatureSet“</span><span class="sxs-lookup"><span data-stu-id="70973-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="70973-104">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="70973-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="70973-105">Die Ressource **WindowsFeatureSet** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass Rollen und Features einem Zielknoten hinzugefügt oder von diesem entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="70973-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="70973-106">Diese Ressource ist eine [zusammengesetzte Ressource](authoringResourceComposite.md), die die Ressource [WindowsFeature](windowsfeatureResource.md) für jedes Feature aufruft, das in der `Name`-Eigenschaft angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="70973-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="70973-107">Verwenden Sie diese Ressource, wenn Sie verschiedene Windows-Features mit demselben Status konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="70973-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="70973-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="70973-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="70973-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="70973-109">Properties</span></span>

|  <span data-ttu-id="70973-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="70973-110">Property</span></span>  |  <span data-ttu-id="70973-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="70973-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="70973-112">Name</span><span class="sxs-lookup"><span data-stu-id="70973-112">Name</span></span>| <span data-ttu-id="70973-113">Die Namen der Rollen oder Features an, die hinzugefügt oder entfernt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="70973-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="70973-114">Dies ist identisch mit der **Name**-Eigenschaft des Cmdlets [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) und nicht mit dem Anzeigenamen der Rollen oder Features.</span><span class="sxs-lookup"><span data-stu-id="70973-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="70973-115">Credential</span><span class="sxs-lookup"><span data-stu-id="70973-115">Credential</span></span>| <span data-ttu-id="70973-116">Die Anmeldeinformationen zum Hinzufügen oder Entfernen der Rollen oder Features.</span><span class="sxs-lookup"><span data-stu-id="70973-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="70973-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="70973-117">Ensure</span></span>| <span data-ttu-id="70973-118">Gibt an, ob die Rollen oder Features hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="70973-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="70973-119">Um sicherzustellen, dass die Rollen oder Features hinzugefügt werden, legen Sie diese Eigenschaft auf „Present“ fest. Um sicherzustellen, dass die Rollen oder Features entfernt werden, legen Sie diese Eigenschaft auf „Absent“ fest.</span><span class="sxs-lookup"><span data-stu-id="70973-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="70973-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="70973-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="70973-121">Legen Sie diese Eigenschaft auf **$true** fest, um alle erforderlichen Teilfeatures in die Features einzubeziehen, die Sie mit der **Name**-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="70973-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="70973-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="70973-122">LogPath</span></span>| <span data-ttu-id="70973-123">Der Pfad zu einer Protokolldatei, in der der Ressourcenanbieter den Vorgang protokollieren soll.</span><span class="sxs-lookup"><span data-stu-id="70973-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="70973-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="70973-124">DependsOn</span></span>| <span data-ttu-id="70973-125">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="70973-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="70973-126">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="70973-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="70973-127">Source</span><span class="sxs-lookup"><span data-stu-id="70973-127">Source</span></span>| <span data-ttu-id="70973-128">Gibt bei Bedarf den Speicherort der Quelldatei an, die für die Installation verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="70973-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="70973-129">Beispiel</span><span class="sxs-lookup"><span data-stu-id="70973-129">Example</span></span>

<span data-ttu-id="70973-130">Mit der folgenden Konfiguration wird sichergestellt, dass die Features **Webserver** (IIS) und **SMTP-Server** sowie alle Teilfeatures installiert werden.</span><span class="sxs-lookup"><span data-stu-id="70973-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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