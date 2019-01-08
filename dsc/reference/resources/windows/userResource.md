---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „User“
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047885"
---
# <a name="dsc-user-resource"></a><span data-ttu-id="43441-103">DSC-Ressource „User“</span><span class="sxs-lookup"><span data-stu-id="43441-103">DSC User Resource</span></span>

<span data-ttu-id="43441-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="43441-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="43441-105">Die Ressource **User** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten lokaler Benutzerkonten auf dem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="43441-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="43441-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="43441-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="43441-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="43441-107">Properties</span></span>

|  <span data-ttu-id="43441-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="43441-108">Property</span></span>  |  <span data-ttu-id="43441-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="43441-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="43441-110">UserName</span><span class="sxs-lookup"><span data-stu-id="43441-110">UserName</span></span>| <span data-ttu-id="43441-111">Gibt den Kontonamen an, für den Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="43441-111">Indicates the account name for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="43441-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="43441-112">Description</span></span>| <span data-ttu-id="43441-113">Gibt die Beschreibung an, die Sie für das Benutzerkonto verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="43441-113">Indicates the description you want to use for the user account.</span></span>|
| <span data-ttu-id="43441-114">Disabled</span><span class="sxs-lookup"><span data-stu-id="43441-114">Disabled</span></span>| <span data-ttu-id="43441-115">Gibt an, ob das Konto aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="43441-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="43441-116">Legen Sie diese Eigenschaft auf `$true` fest, um sicherzustellen, dass dieses Konto deaktiviert ist. Legen Sie sie auf `$false` fest, um sicherzustellen, dass es aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="43441-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span>|
| <span data-ttu-id="43441-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="43441-117">Ensure</span></span>| <span data-ttu-id="43441-118">Gibt an, ob das Konto vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="43441-118">Indicates if the account exists.</span></span> <span data-ttu-id="43441-119">Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass das Konto vorhanden ist. Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass das Konto nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="43441-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>|
| <span data-ttu-id="43441-120">FullName</span><span class="sxs-lookup"><span data-stu-id="43441-120">FullName</span></span>| <span data-ttu-id="43441-121">Stellt eine Zeichenfolge mit dem vollständigen Namen dar, den Sie für das Benutzerkonto verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="43441-121">Represents a string with the full name you want to use for the user account.</span></span>|
| <span data-ttu-id="43441-122">Password</span><span class="sxs-lookup"><span data-stu-id="43441-122">Password</span></span>| <span data-ttu-id="43441-123">Gibt das Kennwort an, das Sie für dieses Konto verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="43441-123">Indicates the password you want to use for this account.</span></span> |
| <span data-ttu-id="43441-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="43441-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="43441-125">Gibt an, ob der Benutzer das Kennwort ändern kann.</span><span class="sxs-lookup"><span data-stu-id="43441-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="43441-126">Legen Sie diese Eigenschaft auf `$true` fest, um sicherzustellen, dass der Benutzer das Kennwort nicht ändern kann. Legen Sie es auf `$false` fest, damit der Benutzer das Kennwort ändern kann.</span><span class="sxs-lookup"><span data-stu-id="43441-126">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="43441-127">Der Standardwert ist `$false`.</span><span class="sxs-lookup"><span data-stu-id="43441-127">The default value is `$false`.</span></span>|
| <span data-ttu-id="43441-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="43441-128">PasswordChangeRequired</span></span>| <span data-ttu-id="43441-129">Gibt an, ob der Benutzer sein Kennwort bei der nächsten Anmeldung ändern muss.</span><span class="sxs-lookup"><span data-stu-id="43441-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="43441-130">Legen Sie diese Eigenschaft auf `$true` fest, wenn der Benutzer das Kennwort ändern muss.</span><span class="sxs-lookup"><span data-stu-id="43441-130">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="43441-131">Der Standardwert ist `$true`.</span><span class="sxs-lookup"><span data-stu-id="43441-131">The default value is `$true`.</span></span>|
| <span data-ttu-id="43441-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="43441-132">PasswordNeverExpires</span></span>| <span data-ttu-id="43441-133">Gibt an, ob das Kennwort abläuft.</span><span class="sxs-lookup"><span data-stu-id="43441-133">Indicates if the password will expire.</span></span> <span data-ttu-id="43441-134">Um sicherzustellen, dass das Kennwort für dieses Konto nie abläuft, legen Sie diese Eigenschaft auf `$true` fest. Legen Sie sie auf `$false` fest, wenn das Kennwort ablaufen soll.</span><span class="sxs-lookup"><span data-stu-id="43441-134">To ensure that the password for this account will never expire, set this property to `$true`, and set it to `$false` if the password will expire.</span></span> <span data-ttu-id="43441-135">Der Standardwert ist `$false`.</span><span class="sxs-lookup"><span data-stu-id="43441-135">The default value is `$false`.</span></span>|
| <span data-ttu-id="43441-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="43441-136">DependsOn</span></span> | <span data-ttu-id="43441-137">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="43441-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="43441-138">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="43441-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="43441-139">Beispiel</span><span class="sxs-lookup"><span data-stu-id="43441-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```