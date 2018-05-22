---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
description: Stellt einen Mechanismus zum Verwalten lokaler Gruppen auf dem Zielknoten zur Verfügung.
title: DSC-Ressource „GroupSet“
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-groupset-resource"></a><span data-ttu-id="a2be3-104">DSC-Ressource „GroupSet“</span><span class="sxs-lookup"><span data-stu-id="a2be3-104">DSC GroupSet Resource</span></span>

> <span data-ttu-id="a2be3-105">Gilt für: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a2be3-105">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="a2be3-106">Die Ressource **GroupSet** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Gruppen auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="a2be3-106">The **GroupSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span> <span data-ttu-id="a2be3-107">Diese Ressource ist eine [zusammengesetzte Ressource](authoringResourceComposite.md), die die Ressource [Group](groupResource.md) für jede Gruppe aufruft, die im `GroupName`-Parameter angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="a2be3-107">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Group resource](groupResource.md) for each group specified in the `GroupName` parameter.</span></span>

<span data-ttu-id="a2be3-108">Verwenden Sie diese Ressource, wenn Sie dieselbe Liste von Mitgliedern mehreren Gruppen hinzufügen oder aus diesen entfernen möchten, mehr als eine Gruppe entfernen möchten oder mehr als eine Gruppe mit derselben Liste von Mitgliedern hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="a2be3-108">Use this resource when you want to add and/or remove the same list of members to more than one group, remove more than one group, or add more than one group with the same list of members.</span></span>

##<a name="syntax"></a><span data-ttu-id="a2be3-109">Syntax##</span><span class="sxs-lookup"><span data-stu-id="a2be3-109">Syntax##</span></span>
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

## <a name="properties"></a><span data-ttu-id="a2be3-110">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="a2be3-110">Properties</span></span>

|  <span data-ttu-id="a2be3-111">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a2be3-111">Property</span></span>  |  <span data-ttu-id="a2be3-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a2be3-112">Description</span></span>   |
|---|---|
| <span data-ttu-id="a2be3-113">GroupName</span><span class="sxs-lookup"><span data-stu-id="a2be3-113">GroupName</span></span>| <span data-ttu-id="a2be3-114">Die Namen der Gruppen, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="a2be3-114">The names of the groups for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="a2be3-115">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="a2be3-115">MembersToExclude</span></span>| <span data-ttu-id="a2be3-116">Verwenden Sie diese Eigenschaft, um Mitglieder aus der vorhandenen Gruppenmitgliedschaft zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="a2be3-116">Use this property to remove members from the existing membership of the groups.</span></span> <span data-ttu-id="a2be3-117">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="a2be3-117">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="a2be3-118">Wenn Sie diese Eigenschaft in einer Konfiguration festgelegt haben, verwenden Sie die Eigenschaft **Members** nicht.</span><span class="sxs-lookup"><span data-stu-id="a2be3-118">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="a2be3-119">Andernfalls wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="a2be3-119">Doing so will generate an error.</span></span>|
| <span data-ttu-id="a2be3-120">Credential</span><span class="sxs-lookup"><span data-stu-id="a2be3-120">Credential</span></span>| <span data-ttu-id="a2be3-121">Die Anmeldeinformationen für den Zugriff auf Remoteressourcen.</span><span class="sxs-lookup"><span data-stu-id="a2be3-121">The credentials required to access remote resources.</span></span> <span data-ttu-id="a2be3-122">**Hinweis**: Dieses Konto muss die entsprechenden Active Directory-Berechtigungen aufweisen, um alle nicht lokalen Konten zur Gruppe hinzuzufügen. Andernfalls tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="a2be3-122">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error will occur.</span></span>
| <span data-ttu-id="a2be3-123">Ensure</span><span class="sxs-lookup"><span data-stu-id="a2be3-123">Ensure</span></span>| <span data-ttu-id="a2be3-124">Gibt an, ob die Gruppen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="a2be3-124">Indicates whether the groups exist.</span></span> <span data-ttu-id="a2be3-125">Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass die Gruppen nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="a2be3-125">Set this property to "Absent" to ensure that the groups do not exist.</span></span> <span data-ttu-id="a2be3-126">Das Festlegen auf „Present“ (den Standardwert) stellt sicher, dass die Gruppen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="a2be3-126">Setting it to "Present" (the default value) ensures that the groups exist.</span></span>|
| <span data-ttu-id="a2be3-127">Members</span><span class="sxs-lookup"><span data-stu-id="a2be3-127">Members</span></span>| <span data-ttu-id="a2be3-128">Verwenden Sie diese Eigenschaft, um die aktuelle Gruppenmitgliedschaft durch die angegebenen Member zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="a2be3-128">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="a2be3-129">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="a2be3-129">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="a2be3-130">Wenn Sie diese Eigenschaft in einer Konfiguration festlegen, verwenden Sie weder die Eigenschaft **MembersToExclude** noch die Eigenschaft **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="a2be3-130">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="a2be3-131">Andernfalls wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="a2be3-131">Doing so will generate an error.</span></span>|
| <span data-ttu-id="a2be3-132">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="a2be3-132">MembersToInclude</span></span>| <span data-ttu-id="a2be3-133">Verwenden Sie diese Eigenschaft, um Member zur vorhandenen Gruppenmitgliedschaft hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a2be3-133">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="a2be3-134">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="a2be3-134">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="a2be3-135">Wenn Sie diese Eigenschaft in einer Konfiguration festgelegt haben, verwenden Sie die Eigenschaft **Members** nicht.</span><span class="sxs-lookup"><span data-stu-id="a2be3-135">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="a2be3-136">Andernfalls wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="a2be3-136">Doing so will generate an error.</span></span>|
| <span data-ttu-id="a2be3-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="a2be3-137">DependsOn</span></span> | <span data-ttu-id="a2be3-138">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="a2be3-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="a2be3-139">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.</span><span class="sxs-lookup"><span data-stu-id="a2be3-139">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example-1"></a><span data-ttu-id="a2be3-140">Beispiel 1</span><span class="sxs-lookup"><span data-stu-id="a2be3-140">Example 1</span></span>

<span data-ttu-id="a2be3-141">Im folgenden Beispiel wird gezeigt, wie Sie sicherstellen, dass die beiden Gruppen „myGroup“ und „myOtherGroup“ vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="a2be3-141">The following example shows how to ensure that two groups called "myGroup" and "myOtherGroup" are present.</span></span>

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

><span data-ttu-id="a2be3-142">**Hinweis:** In diesem Beispiel werden der Einfachheit halber unverschlüsselte Anmeldeinformationen verwendet.</span><span class="sxs-lookup"><span data-stu-id="a2be3-142">**Note:** This example uses plaintext credentials for simplicity.</span></span> <span data-ttu-id="a2be3-143">Informationen zum Verschlüsseln von Anmeldeinformationen in der MOF-Konfigurationsdatei finden Sie unter [Schützen der MOF-Datei](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="a2be3-143">For information about how to encrypt credentials in the configuration MOF file, see [Securing the MOF File](secureMOF.md).</span></span>