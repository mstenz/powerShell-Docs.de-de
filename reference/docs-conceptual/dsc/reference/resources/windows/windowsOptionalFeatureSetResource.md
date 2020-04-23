---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „WindowsOptionalFeatureSet“
ms.openlocfilehash: f378006a6c362ee9890d70dd76fb552dd262a544
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71952867"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="77f53-103">DSC-Ressource „WindowsOptionalFeatureSet“</span><span class="sxs-lookup"><span data-stu-id="77f53-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="77f53-104">Gilt für: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="77f53-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="77f53-105">Die Ressource **WindowsOptionalFeatureSet** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass optionale Features auf einem Zielknoten aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="77f53-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="77f53-106">Diese Ressource ist eine [zusammengesetzte Ressource](../../../resources/authoringResourceComposite.md), die die Ressource [WindowsOptionalFeature](windowsOptionalFeatureResource.md) für jedes Feature aufruft, das in der **Name**-Eigenschaft angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="77f53-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="77f53-107">Verwenden Sie diese Ressource, wenn Sie verschiedene optionale Windows-Features mit demselben Status konfigurieren möchten.</span><span class="sxs-lookup"><span data-stu-id="77f53-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="77f53-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="77f53-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="77f53-109">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="77f53-109">Properties</span></span>

|<span data-ttu-id="77f53-110">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="77f53-110">Property</span></span> |<span data-ttu-id="77f53-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="77f53-111">Description</span></span> |
|---|---|
|<span data-ttu-id="77f53-112">Name</span><span class="sxs-lookup"><span data-stu-id="77f53-112">Name</span></span> |<span data-ttu-id="77f53-113">Gibt den Namen der Features an, die aktiviert oder deaktiviert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="77f53-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="77f53-114">`Source`</span><span class="sxs-lookup"><span data-stu-id="77f53-114">Source</span></span> |<span data-ttu-id="77f53-115">Nicht implementiert.</span><span class="sxs-lookup"><span data-stu-id="77f53-115">Not implemented.</span></span> |
|<span data-ttu-id="77f53-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="77f53-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="77f53-117">Gibt an, ob Windows Update (WU) von DISM kontaktiert wird, wenn die Quelldateien zum Aktivieren von Features gesucht werden.</span><span class="sxs-lookup"><span data-stu-id="77f53-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="77f53-118">Falls `$true`, wird WU nicht von DISM kontaktiert.</span><span class="sxs-lookup"><span data-stu-id="77f53-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="77f53-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="77f53-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="77f53-120">Legen Sie diese Einstellung auf `$true` fest, um alle zu den Features gehörigen Dateien zu entfernen, wenn **Ensure** auf **Absent** festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="77f53-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="77f53-121">LogLevel</span><span class="sxs-lookup"><span data-stu-id="77f53-121">LogLevel</span></span> |<span data-ttu-id="77f53-122">Die maximale Ausgabeebene, die in den Protokollen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="77f53-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="77f53-123">Zulässige Werte: **ErrorsOnly**, **ErrorsAndWarning** und **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="77f53-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="77f53-124">LogPath</span><span class="sxs-lookup"><span data-stu-id="77f53-124">LogPath</span></span> |<span data-ttu-id="77f53-125">Der Pfad zu einer Protokolldatei, in der der Ressourcenanbieter den Vorgang protokollieren soll.</span><span class="sxs-lookup"><span data-stu-id="77f53-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="77f53-126">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="77f53-126">Common properties</span></span>

|<span data-ttu-id="77f53-127">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="77f53-127">Property</span></span> |<span data-ttu-id="77f53-128">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="77f53-128">Description</span></span> |
|---|---|
|<span data-ttu-id="77f53-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="77f53-129">DependsOn</span></span> |<span data-ttu-id="77f53-130">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="77f53-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="77f53-131">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="77f53-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="77f53-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="77f53-132">Ensure</span></span> |<span data-ttu-id="77f53-133">Gibt an, ob die Features aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="77f53-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="77f53-134">Um sicherzustellen, dass die Features aktiviert sind, legen Sie diese Eigenschaft auf **Enable** fest.</span><span class="sxs-lookup"><span data-stu-id="77f53-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="77f53-135">Um sicherzustellen, dass die Features deaktiviert sind, legen Sie die Eigenschaft auf **Disable** fest.</span><span class="sxs-lookup"><span data-stu-id="77f53-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="77f53-136">Der Standardwert ist **Enable**.</span><span class="sxs-lookup"><span data-stu-id="77f53-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="77f53-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="77f53-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="77f53-138">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="77f53-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="77f53-139">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="77f53-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="77f53-140">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="77f53-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>