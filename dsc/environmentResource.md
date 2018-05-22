---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Resource „Environment“
ms.openlocfilehash: 023ecf4cc2e3f553770d9c49a94b6e903e560b01
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="cec3a-103">DSC-Resource „Environment“</span><span class="sxs-lookup"><span data-stu-id="cec3a-103">DSC Environment Resource</span></span>

> <span data-ttu-id="cec3a-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cec3a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="cec3a-105">Die Ressource __Environment__ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Systemumgebungsvariablen.</span><span class="sxs-lookup"><span data-stu-id="cec3a-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="cec3a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cec3a-106">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="cec3a-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="cec3a-107">Properties</span></span>

|  <span data-ttu-id="cec3a-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="cec3a-108">Property</span></span>  |  <span data-ttu-id="cec3a-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="cec3a-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="cec3a-110">Name</span><span class="sxs-lookup"><span data-stu-id="cec3a-110">Name</span></span>| <span data-ttu-id="cec3a-111">Gibt den Namen der Umgebungsvariablen an, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="cec3a-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="cec3a-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="cec3a-112">Ensure</span></span>| <span data-ttu-id="cec3a-113">Gibt an, ob eine Variable vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="cec3a-113">Indicates if a variable exists.</span></span> <span data-ttu-id="cec3a-114">Legen Sie diese Eigenschaft auf __Present__ fest, um die Umgebungsvariable zu erstellen, falls sie noch nicht vorhanden ist, oder um sicherzustellen, dass ihr Wert der Angabe durch die __Value__-Eigenschaft entspricht, wenn die Variable bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="cec3a-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="cec3a-115">Legen Sie sie auf __Absent__ fest, um die Variable zu löschen, falls sie vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="cec3a-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="cec3a-116">Pfad</span><span class="sxs-lookup"><span data-stu-id="cec3a-116">Path</span></span>| <span data-ttu-id="cec3a-117">Definiert die Umgebungsvariable, die konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="cec3a-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="cec3a-118">Legen Sie diese Eigenschaft auf __$true__ fest, wenn die Variable die __Path__-Variable ist. Legen Sie sie andernfalls auf __$false__ fest.</span><span class="sxs-lookup"><span data-stu-id="cec3a-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="cec3a-119">Der Standardwert ist __$false__.</span><span class="sxs-lookup"><span data-stu-id="cec3a-119">The default is __$false__.</span></span> <span data-ttu-id="cec3a-120">Wenn die konfigurierte Variable die __Path__-Variable ist, wird der von der __Value__-Eigenschaft bereitgestellte Wert an den vorhandenen Wert angefügt.</span><span class="sxs-lookup"><span data-stu-id="cec3a-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="cec3a-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="cec3a-121">DependsOn</span></span> | <span data-ttu-id="cec3a-122">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="cec3a-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cec3a-123">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="cec3a-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="cec3a-124">Wert</span><span class="sxs-lookup"><span data-stu-id="cec3a-124">Value</span></span>| <span data-ttu-id="cec3a-125">Der Wert, der der Umgebungsvariablen zugewiesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="cec3a-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="cec3a-126">Beispiel</span><span class="sxs-lookup"><span data-stu-id="cec3a-126">Example</span></span>

<span data-ttu-id="cec3a-127">Im folgende Beispiel wird sichergestellt, dass __TestEnvironmentVariable__ vorhanden ist und den Wert __TestValue__ hat.</span><span class="sxs-lookup"><span data-stu-id="cec3a-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="cec3a-128">Falls sie nicht vorhanden ist, wird sie erstellt.</span><span class="sxs-lookup"><span data-stu-id="cec3a-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```