---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC für die Linux-Resource „nxUser“
ms.openlocfilehash: 4cf8080fbfa58e082ed007d42d6aa2648d1cf58a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557174"
---
# <a name="dsc-for-linux-nxuser-resource"></a><span data-ttu-id="28b75-103">DSC für die Linux-Resource „nxUser“</span><span class="sxs-lookup"><span data-stu-id="28b75-103">DSC for Linux nxUser Resource</span></span>

<span data-ttu-id="28b75-104">Die Ressource **nxUser** in PowerShell DSC (Desired State Configuration) bietet einen Mechanismus zum Verwalten von Dateien und Verzeichnissen auf einem Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="28b75-104">The **nxUser** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage local users on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="28b75-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="28b75-105">Syntax</span></span>

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="28b75-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="28b75-106">Properties</span></span>

|<span data-ttu-id="28b75-107">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="28b75-107">Property</span></span> |<span data-ttu-id="28b75-108">Gibt den Kontonamen an, für den Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="28b75-108">Indicates the account name for which you want to ensure a specific state.</span></span> |
|---|---|
|<span data-ttu-id="28b75-109">UserName</span><span class="sxs-lookup"><span data-stu-id="28b75-109">UserName</span></span> |<span data-ttu-id="28b75-110">Gibt den Speicherort an, an dem Sie den Zustand einer Datei oder eines Verzeichnisses sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="28b75-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="28b75-111">FullName</span><span class="sxs-lookup"><span data-stu-id="28b75-111">FullName</span></span> |<span data-ttu-id="28b75-112">Eine Zeichenfolge, die den vollständigen Namen des Benutzerkontos enthält.</span><span class="sxs-lookup"><span data-stu-id="28b75-112">A string that contains the full name to use for the user account.</span></span> |
|<span data-ttu-id="28b75-113">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="28b75-113">Description</span></span> |<span data-ttu-id="28b75-114">Die Beschreibung des Benutzerkontos.</span><span class="sxs-lookup"><span data-stu-id="28b75-114">The description for the user account.</span></span> |
|<span data-ttu-id="28b75-115">Kennwort</span><span class="sxs-lookup"><span data-stu-id="28b75-115">Password</span></span> |<span data-ttu-id="28b75-116">Der Hash des Benutzerkennworts im entsprechenden Format für den Linux-Computer.</span><span class="sxs-lookup"><span data-stu-id="28b75-116">The hash of the users password in the appropriate form for the Linux computer.</span></span> <span data-ttu-id="28b75-117">Dies ist normalerweise ein nach dem Zufallsprinzip gewählter SHA-256- oder SHA-512-Hash.</span><span class="sxs-lookup"><span data-stu-id="28b75-117">Typically, this is a salted SHA-256, or SHA-512 hash.</span></span> <span data-ttu-id="28b75-118">Unter Debian und Ubuntu Linux kann dieser Wert mit dem Befehl `mkpasswd` generiert werden.</span><span class="sxs-lookup"><span data-stu-id="28b75-118">On Debian and Ubuntu Linux, this value can be generated with the `mkpasswd` command.</span></span> <span data-ttu-id="28b75-119">Für andere Linux-Distributionen kann die „crypt“-Methode der Crypt-Bibliothek von Python zum Generieren des Hashes verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="28b75-119">For other Linux distros, the crypt method of Python's Crypt library can be used to generate the hash.</span></span> |
|<span data-ttu-id="28b75-120">Disabled</span><span class="sxs-lookup"><span data-stu-id="28b75-120">Disabled</span></span> |<span data-ttu-id="28b75-121">Gibt an, ob das Konto aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="28b75-121">Indicates whether the account is enabled.</span></span> <span data-ttu-id="28b75-122">Legen Sie diese Eigenschaft auf `$true` fest, um sicherzustellen, dass dieses Konto deaktiviert ist. Legen Sie sie auf `$false` fest, um sicherzustellen, dass es aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="28b75-122">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="28b75-123">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="28b75-123">PasswordChangeRequired</span></span> |<span data-ttu-id="28b75-124">Gibt an, ob der Benutzer das Kennwort ändern kann.</span><span class="sxs-lookup"><span data-stu-id="28b75-124">Indicates whether the user can change the password.</span></span> <span data-ttu-id="28b75-125">Legen Sie diese Eigenschaft auf `$true` fest, um sicherzustellen, dass der Benutzer das Kennwort nicht ändern kann. Legen Sie es auf `$false` fest, damit der Benutzer das Kennwort ändern kann.</span><span class="sxs-lookup"><span data-stu-id="28b75-125">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="28b75-126">Standardwert: `$false`.</span><span class="sxs-lookup"><span data-stu-id="28b75-126">The default value is `$false`.</span></span> <span data-ttu-id="28b75-127">Diese Eigenschaft wird nur ausgewertet, wenn das Benutzerkonto zuvor nicht vorhanden war und erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="28b75-127">This property is only evaluated if the user account did not exist previously and is being created.</span></span> |
|<span data-ttu-id="28b75-128">HomeDirectory</span><span class="sxs-lookup"><span data-stu-id="28b75-128">HomeDirectory</span></span> |<span data-ttu-id="28b75-129">Das Basisverzeichnis des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="28b75-129">The home directory for the user.</span></span> |
|<span data-ttu-id="28b75-130">GroupID</span><span class="sxs-lookup"><span data-stu-id="28b75-130">GroupID</span></span> |<span data-ttu-id="28b75-131">Die primäre Gruppen-ID des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="28b75-131">The primary group ID for the user.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="28b75-132">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="28b75-132">Common properties</span></span>

|<span data-ttu-id="28b75-133">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="28b75-133">Property</span></span> |<span data-ttu-id="28b75-134">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="28b75-134">Description</span></span> |
|---|---|
|<span data-ttu-id="28b75-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="28b75-135">DependsOn</span></span> |<span data-ttu-id="28b75-136">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="28b75-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="28b75-137">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="28b75-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="28b75-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="28b75-138">Ensure</span></span> |<span data-ttu-id="28b75-139">Gibt an, ob das Konto vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="28b75-139">Specifies whether the account exists.</span></span> <span data-ttu-id="28b75-140">Legen Sie diese Eigenschaft auf **Present** fest, um sicherzustellen, dass das Konto vorhanden ist. Legen Sie sie auf **Absent** fest, um sicherzustellen, dass das Konto nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="28b75-140">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> |

## <a name="example"></a><span data-ttu-id="28b75-141">Beispiel</span><span class="sxs-lookup"><span data-stu-id="28b75-141">Example</span></span>

<span data-ttu-id="28b75-142">Im folgenden Beispiel wird sichergestellt, dass der Benutzer „monuser“ vorhanden und Mitglied der Gruppe „DBusers“ ist.</span><span class="sxs-lookup"><span data-stu-id="28b75-142">The following example ensures that the user "monuser" exists and is a member of the group "DBusers".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
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
