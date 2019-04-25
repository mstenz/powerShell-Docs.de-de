---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Resource „Environment“
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077533"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="2a389-103">DSC-Resource „Environment“</span><span class="sxs-lookup"><span data-stu-id="2a389-103">DSC Environment Resource</span></span>

> <span data-ttu-id="2a389-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2a389-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2a389-105">Die Ressource __Environment__ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Systemumgebungsvariablen.</span><span class="sxs-lookup"><span data-stu-id="2a389-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a389-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a389-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="2a389-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="2a389-107">Properties</span></span>

|  <span data-ttu-id="2a389-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2a389-108">Property</span></span>  |  <span data-ttu-id="2a389-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2a389-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="2a389-110">Name</span><span class="sxs-lookup"><span data-stu-id="2a389-110">Name</span></span>| <span data-ttu-id="2a389-111">Gibt den Namen der Umgebungsvariablen an, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="2a389-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="2a389-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="2a389-112">Ensure</span></span>| <span data-ttu-id="2a389-113">Gibt an, ob eine Variable vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2a389-113">Indicates if a variable exists.</span></span> <span data-ttu-id="2a389-114">Legen Sie diese Eigenschaft auf __Present__ fest, um die Umgebungsvariable zu erstellen, falls sie noch nicht vorhanden ist, oder um sicherzustellen, dass ihr Wert der Angabe durch die __Value__-Eigenschaft entspricht, wenn die Variable bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2a389-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="2a389-115">Legen Sie sie auf __Absent__ fest, um die Variable zu löschen, falls sie vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2a389-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="2a389-116">Pfad</span><span class="sxs-lookup"><span data-stu-id="2a389-116">Path</span></span>| <span data-ttu-id="2a389-117">Definiert die Umgebungsvariable, die konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="2a389-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="2a389-118">Legen Sie diese Eigenschaft auf __$true__ fest, wenn die Variable die __Path__-Variable ist. Legen Sie sie andernfalls auf __$false__ fest.</span><span class="sxs-lookup"><span data-stu-id="2a389-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="2a389-119">Der Standardwert ist __$false__.</span><span class="sxs-lookup"><span data-stu-id="2a389-119">The default is __$false__.</span></span> <span data-ttu-id="2a389-120">Wenn die konfigurierte Variable die __Path__-Variable ist, wird der von der __Value__-Eigenschaft bereitgestellte Wert an den vorhandenen Wert angefügt.</span><span class="sxs-lookup"><span data-stu-id="2a389-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="2a389-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2a389-121">DependsOn</span></span> | <span data-ttu-id="2a389-122">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="2a389-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2a389-123">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2a389-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="2a389-124">Wert</span><span class="sxs-lookup"><span data-stu-id="2a389-124">Value</span></span>| <span data-ttu-id="2a389-125">Der Wert, der der Umgebungsvariablen zugewiesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="2a389-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="2a389-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2a389-126">Example</span></span>

<span data-ttu-id="2a389-127">Im folgende Beispiel wird sichergestellt, dass __TestEnvironmentVariable__ vorhanden ist und den Wert __TestValue__ hat.</span><span class="sxs-lookup"><span data-stu-id="2a389-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="2a389-128">Falls sie nicht vorhanden ist, wird sie erstellt.</span><span class="sxs-lookup"><span data-stu-id="2a389-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```