---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC für Linux-Resource „nxGroup“
ms.openlocfilehash: 3682cb728d314d00b4a64a93b93018e8a6d12a21
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560847"
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="4c694-103">DSC für Linux-Resource „nxGroup“</span><span class="sxs-lookup"><span data-stu-id="4c694-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="4c694-104">Die Ressource **nxGroup** in PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Gruppen auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="4c694-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c694-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c694-105">Syntax</span></span>

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a><span data-ttu-id="4c694-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="4c694-106">Properties</span></span>

|<span data-ttu-id="4c694-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="4c694-107">Property</span></span> |<span data-ttu-id="4c694-108">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="4c694-108">Description</span></span> |
|---|---|
|<span data-ttu-id="4c694-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="4c694-109">GroupName</span></span> |<span data-ttu-id="4c694-110">Gibt den Namen der Gruppe an, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="4c694-110">Specifies the name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="4c694-111">Members</span><span class="sxs-lookup"><span data-stu-id="4c694-111">Members</span></span> |<span data-ttu-id="4c694-112">Gibt die Mitglieder an, die die Gruppe bilden.</span><span class="sxs-lookup"><span data-stu-id="4c694-112">Specifies the members that form the group.</span></span> |
|<span data-ttu-id="4c694-113">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="4c694-113">MembersToInclude</span></span> |<span data-ttu-id="4c694-114">Gibt die Benutzer an, die Mitglied dieser Gruppe werden sollen.</span><span class="sxs-lookup"><span data-stu-id="4c694-114">Specifies the users who you want to ensure are members of the group.</span></span> |
|<span data-ttu-id="4c694-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="4c694-115">MembersToExclude</span></span> |<span data-ttu-id="4c694-116">Gibt die Benutzer an, die nicht Mitglied dieser Gruppe werden sollen.</span><span class="sxs-lookup"><span data-stu-id="4c694-116">Specifies the users who you want to ensure are not members of the group.</span></span> |
|<span data-ttu-id="4c694-117">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="4c694-117">PreferredGroupID</span></span> |<span data-ttu-id="4c694-118">Legt nach Möglichkeit die Gruppen-ID auf den angegebenen Wert fest.</span><span class="sxs-lookup"><span data-stu-id="4c694-118">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="4c694-119">Wenn die Gruppen-ID derzeit verwendet wird, wird die nächste verfügbare Gruppen-ID verwendet.</span><span class="sxs-lookup"><span data-stu-id="4c694-119">If the group id is currently in use, the next available group id is used.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4c694-120">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="4c694-120">Common properties</span></span>

|<span data-ttu-id="4c694-121">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="4c694-121">Property</span></span> |<span data-ttu-id="4c694-122">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="4c694-122">Description</span></span> |
|---|---|
|<span data-ttu-id="4c694-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4c694-123">DependsOn</span></span> |<span data-ttu-id="4c694-124">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="4c694-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4c694-125">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4c694-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4c694-126">Ensure</span><span class="sxs-lookup"><span data-stu-id="4c694-126">Ensure</span></span> |<span data-ttu-id="4c694-127">Bestimmt, ob das Vorhandensein der Gruppe geprüft werden soll.</span><span class="sxs-lookup"><span data-stu-id="4c694-127">Determines whether to check if the group exists.</span></span> <span data-ttu-id="4c694-128">Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass die Gruppe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="4c694-128">Set this property to **Present** to ensure the group exists.</span></span> <span data-ttu-id="4c694-129">Legen Sie sie auf **Absent** fest, um sicherzustellen, dass die Gruppe nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="4c694-129">Set it to **Absent** to ensure the group does not exist.</span></span> <span data-ttu-id="4c694-130">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="4c694-130">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="4c694-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="4c694-131">Example</span></span>

<span data-ttu-id="4c694-132">Im folgenden Beispiel wird sichergestellt, dass der Benutzer „monuser“ vorhanden und Mitglied der Gruppe „DBusers“ ist.</span><span class="sxs-lookup"><span data-stu-id="4c694-132">The following example ensures that the user 'monuser' exists and is a member of the group 'DBusers'.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```
