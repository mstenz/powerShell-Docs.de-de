---
title: Ändern des psmodulepath-Installations Pfads | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953839"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="5febe-102">Ändern des Installationspfads PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5febe-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="5febe-103">Die `PSModulePath`-Umgebungsvariable speichert die Pfade zu den Speicherorten der Module, die auf dem Datenträger installiert sind.</span><span class="sxs-lookup"><span data-stu-id="5febe-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="5febe-104">PowerShell verwendet diese Variable, um Module zu suchen, wenn der Benutzer nicht den vollständigen Pfad zu einem Modul angibt.</span><span class="sxs-lookup"><span data-stu-id="5febe-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="5febe-105">Die Pfade in dieser Variablen werden in der Reihenfolge durchsucht, in der Sie angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5febe-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="5febe-106">Wenn PowerShell gestartet wird, wird `PSModulePath` als System Umgebungsvariable mit dem folgenden Standardwert erstellt: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` oder `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` für Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5febe-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` or `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="5febe-107">So zeigen Sie die psmodulepath-Variable an</span><span class="sxs-lookup"><span data-stu-id="5febe-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="5febe-108">Geben Sie den folgenden Befehl ein, um die in der `PSModulePath` Variablen angegebenen Pfade anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="5febe-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="5febe-109">So fügen Sie der psmodulepath-Variablen Speicherorte hinzu</span><span class="sxs-lookup"><span data-stu-id="5febe-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="5febe-110">Um dieser Variablen Pfade hinzuzufügen, verwenden Sie eine der folgenden Methoden:</span><span class="sxs-lookup"><span data-stu-id="5febe-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="5febe-111">Wenn Sie einen temporären Wert hinzufügen möchten, der nur für die aktuelle Sitzung verfügbar ist, führen Sie den folgenden Befehl in der Befehlszeile aus:</span><span class="sxs-lookup"><span data-stu-id="5febe-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="5febe-112">Wenn Sie einen persistenten Wert hinzufügen möchten, der immer verfügbar ist, wenn eine Sitzung geöffnet wird, fügen Sie den obigen Befehl einer PowerShell-Profil Datei (`$PROFILE`) hinzu ></span><span class="sxs-lookup"><span data-stu-id="5febe-112">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="5febe-113">Weitere Informationen zu Profilen finden Sie unter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="5febe-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="5febe-114">Um der Registrierung eine permanente Variable hinzuzufügen, erstellen Sie eine neue Benutzer Umgebungsvariable mit dem Namen `PSModulePath`, indem Sie im Dialogfeld **System Eigenschaften** den Umgebungsvariablen-Editor verwenden.</span><span class="sxs-lookup"><span data-stu-id="5febe-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="5febe-115">Verwenden Sie die .NET-Methode " [stenvironmentvariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) " in der [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) -Klasse, um eine persistente Variable mithilfe eines Skripts hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5febe-115">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="5febe-116">Das folgende Skript fügt z. b. den `C:\Program Files\Fabrikam\Module` Pfad zum Wert der Umgebungsvariablen `PSModulePath` des Computers hinzu.</span><span class="sxs-lookup"><span data-stu-id="5febe-116">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="5febe-117">Um den Pfad der Umgebungsvariablen User `PSModulePath` hinzuzufügen, legen Sie für das Ziel den Wert "User" fest.</span><span class="sxs-lookup"><span data-stu-id="5febe-117">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="5febe-118">So entfernen Sie Speicherorte aus dem psmodulepath</span><span class="sxs-lookup"><span data-stu-id="5febe-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="5febe-119">Sie können Pfade aus der Variablen entfernen, indem Sie ähnliche Methoden verwenden, z. b. `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` den Pfad " **c:\modulepath** " aus der aktuellen Sitzung entfernt.</span><span class="sxs-lookup"><span data-stu-id="5febe-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="5febe-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5febe-120">See Also</span></span>

[<span data-ttu-id="5febe-121">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="5febe-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
