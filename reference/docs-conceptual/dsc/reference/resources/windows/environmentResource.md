---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC-Resource „Environment“
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954717"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="abfe7-103">DSC-Resource „Environment“</span><span class="sxs-lookup"><span data-stu-id="abfe7-103">DSC Environment Resource</span></span>

> <span data-ttu-id="abfe7-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="abfe7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="abfe7-105">Die Ressource **Environment** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Systemumgebungsvariablen.</span><span class="sxs-lookup"><span data-stu-id="abfe7-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="abfe7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="abfe7-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="abfe7-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="abfe7-107">Properties</span></span>

|<span data-ttu-id="abfe7-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="abfe7-108">Property</span></span> |<span data-ttu-id="abfe7-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="abfe7-109">Description</span></span> |
|---|---|
|<span data-ttu-id="abfe7-110">Name</span><span class="sxs-lookup"><span data-stu-id="abfe7-110">Name</span></span> |<span data-ttu-id="abfe7-111">Gibt den Namen der Umgebungsvariablen an, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="abfe7-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="abfe7-112">Pfad</span><span class="sxs-lookup"><span data-stu-id="abfe7-112">Path</span></span> |<span data-ttu-id="abfe7-113">Definiert die Umgebungsvariable, die konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="abfe7-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="abfe7-114">Legen Sie diese Eigenschaft auf `$true` fest, wenn die Variable die **Path**-Variable ist. Legen Sie sie andernfalls auf `$false` fest.</span><span class="sxs-lookup"><span data-stu-id="abfe7-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="abfe7-115">Der Standardwert ist `$false`.</span><span class="sxs-lookup"><span data-stu-id="abfe7-115">The default is `$false`.</span></span> <span data-ttu-id="abfe7-116">Wenn die konfigurierte Variable die **Path**-Variable ist, wird der von der **Value**-Eigenschaft bereitgestellte Wert an den vorhandenen Wert angefügt.</span><span class="sxs-lookup"><span data-stu-id="abfe7-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="abfe7-117">Wert</span><span class="sxs-lookup"><span data-stu-id="abfe7-117">Value</span></span> |<span data-ttu-id="abfe7-118">Der Wert, der der Umgebungsvariablen zugewiesen werden soll.</span><span class="sxs-lookup"><span data-stu-id="abfe7-118">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="abfe7-119">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="abfe7-119">Common properties</span></span>

|<span data-ttu-id="abfe7-120">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="abfe7-120">Property</span></span> |<span data-ttu-id="abfe7-121">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="abfe7-121">Description</span></span> |
|---|---|
|<span data-ttu-id="abfe7-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="abfe7-122">DependsOn</span></span> |<span data-ttu-id="abfe7-123">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="abfe7-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="abfe7-124">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="abfe7-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="abfe7-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="abfe7-125">Ensure</span></span> |<span data-ttu-id="abfe7-126">Gibt an, ob eine Variable vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="abfe7-126">Indicates if a variable exists.</span></span> <span data-ttu-id="abfe7-127">Legen Sie diese Eigenschaft auf **Present** fest, um die Umgebungsvariable zu erstellen, falls sie noch nicht vorhanden ist, oder um sicherzustellen, dass ihr Wert der Angabe durch die **Value**-Eigenschaft entspricht, wenn die Variable bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="abfe7-127">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="abfe7-128">Legen Sie sie auf **Absent** fest, um die Variable zu löschen, falls sie vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="abfe7-128">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="abfe7-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="abfe7-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="abfe7-130">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="abfe7-130">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="abfe7-131">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="abfe7-131">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="abfe7-132">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="abfe7-132">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="abfe7-133">Beispiel</span><span class="sxs-lookup"><span data-stu-id="abfe7-133">Example</span></span>

<span data-ttu-id="abfe7-134">Im folgende Beispiel wird sichergestellt, dass „TestEnvironmentVariable“ vorhanden ist und den Wert _TestValue_ hat.</span><span class="sxs-lookup"><span data-stu-id="abfe7-134">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="abfe7-135">Falls sie nicht vorhanden ist, wird sie erstellt.</span><span class="sxs-lookup"><span data-stu-id="abfe7-135">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```