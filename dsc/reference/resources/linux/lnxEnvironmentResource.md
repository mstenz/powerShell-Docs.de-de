---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxEnvironment“
ms.openlocfilehash: 763ec560faa6adaf42aef3c21c9045be95f780bc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078009"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="763e2-103">DSC für Linux-Resource „nxEnvironment“</span><span class="sxs-lookup"><span data-stu-id="763e2-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="763e2-104">Die Ressource **nxEnvironment** in PowerShell DSC (Desired State Configuration) bietet einen Mechanismus zum Verwalten von Systemumgebungsvariablen auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="763e2-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="763e2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="763e2-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="763e2-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="763e2-106">Properties</span></span>

|  <span data-ttu-id="763e2-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="763e2-107">Property</span></span> |  <span data-ttu-id="763e2-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="763e2-108">Description</span></span> |
|---|---|
| <span data-ttu-id="763e2-109">Name</span><span class="sxs-lookup"><span data-stu-id="763e2-109">Name</span></span>| <span data-ttu-id="763e2-110">Gibt den Namen der Umgebungsvariablen an, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="763e2-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="763e2-111">Wert</span><span class="sxs-lookup"><span data-stu-id="763e2-111">Value</span></span>| <span data-ttu-id="763e2-112">Der Wert, der der Umgebungsvariablen zugewiesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="763e2-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="763e2-113">Ensure</span><span class="sxs-lookup"><span data-stu-id="763e2-113">Ensure</span></span>| <span data-ttu-id="763e2-114">Bestimmt, ob das Vorhandensein der Variablen geprüft werden soll.</span><span class="sxs-lookup"><span data-stu-id="763e2-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="763e2-115">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass die Variable vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="763e2-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="763e2-116">Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass die Variable nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="763e2-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="763e2-117">Der Standardwert ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="763e2-117">The default value is "Present".</span></span>|
| <span data-ttu-id="763e2-118">Pfad</span><span class="sxs-lookup"><span data-stu-id="763e2-118">Path</span></span>| <span data-ttu-id="763e2-119">Definiert die Umgebungsvariable, die konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="763e2-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="763e2-120">Legen Sie diese Eigenschaft auf **$true** fest, wenn die Variable die **Path**-Variable ist. Legen Sie sie andernfalls auf **$false** fest.</span><span class="sxs-lookup"><span data-stu-id="763e2-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="763e2-121">Der Standardwert ist **$false**.</span><span class="sxs-lookup"><span data-stu-id="763e2-121">The default is **$false**.</span></span> <span data-ttu-id="763e2-122">Wenn die konfigurierte Variable die **Path**-Variable ist, wird der von der **Value**-Eigenschaft bereitgestellte Wert an den vorhandenen Wert angefügt.</span><span class="sxs-lookup"><span data-stu-id="763e2-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="763e2-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="763e2-123">DependsOn</span></span> | <span data-ttu-id="763e2-124">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="763e2-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="763e2-125">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="763e2-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="763e2-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="763e2-126">Additional Information</span></span>

* <span data-ttu-id="763e2-127">Wenn **Path** fehlt oder auf **$false** festgelegt ist, werden Umgebungsvariablen in `/etc/environment` verwaltet.</span><span class="sxs-lookup"><span data-stu-id="763e2-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="763e2-128">Ihre Programme oder Skripts erfordern möglicherweise das Konfigurieren des Abrufs der Datei `/etc/environment` für den Zugriff auf die verwalteten Umgebungsvariablen.</span><span class="sxs-lookup"><span data-stu-id="763e2-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="763e2-129">Wenn **Path** auf **$true** festgelegt ist, wird die Umgebungsvariable in der Datei `/etc/profile.d/DSCenvironment.sh` verwaltet.</span><span class="sxs-lookup"><span data-stu-id="763e2-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="763e2-130">Diese Datei wird erstellt, falls sie nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="763e2-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="763e2-131">Wenn **Ensure** auf „Absent“ und **Path** auf **$true** festgelegt ist, wird eine vorhandene Umgebungsvariable nur aus `/etc/profile.d/DSCenvironment.sh` und nicht aus anderen Dateien entfernt.</span><span class="sxs-lookup"><span data-stu-id="763e2-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="763e2-132">Beispiel</span><span class="sxs-lookup"><span data-stu-id="763e2-132">Example</span></span>

<span data-ttu-id="763e2-133">Das folgende Beispiel veranschaulicht das Verwenden der Ressource **nxEnvironment** zum Sicherstellen, dass **TestEnvironmentVariable** vorhanden ist und den Wert „Test-Value“ hat.</span><span class="sxs-lookup"><span data-stu-id="763e2-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="763e2-134">Wenn **TestEnvironmentVariable** nicht vorhanden ist, wird die Variable erstellt.</span><span class="sxs-lookup"><span data-stu-id="763e2-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```