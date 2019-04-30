---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: ryanpu
title: Verbesserungen bei Just Enough Administration (JEA)
ms.openlocfilehash: 66cbacb78f8a365e9c8556c7c56b3c3525de7395
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055631"
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="d93df-103">Verbesserungen bei Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="d93df-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="d93df-104">Eingeschränktes Kopieren von Dateien auf einen bzw. von einem JEA-Endpunkt</span><span class="sxs-lookup"><span data-stu-id="d93df-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="d93df-105">Sie können Dateien jetzt remote auf einen bzw. von einem JEA-Endpunkt kopieren und sich dabei darauf verlassen, dass der Benutzer, der die Verbindung herstellt, keine *beliebige* Datei auf Ihrem System kopieren kann.</span><span class="sxs-lookup"><span data-stu-id="d93df-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span> <span data-ttu-id="d93df-106">Dies ist möglich, indem Sie Ihre PSSC-Datei für die Bereitstellung eines Benutzerlaufwerks konfigurieren, mit dem sich Benutzer verbinden können.</span><span class="sxs-lookup"><span data-stu-id="d93df-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span> <span data-ttu-id="d93df-107">Das Benutzerlaufwerk ist ein neues PSDrive, das für jeden Benutzer, der eine Verbindung herstellt, einzigartig ist und über mehrere Sitzungen hinweg beibehalten wird.</span><span class="sxs-lookup"><span data-stu-id="d93df-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span> <span data-ttu-id="d93df-108">Wenn zum Kopieren von Dateien in eine bzw. aus einer JEA-Sitzung `Copy-Item` verwendet wird, wird der Zugriff nur auf das Benutzerlaufwerk gestattet.</span><span class="sxs-lookup"><span data-stu-id="d93df-108">When `Copy-Item` is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span> <span data-ttu-id="d93df-109">Beim Versuch, Dateien auf ein anderes PSDrive zu kopieren, wird der Vorgang mit einem Fehler abgebrochen.</span><span class="sxs-lookup"><span data-stu-id="d93df-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="d93df-110">Verwenden Sie die folgenden neuen Felder, um das Benutzerlaufwerk in Ihrer Konfigurationsdatei für JEA-Sitzungen einzurichten:</span><span class="sxs-lookup"><span data-stu-id="d93df-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="d93df-111">Der Ordner zum Sichern des Benutzerlaufwerks wird in `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER` erstellt.</span><span class="sxs-lookup"><span data-stu-id="d93df-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="d93df-112">Um das Benutzerlaufwerk zu verwenden und Dateien auf einen bzw. von einem JEA-Endpunkt zu kopieren, der für die Bereitstellung des Benutzerlaufwerks konfiguriert ist, verwenden Sie `Copy-Item` mit den Parametern `-ToSession` und `-FromSession`.</span><span class="sxs-lookup"><span data-stu-id="d93df-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on `Copy-Item`.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine.
# You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="d93df-113">Anschließend können Sie benutzerdefinierte Funktionen schreiben, um die auf dem Benutzerlaufwerk gespeicherten Daten zu verarbeiten und für Benutzer in Ihrer Datei für Rollenfunktionen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="d93df-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="d93df-114">Unterstützung für gruppenverwaltete Dienstkonten</span><span class="sxs-lookup"><span data-stu-id="d93df-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="d93df-115">In einigen Fällen muss ein Task, den ein Benutzer in einer JEA-Sitzung ausführen muss, auf Ressourcen außerhalb des lokalen Computers zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d93df-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span> <span data-ttu-id="d93df-116">Wenn eine JEA-Sitzung für die Verwendung eines virtuellen Kontos konfiguriert ist, wird bei jedem Versuch, auf diese Ressourcen zuzugreifen, die Identität des lokalen Computers (nicht des virtuellen Kontos oder des verbundenen Benutzers) als Ursprung dieses Zugriffsversuchs angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d93df-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span> <span data-ttu-id="d93df-117">In TP5 kann JEA im Kontext eines [gruppenverwalteten Dienstkontos](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)) ausgeführt werden. Dadurch wird der Zugriff auf Netzwerkressourcen über eine Domänenidentität deutlich vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="d93df-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj128431\(v=ws.11\)), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="d93df-118">Um eine JEA-Sitzung für die Ausführung über ein gruppenverwaltetes Dienstkonto zu konfigurieren, verwenden Sie den folgenden neuen Schlüssel in Ihrer PSSC-Datei:</span><span class="sxs-lookup"><span data-stu-id="d93df-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> [!NOTE]
> <span data-ttu-id="d93df-119">Gruppenverwaltete Dienstkonten bieten nicht die Isolation oder den begrenzten Bereich virtueller Konten.</span><span class="sxs-lookup"><span data-stu-id="d93df-119">Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="d93df-120">Jeder verbundene Benutzer verwendet dieselbe Identität des gruppenverwalteten Dienstkontos, das möglicherweise über Berechtigungen für Ihr gesamtes Unternehmen verfügt.</span><span class="sxs-lookup"><span data-stu-id="d93df-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span> <span data-ttu-id="d93df-121">Gehen Sie daher mit Bedacht vor, wenn Sie die Verwendung eines gruppenverwalteten Dienstkontos wählen. Wenn möglich, sollten Sie immer virtuelle Konten vorziehen, die auf den lokalen Computer beschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="d93df-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="d93df-122">Richtlinien für bedingten Zugriff</span><span class="sxs-lookup"><span data-stu-id="d93df-122">Conditional access policies</span></span>

<span data-ttu-id="d93df-123">Bei JEA lässt sich hervorragend einschränken, welche Aufgaben ein Benutzer, der sich mit einem System verbunden hat, zum Verwalten des Systems ausführen darf. Doch wie gehen Sie vor, wenn Sie einschränken möchten, *wann* ein Benutzer JEA verwenden kann?</span><span class="sxs-lookup"><span data-stu-id="d93df-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span> <span data-ttu-id="d93df-124">Wir haben die Sitzungskonfigurationsdateien (PSSC-Dateien) um Optionen erweitert, mit denen Sie Sicherheitsgruppen angeben können, deren Mitglied ein Benutzer sein muss, um eine JEA-Sitzung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d93df-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span> <span data-ttu-id="d93df-125">Dies kann insbesondere dann nützlich sein, wenn Sie in Ihrer Umgebung über ein JIT-System (Just In Time) verfügen und festlegen möchten, dass Ihre Benutzer über erhöhte Berechtigungen verfügen müssen, bevor sie auf einen JEA-Endpunkt mit hohen Berechtigungen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d93df-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="d93df-126">Über das neue Feld *RequiredGroups* in der PSSC-Datei können Sie die Logik angeben, mit der ermittelt wird, ob ein Benutzer sich mit JEA verbinden kann.</span><span class="sxs-lookup"><span data-stu-id="d93df-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span> <span data-ttu-id="d93df-127">Dazu geben Sie eine (optional geschachtelte) Hashtabelle an, die zum Erstellen Ihrer Regeln die Schlüssel „And“ und „Or“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="d93df-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span> <span data-ttu-id="d93df-128">Nachfolgend finden Sie einige Beispiele für die Verwendung dieses Felds:</span><span class="sxs-lookup"><span data-stu-id="d93df-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="d93df-129">Behoben: Virtuelle Konten werden jetzt unter Windows Server 2008 R2 unterstützt</span><span class="sxs-lookup"><span data-stu-id="d93df-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>

<span data-ttu-id="d93df-130">In WMF 5.1 können nun virtuelle Konten auf Windows Server 2008 R2 verwendet werden, sodass für Windows Server 2008 R2 - 2016 jetzt konsistente Konfigurationen und übereinstimmende Features bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="d93df-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span> <span data-ttu-id="d93df-131">Bei Verwendung von JEA unter Windows 7 werden virtuelle Konten weiterhin nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d93df-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>