---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC für Linux-Resource „nxGroup“
ms.openlocfilehash: 750b7c38a38fb8a7781585a3a7776f832ee62495
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a><span data-ttu-id="891e4-103">DSC für Linux-Resource „nxGroup“</span><span class="sxs-lookup"><span data-stu-id="891e4-103">DSC for Linux nxGroup Resource</span></span>

<span data-ttu-id="891e4-104">Die Ressource **nxGroup** in PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Gruppen auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="891e4-104">The **nxGroup** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="891e4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="891e4-105">Syntax</span></span>

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a><span data-ttu-id="891e4-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="891e4-106">Properties</span></span>

|  <span data-ttu-id="891e4-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="891e4-107">Property</span></span> |  <span data-ttu-id="891e4-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="891e4-108">Description</span></span> |
|---|---|
| <span data-ttu-id="891e4-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="891e4-109">GroupName</span></span>| <span data-ttu-id="891e4-110">Gibt den Namen der Gruppe an, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="891e4-110">Specifies the name of the group for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="891e4-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="891e4-111">Ensure</span></span>| <span data-ttu-id="891e4-112">Bestimmt, ob das Vorhandensein der Gruppe geprüft werden soll.</span><span class="sxs-lookup"><span data-stu-id="891e4-112">Determines whether to check if the group exists.</span></span> <span data-ttu-id="891e4-113">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass die Gruppe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="891e4-113">Set this property to "Present" to ensure the group exists.</span></span> <span data-ttu-id="891e4-114">Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass die Gruppe nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="891e4-114">Set it to "Absent" to ensure the group does not exist.</span></span> <span data-ttu-id="891e4-115">Der Standardwert ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="891e4-115">The default value is "Present".</span></span>|
| <span data-ttu-id="891e4-116">Members</span><span class="sxs-lookup"><span data-stu-id="891e4-116">Members</span></span>| <span data-ttu-id="891e4-117">Gibt die Mitglieder an, die die Gruppe bilden.</span><span class="sxs-lookup"><span data-stu-id="891e4-117">Specifies the members that form the group.</span></span>|
| <span data-ttu-id="891e4-118">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="891e4-118">MembersToInclude</span></span>| <span data-ttu-id="891e4-119">Gibt die Benutzer an, die Mitglied dieser Gruppe werden sollen.</span><span class="sxs-lookup"><span data-stu-id="891e4-119">Specifies the users who you want to ensure are members of the group.</span></span>|
| <span data-ttu-id="891e4-120">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="891e4-120">MembersToExclude</span></span>| <span data-ttu-id="891e4-121">Gibt die Benutzer an, die nicht Mitglied dieser Gruppe werden sollen.</span><span class="sxs-lookup"><span data-stu-id="891e4-121">Specifies the users who you want to ensure are not members of the group.</span></span>|
| <span data-ttu-id="891e4-122">PreferredGroupID</span><span class="sxs-lookup"><span data-stu-id="891e4-122">PreferredGroupID</span></span>| <span data-ttu-id="891e4-123">Legt nach Möglichkeit die Gruppen-ID auf den angegebenen Wert fest.</span><span class="sxs-lookup"><span data-stu-id="891e4-123">Sets the group id to the provided value if possible.</span></span> <span data-ttu-id="891e4-124">Wenn die Gruppen-ID derzeit verwendet wird, wird die nächste verfügbare Gruppen-ID verwendet.</span><span class="sxs-lookup"><span data-stu-id="891e4-124">If the group id is currently in use, the next available group id is used.</span></span>|
| <span data-ttu-id="891e4-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="891e4-125">DependsOn</span></span> | <span data-ttu-id="891e4-126">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="891e4-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="891e4-127">Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="891e4-127">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="891e4-128">Beispiel</span><span class="sxs-lookup"><span data-stu-id="891e4-128">Example</span></span>

<span data-ttu-id="891e4-129">Im folgenden Beispiel wird sichergestellt, dass der Benutzer „monuser“ vorhanden und Mitglied der Gruppe „DBusers“ ist.</span><span class="sxs-lookup"><span data-stu-id="891e4-129">The following example ensures that the user “monuser” exists and is a member of the group "DBusers".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}

nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"
}
}
```