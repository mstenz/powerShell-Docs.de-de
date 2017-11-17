---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „WindowsFeature“"
ms.openlocfilehash: a3433577a122f6c7e31360e094a089f6ceef77c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="80435-103">DSC-Ressource „WindowsFeature“</span><span class="sxs-lookup"><span data-stu-id="80435-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="80435-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="80435-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="80435-105">Die Ressource **WindowsFeature** in Windows PowerShell DSC (Desired State Configuration) bietet einen Mechanismus, um sicherzustellen, dass Rollen und Features einem Knoten hinzugefügt oder entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="80435-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="80435-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="80435-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="80435-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="80435-107">Properties</span></span>

|  <span data-ttu-id="80435-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="80435-108">Property</span></span>  |  <span data-ttu-id="80435-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="80435-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="80435-110">Name</span><span class="sxs-lookup"><span data-stu-id="80435-110">Name</span></span>| <span data-ttu-id="80435-111">Gibt den Namen der Rolle oder des Features an, die/das hinzugefügt oder entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="80435-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="80435-112">Dies ist identisch mit der __Name__-Eigenschaft aus dem Cmdlet [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) und nicht mit dem Anzeigenamen der Rolle oder des Features.</span><span class="sxs-lookup"><span data-stu-id="80435-112">This is the same as the __Name__ property from the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the role or feature.</span></span>| 
| <span data-ttu-id="80435-113">Credential</span><span class="sxs-lookup"><span data-stu-id="80435-113">Credential</span></span>| <span data-ttu-id="80435-114">Gibt die Anmeldeinformationen zum Hinzufügen oder Entfernen der Rolle oder des Features an.</span><span class="sxs-lookup"><span data-stu-id="80435-114">Indicates the credentials to use to add or remove the role or feature.</span></span>| 
| <span data-ttu-id="80435-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="80435-115">Ensure</span></span>| <span data-ttu-id="80435-116">Gibt an, ob die Rolle oder das Feature hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="80435-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="80435-117">Um sicherzustellen, dass die Rolle oder das Feature hinzugefügt wird, legen Sie diese Eigenschaft auf „Present“ fest. Um sicherzustellen, dass die Rolle oder das Feature entfernt wird, legen Sie diese Eigenschaft auf „Absent“ fest.</span><span class="sxs-lookup"><span data-stu-id="80435-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="80435-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="80435-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="80435-119">Legen Sie diese Eigenschaft auf __$true__ fest, um den Status aller erforderlichen Teilfeatures mit dem Status des Features sicherzustellen, das Sie mit der __Name__-Eigenschaft angeben.</span><span class="sxs-lookup"><span data-stu-id="80435-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>| 
| <span data-ttu-id="80435-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="80435-120">LogPath</span></span>| <span data-ttu-id="80435-121">Gibt den Pfad zu einer Protokolldatei an, in der der Ressourcenanbieter den Vorgang protokollieren soll.</span><span class="sxs-lookup"><span data-stu-id="80435-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="80435-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="80435-122">DependsOn</span></span>| <span data-ttu-id="80435-123">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="80435-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="80435-124">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="80435-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="80435-125">Source</span><span class="sxs-lookup"><span data-stu-id="80435-125">Source</span></span>| <span data-ttu-id="80435-126">Gibt bei Bedarf den Speicherort der Quelldatei an, die für die Installation verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="80435-126">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="80435-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="80435-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present" 
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature  
}
```

