---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
description: Stellt einen Mechanismus zum Verwalten lokaler Gruppen auf dem Zielknoten zur Verfügung.
title: DSC-Ressource „GroupSet“
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077176"
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="9abb2-104">DSC-Ressource „GroupSet“</span><span class="sxs-lookup"><span data-stu-id="9abb2-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="9abb2-105">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9abb2-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="9abb2-106">Die Ressource **GroupSet** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Gruppen auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="9abb2-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="9abb2-107">Diese Ressource ist eine [zusammengesetzte Ressource](../../../resources/authoringResourceComposite.md), die die Ressource [Group](groupResource.md) für jede Gruppe aufruft, die im `GroupName`-Parameter angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="9abb2-107">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="9abb2-108">Verwenden Sie diese Ressource, wenn Sie dieselbe Liste von Mitgliedern mehreren Gruppen hinzufügen oder aus diesen entfernen möchten, mehr als eine Gruppe entfernen möchten oder mehr als eine Gruppe mit derselben Liste von Mitgliedern hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="9abb2-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

## <a name="syntax"></a><span data-ttu-id="9abb2-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="9abb2-109">Syntax</span></span>

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="9abb2-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="9abb2-110">Properties</span></span>

|  <span data-ttu-id="9abb2-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9abb2-111">Property</span></span>  |  <span data-ttu-id="9abb2-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9abb2-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="9abb2-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="9abb2-113">GroupName</span></span>| <span data-ttu-id="9abb2-114">Die Namen der Gruppen, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="9abb2-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9abb2-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="9abb2-115">MembersToExclude</span></span>| <span data-ttu-id="9abb2-116">Verwenden Sie diese Eigenschaft, um Mitglieder aus der vorhandenen Gruppenmitgliedschaft zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="9abb2-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="9abb2-117">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="9abb2-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="9abb2-118">Wenn Sie diese Eigenschaft in einer Konfiguration festgelegt haben, verwenden Sie die Eigenschaft **Members** nicht.</span><span class="sxs-lookup"><span data-stu-id="9abb2-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="9abb2-119">Andernfalls wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="9abb2-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="9abb2-120">Credential</span><span class="sxs-lookup"><span data-stu-id="9abb2-120">Credential</span></span>| <span data-ttu-id="9abb2-121">Die Anmeldeinformationen für den Zugriff auf Remoteressourcen.</span><span class="sxs-lookup"><span data-stu-id="9abb2-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="9abb2-122">**Hinweis**: Dieses Konto muss die entsprechenden Active Directory-Berechtigungen aufweisen, um alle nicht lokalen Konten zur Gruppe hinzuzufügen. Andernfalls tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="9abb2-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="9abb2-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="9abb2-123">Ensure</span></span>| <span data-ttu-id="9abb2-124">Gibt an, ob die Gruppen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="9abb2-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="9abb2-125">Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass die Gruppen nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="9abb2-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="9abb2-126">Das Festlegen auf „Present“ (den Standardwert) stellt sicher, dass die Gruppen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="9abb2-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="9abb2-127">Members</span><span class="sxs-lookup"><span data-stu-id="9abb2-127">Members</span></span>| <span data-ttu-id="9abb2-128">Verwenden Sie diese Eigenschaft, um die aktuelle Gruppenmitgliedschaft durch die angegebenen Member zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="9abb2-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="9abb2-129">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="9abb2-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="9abb2-130">Wenn Sie diese Eigenschaft in einer Konfiguration festlegen, verwenden Sie weder die Eigenschaft **MembersToExclude** noch die Eigenschaft **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="9abb2-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="9abb2-131">Andernfalls wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="9abb2-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="9abb2-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="9abb2-132">MembersToInclude</span></span>| <span data-ttu-id="9abb2-133">Verwenden Sie diese Eigenschaft, um Member zur vorhandenen Gruppenmitgliedschaft hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9abb2-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="9abb2-134">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="9abb2-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="9abb2-135">Wenn Sie diese Eigenschaft in einer Konfiguration festgelegt haben, verwenden Sie die Eigenschaft **Members** nicht.</span><span class="sxs-lookup"><span data-stu-id="9abb2-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="9abb2-136">Andernfalls wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="9abb2-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="9abb2-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9abb2-137">DependsOn</span></span> | <span data-ttu-id="9abb2-138">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="9abb2-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9abb2-139">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.</span><span class="sxs-lookup"><span data-stu-id="9abb2-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1-ensuring-groups-are-present"></a><span data-ttu-id="9abb2-140">Beispiel 1: Sicherstellen, dass Gruppen vorhanden sind</span><span class="sxs-lookup"><span data-stu-id="9abb2-140">Example 1: Ensuring Groups are present</span></span>

<span data-ttu-id="9abb2-141">Im folgenden Beispiel wird gezeigt, wie Sie sicherstellen, dass die beiden Gruppen „myGroup“ und „myOtherGroup“ vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="9abb2-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="9abb2-142">In diesem Beispiel werden der Einfachheit halber unverschlüsselte Anmeldeinformationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="9abb2-142">This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="9abb2-143">Informationen zum Verschlüsseln von Anmeldeinformationen in der MOF-Konfigurationsdatei finden Sie unter [Schützen der MOF-Datei](../../../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="9abb2-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](../../../pull-server/secureMOF.md).</span></span>
