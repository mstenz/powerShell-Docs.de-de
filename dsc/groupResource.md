---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „Group“"
ms.openlocfilehash: 6fb6c5f9593687d7204ff31fddd9bca978ed2707
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-group-resource"></a><span data-ttu-id="154ec-103">DSC-Ressource „Group“</span><span class="sxs-lookup"><span data-stu-id="154ec-103">DSC Group Resource</span></span>

> <span data-ttu-id="154ec-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="154ec-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="154ec-105">Die Ressource „Group“ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Gruppen auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="154ec-105">The Group resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="154ec-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="154ec-106">Syntax</span></span>
```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="154ec-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="154ec-107">Properties</span></span>

|  <span data-ttu-id="154ec-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="154ec-108">Property</span></span>  |  <span data-ttu-id="154ec-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="154ec-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="154ec-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="154ec-110">GroupName</span></span>| <span data-ttu-id="154ec-111">Der Name der Gruppe, für die Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="154ec-111">The name of the group for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="154ec-112">Credential</span><span class="sxs-lookup"><span data-stu-id="154ec-112">Credential</span></span>| <span data-ttu-id="154ec-113">Die Anmeldeinformationen für den Zugriff auf Remoteressourcen.</span><span class="sxs-lookup"><span data-stu-id="154ec-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="154ec-114">**Hinweis**: Dieses Konto muss die entsprechenden Active Directory-Berechtigungen aufweisen, um alle nicht lokalen Konten zur Gruppe hinzuzufügen. Andernfalls tritt ein Fehler auf, wenn die Konfiguration auf dem Zielknoten ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="154ec-114">**Note**: This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>  
| <span data-ttu-id="154ec-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="154ec-115">Description</span></span>| <span data-ttu-id="154ec-116">Die Beschreibung der Gruppe.</span><span class="sxs-lookup"><span data-stu-id="154ec-116">The description of the group.</span></span>| 
| <span data-ttu-id="154ec-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="154ec-117">Ensure</span></span>| <span data-ttu-id="154ec-118">Gibt an, ob die Gruppe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="154ec-118">Indicates if the group exists.</span></span> <span data-ttu-id="154ec-119">Legen Sie diese Eigenschaft auf „Absent“ fest, um sicherzustellen, dass die Gruppe nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="154ec-119">Set this property to "Absent" to ensure that the group does not exist.</span></span> <span data-ttu-id="154ec-120">Das Festlegen auf „Present“ (den Standardwert) stellt sicher, dass die Gruppe vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="154ec-120">Setting it to "Present" (the default value) ensures that the group exists.</span></span>| 
| <span data-ttu-id="154ec-121">Mitglieder</span><span class="sxs-lookup"><span data-stu-id="154ec-121">Members</span></span>| <span data-ttu-id="154ec-122">Verwenden Sie diese Eigenschaft, um die aktuelle Gruppenmitgliedschaft durch die angegebenen Member zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="154ec-122">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="154ec-123">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="154ec-123">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="154ec-124">Wenn Sie diese Eigenschaft in einer Konfiguration festlegen, verwenden Sie weder die Eigenschaft **MembersToExclude** noch die Eigenschaft **MembersToInclude**.</span><span class="sxs-lookup"><span data-stu-id="154ec-124">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="154ec-125">Andernfalls kommt es zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="154ec-125">Doing so generates an error.</span></span>| 
| <span data-ttu-id="154ec-126">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="154ec-126">MembersToExclude</span></span>| <span data-ttu-id="154ec-127">Verwenden Sie diese Eigenschaft, um Member aus der vorhandenen Gruppenmitgliedschaft zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="154ec-127">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="154ec-128">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="154ec-128">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="154ec-129">Wenn Sie diese Eigenschaft in einer Konfiguration festgelegt haben, verwenden Sie die Eigenschaft **Members** nicht.</span><span class="sxs-lookup"><span data-stu-id="154ec-129">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="154ec-130">Andernfalls kommt es zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="154ec-130">Doing so generates an error.</span></span>| 
| <span data-ttu-id="154ec-131">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="154ec-131">MembersToInclude</span></span>| <span data-ttu-id="154ec-132">Verwenden Sie diese Eigenschaft, um Member zur vorhandenen Gruppenmitgliedschaft hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="154ec-132">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="154ec-133">Der Wert dieser Eigenschaft ist ein Zeichenfolgenarray im Format *Domäne*\\*Benutzername*.</span><span class="sxs-lookup"><span data-stu-id="154ec-133">The value of this property is an array of strings of the form *Domain*\\*UserName*.</span></span> <span data-ttu-id="154ec-134">Wenn Sie diese Eigenschaft in einer Konfiguration festgelegt haben, verwenden Sie die Eigenschaft **Members** nicht.</span><span class="sxs-lookup"><span data-stu-id="154ec-134">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="154ec-135">Andernfalls wird ein Fehler generiert.</span><span class="sxs-lookup"><span data-stu-id="154ec-135">Doing so will generate an error.</span></span>| 
| <span data-ttu-id="154ec-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="154ec-136">DependsOn</span></span> | <span data-ttu-id="154ec-137">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="154ec-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="154ec-138">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft „DependsOn = „[ResourceType]ResourceName“.</span><span class="sxs-lookup"><span data-stu-id="154ec-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`\`.</span></span>| 

## <a name="example-1"></a><span data-ttu-id="154ec-139">Beispiel 1</span><span class="sxs-lookup"><span data-stu-id="154ec-139">Example 1</span></span>

<span data-ttu-id="154ec-140">Im folgenden Beispiel wird veranschaulicht, wie sichergestellt wird, dass eine Gruppe namens „TestGroup“ nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="154ec-140">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span> 

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```
## <a name="example-2"></a><span data-ttu-id="154ec-141">Beispiel 2</span><span class="sxs-lookup"><span data-stu-id="154ec-141">Example 2</span></span>
<span data-ttu-id="154ec-142">Im folgenden Beispiel wird veranschaulicht, wie Sie einen Active Directory-Benutzer der lokalen Administratorengruppe als Teil eines Testbuilds für mehrere Computer hinzufügen, bei dem Sie bereits PS-Anmeldeinformationen (PSCredential) für das Konto „Lokaler Administrator“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="154ec-142">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Adminstrator account.</span></span> <span data-ttu-id="154ec-143">Da diese auch für das Domänenadministratorkonto (nach der Domänenhöherstufung) verwendet werden, müssen wir diese vorhandenen PSCredential dann in domänenkompatible Anmeldeinformationen konvertieren, um es uns zu ermöglichen, der Gruppe „Lokale Administratoren“ auf dem Mitgliedsserver einen Domänenbenutzer hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="154ec-143">As this is also used for the Domain Admin Account (after Domain promotion) we then need to convert this existing PSCredential to a Domain Friendly credential to enable us to add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
     @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'   
      }    
    )
}
                  
$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup
        {
            GroupName='Administrators'   
            Ensure= 'Present'             
            MembersToInclude= "$domain\$($Node.AdminAccount)"
            Credential = $dCredential    
            PsDscRunAsCredential = $DCredential
        }
```

## <a name="example-3"></a><span data-ttu-id="154ec-144">Beispiel 3</span><span class="sxs-lookup"><span data-stu-id="154ec-144">Example 3</span></span>
<span data-ttu-id="154ec-145">Das folgende Beispiel zeigt, wie sichergestellt wird, dass die lokale Gruppe „TigerTeamAdmins“ auf dem Server „TigerTeamSource.Contoso.Com“ ein bestimmtes Domänenkonto, „Contoso\JerryG“, nicht enthält.</span><span class="sxs-lookup"><span data-stu-id="154ec-145">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>  

```powershell

Configuration SecureTigerTeamSrouce 
{
  Import-DscResource -ModuleName 'PSDesiredStateConfiguration'
  
  Node TigerTeamSource.Contoso.Com {
  Group TigerTeamAdmins
    {
       GroupName        = 'TigerTeamAdmins'   
       Ensure           = 'Absent'             
       MembersToInclude = "Contoso\JerryG"
    }
  }
}
```

