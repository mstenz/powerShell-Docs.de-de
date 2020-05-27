---
title: WS-Management-Remoting (WSMan) in PowerShell Core
description: Remoting in PowerShell Core mithilfe von WSMan
ms.date: 08/06/2018
ms.openlocfilehash: 7b090e1463808ab10758bbd417d52fcc16c31366
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564512"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="17476-103">WS-Management-Remoting (WSMan) in PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="17476-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="17476-104">Anweisungen zum Erstellen eines Remoting-Endpunkts</span><span class="sxs-lookup"><span data-stu-id="17476-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="17476-105">Das PowerShell Core-Paket für Windows enthält ein WinRM-Plug-In (`pwrshplugin.dll`) und ein Installationsskript (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="17476-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="17476-106">Diese Dateien ermöglichen PowerShell eingehende PowerShell-Remoteverbindungen anzunehmen, wenn ihr Endpunkt angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="17476-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="17476-107">Motivation</span><span class="sxs-lookup"><span data-stu-id="17476-107">Motivation</span></span>

<span data-ttu-id="17476-108">Eine PowerShell-Installation kann mithilfe von `New-PSSession` und `Enter-PSSession` PowerShell-Sitzungen mit Remotecomputern erstellen.</span><span class="sxs-lookup"><span data-stu-id="17476-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="17476-109">Der Benutzer muss zunächst einen WinRM-Remoting-Endpunkt erstellen, um PowerShell das Annehmen von eingehenden Remoteverbindungen zu erlauben.</span><span class="sxs-lookup"><span data-stu-id="17476-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="17476-110">Dies ist ein Szenario mit expliziter Anmeldung, bei dem der Benutzer „Install-PowerShellRemoting.ps1“ ausführt, um den WinRM-Endpunkt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="17476-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="17476-111">Das Installationsskript ist eine kurzfristige Lösung, bis `Enable-PSRemoting` eine zusätzliche Funktion hinzugefügt wird, um diese Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="17476-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="17476-112">Weitere Informationen finden Sie im Ticket [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="17476-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="17476-113">Skriptaktionen</span><span class="sxs-lookup"><span data-stu-id="17476-113">Script Actions</span></span>

<span data-ttu-id="17476-114">Das Skript</span><span class="sxs-lookup"><span data-stu-id="17476-114">The script</span></span>

1. <span data-ttu-id="17476-115">Erstellt ein Verzeichnis für das Plug-In unter `$env:windir\System32\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="17476-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="17476-116">Kopiert „Pwrshplugin.dll“ an diesen Speicherort</span><span class="sxs-lookup"><span data-stu-id="17476-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="17476-117">Erstellt eine Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="17476-117">Generates a configuration file</span></span>
1. <span data-ttu-id="17476-118">Registriert das Plug-In für WinRM</span><span class="sxs-lookup"><span data-stu-id="17476-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="17476-119">Registrierung</span><span class="sxs-lookup"><span data-stu-id="17476-119">Registration</span></span>

<span data-ttu-id="17476-120">Das Skript muss in einer PowerShell-Sitzung auf Administratorebene ausgeführt werden, und wird in zwei Modi ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="17476-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="17476-121">Wird durch die PowerShell-Instanz ausgeführt, die es registriert</span><span class="sxs-lookup"><span data-stu-id="17476-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="17476-122">Wird durch eine andere PowerShell-Instanz für die Instanz ausgeführt, die registriert wird</span><span class="sxs-lookup"><span data-stu-id="17476-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="17476-123">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="17476-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="17476-124">**Hinweis:** Das Remoting-Registrierungsskript startet WinRM neu, deshalb werden alle vorhandenen PSRP-Sitzungen sofort beendet, wenn das Skript ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="17476-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="17476-125">Wenn es während einer Remotesitzung ausgeführt wird, wird die Verbindung beendet.</span><span class="sxs-lookup"><span data-stu-id="17476-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="17476-126">Herstellen einer Verbindung mit dem neuen Endpunkt</span><span class="sxs-lookup"><span data-stu-id="17476-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="17476-127">Erstellen Sie eine PowerShell-Sitzung mit dem neuen PowerShell-Endpunkt, indem Sie `-ConfigurationName "some endpoint name"` angeben.</span><span class="sxs-lookup"><span data-stu-id="17476-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="17476-128">Verwenden Sie zum Verbinden mit der PowerShell-Instanz aus dem obigen Beispiel einen dieser Aufrufe:</span><span class="sxs-lookup"><span data-stu-id="17476-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="17476-129">Beachten Sie, dass `New-PSSession`- und `Enter-PSSession`-Aufrufe, die `-ConfigurationName` nicht angeben, den PowerShell-Standardendpunkt `microsoft.powershell` als Ziel verwenden.</span><span class="sxs-lookup"><span data-stu-id="17476-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>
