---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „User“
ms.openlocfilehash: f2660933aec43967e3f4082a983ef328a5b93851
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
#<a name="dsc-user-resource"></a><span data-ttu-id="9ce17-103">DSC-Ressource „User“#</span><span class="sxs-lookup"><span data-stu-id="9ce17-103">DSC User Resource#</span></span>


><span data-ttu-id="9ce17-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9ce17-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="9ce17-105">Die Ressource __User__ in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Benutzerkonten auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="9ce17-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="9ce17-106">Syntax##</span><span class="sxs-lookup"><span data-stu-id="9ce17-106">Syntax##</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="9ce17-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="9ce17-107">Properties</span></span>
|  <span data-ttu-id="9ce17-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="9ce17-108">Property</span></span>  |  <span data-ttu-id="9ce17-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ce17-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="9ce17-110">UserName</span><span class="sxs-lookup"><span data-stu-id="9ce17-110">UserName</span></span>| <span data-ttu-id="9ce17-111">Gibt den Kontonamen an, für den Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="9ce17-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="9ce17-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ce17-112">Description</span></span>| <span data-ttu-id="9ce17-113">Gibt die Beschreibung an, die Sie für das Benutzerkonto verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="9ce17-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="9ce17-114">Disabled</span><span class="sxs-lookup"><span data-stu-id="9ce17-114">Disabled</span></span>| <span data-ttu-id="9ce17-115">Gibt an, ob das Konto aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="9ce17-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="9ce17-116">Legen Sie diese Eigenschaft auf __$true__ fest, um sicherzustellen, dass dieses Konto deaktiviert ist. Legen Sie sie auf __$false__ fest, um sicherzustellen, dass es aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="9ce17-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>|
| <span data-ttu-id="9ce17-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="9ce17-117">Ensure</span></span>| <span data-ttu-id="9ce17-118">Gibt an, ob das Konto vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="9ce17-118">Indicates if the account exists.</span></span> <span data-ttu-id="9ce17-119">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass das Konto vorhanden ist. Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass das Konto nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="9ce17-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="9ce17-120">FullName</span><span class="sxs-lookup"><span data-stu-id="9ce17-120">FullName</span></span>| <span data-ttu-id="9ce17-121">Stellt eine Zeichenfolge mit dem vollständigen Namen dar, den Sie für das Benutzerkonto verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="9ce17-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="9ce17-122">Password</span><span class="sxs-lookup"><span data-stu-id="9ce17-122">Password</span></span>| <span data-ttu-id="9ce17-123">Gibt das Kennwort an, das Sie für dieses Konto verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="9ce17-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="9ce17-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="9ce17-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="9ce17-125">Gibt an, ob der Benutzer das Kennwort ändern kann.</span><span class="sxs-lookup"><span data-stu-id="9ce17-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="9ce17-126">Legen Sie diese Eigenschaft auf __$true__ fest, um sicherzustellen, dass der Benutzer das Kennwort nicht ändern kann. Legen Sie es auf __$false__ fest, damit der Benutzer das Kennwort ändern kann.</span><span class="sxs-lookup"><span data-stu-id="9ce17-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="9ce17-127">Der Standardwert ist __$false__.</span><span class="sxs-lookup"><span data-stu-id="9ce17-127">The default value is __$false__.</span></span>|
| <span data-ttu-id="9ce17-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="9ce17-128">PasswordChangeRequired</span></span>| <span data-ttu-id="9ce17-129">Gibt an, ob der Benutzer sein Kennwort bei der nächsten Anmeldung ändern muss.</span><span class="sxs-lookup"><span data-stu-id="9ce17-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="9ce17-130">Legen Sie diese Eigenschaft auf __$true__ fest, wenn der Benutzer das Kennwort ändern muss.</span><span class="sxs-lookup"><span data-stu-id="9ce17-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="9ce17-131">Der Standardwert ist __$true__.</span><span class="sxs-lookup"><span data-stu-id="9ce17-131">The default value is __$true__.</span></span>|
| <span data-ttu-id="9ce17-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="9ce17-132">PasswordNeverExpires</span></span>| <span data-ttu-id="9ce17-133">Gibt an, ob das Kennwort abläuft.</span><span class="sxs-lookup"><span data-stu-id="9ce17-133">Indicates if the password will expire.</span></span> <span data-ttu-id="9ce17-134">Um sicherzustellen, dass das Kennwort für dieses Konto nicht abläuft, legen Sie diese Eigenschaft auf __$true__ fest. Legen Sie sie auf __$false__ fest, wenn das Kennwort abläuft.</span><span class="sxs-lookup"><span data-stu-id="9ce17-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="9ce17-135">Der Standardwert ist __$false__.</span><span class="sxs-lookup"><span data-stu-id="9ce17-135">The default value is __$false__.</span></span>|
| <span data-ttu-id="9ce17-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9ce17-136">DependsOn</span></span> | <span data-ttu-id="9ce17-137">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="9ce17-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9ce17-138">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9ce17-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="9ce17-139">Beispiel</span><span class="sxs-lookup"><span data-stu-id="9ce17-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```