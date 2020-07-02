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
ms.openlocfilehash: 02e9868fc5c536629f7abc319df06f9a4a394ac8
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837493"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="40121-102">Ändern des Installationspfads PSModulePath</span><span class="sxs-lookup"><span data-stu-id="40121-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="40121-103">Die `PSModulePath` Umgebungsvariable speichert die Pfade zu den Speicherorten der Module, die auf dem Datenträger installiert sind.</span><span class="sxs-lookup"><span data-stu-id="40121-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="40121-104">PowerShell verwendet diese Variable, um Module zu suchen, wenn der Benutzer nicht den vollständigen Pfad zu einem Modul angibt.</span><span class="sxs-lookup"><span data-stu-id="40121-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="40121-105">Die Pfade in dieser Variablen werden in der Reihenfolge durchsucht, in der Sie angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="40121-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="40121-106">Wenn PowerShell gestartet `PSModulePath` wird, wird als System Umgebungsvariable mit dem folgenden Standardwert erstellt: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` unter Windows und `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` unter Linux oder Mac sowie `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` für Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40121-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="40121-107">Der benutzerspezifische **CurrentUser** -Speicherort ist der `WindowsPowerShell\Modules` Ordner im Speicherort der **Dokumente** in Ihrem Benutzerprofil.</span><span class="sxs-lookup"><span data-stu-id="40121-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="40121-108">Der spezifische Pfad dieses Standorts variiert je nach Version von Windows und ob Sie die Ordner Umleitung verwenden.</span><span class="sxs-lookup"><span data-stu-id="40121-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="40121-109">Standardmäßig ist dieser Speicherort unter Windows 10 `$HOME\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="40121-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="40121-110">So zeigen Sie die psmodulepath-Variable an</span><span class="sxs-lookup"><span data-stu-id="40121-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="40121-111">Geben Sie den folgenden Befehl ein, um die in der Variablen angegebenen Pfade anzuzeigen `PSModulePath` :</span><span class="sxs-lookup"><span data-stu-id="40121-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="40121-112">So fügen Sie der psmodulepath-Variablen Speicherorte hinzu</span><span class="sxs-lookup"><span data-stu-id="40121-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="40121-113">Um dieser Variablen Pfade hinzuzufügen, verwenden Sie eine der folgenden Methoden:</span><span class="sxs-lookup"><span data-stu-id="40121-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="40121-114">Wenn Sie einen temporären Wert hinzufügen möchten, der nur für die aktuelle Sitzung verfügbar ist, führen Sie den folgenden Befehl in der Befehlszeile aus:</span><span class="sxs-lookup"><span data-stu-id="40121-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="40121-115">Wenn Sie einen persistenten Wert hinzufügen möchten, der immer verfügbar ist, wenn eine Sitzung geöffnet wird, fügen Sie den obigen Befehl einer PowerShell-Profil Datei ( `$PROFILE` ) hinzu ></span><span class="sxs-lookup"><span data-stu-id="40121-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="40121-116">Weitere Informationen zu Profilen finden Sie unter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="40121-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="40121-117">Um der Registrierung eine persistente Variable hinzuzufügen, erstellen Sie eine neue Benutzer Umgebungsvariable `PSModulePath` mit dem Namen, indem Sie im Dialogfeld **System Eigenschaften** den Umgebungsvariablen-Editor verwenden.</span><span class="sxs-lookup"><span data-stu-id="40121-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="40121-118">Verwenden Sie die .NET-Methode " [stenvironmentvariable](/dotnet/api/system.environment.setenvironmentvariable) " in der [System. Environment](/dotnet/api/system.environment) -Klasse, um eine persistente Variable mithilfe eines Skripts hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="40121-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="40121-119">Mit dem folgenden Skript wird z. b `C:\Program Files\Fabrikam\Module` . der Pfad zum Wert der `PSModulePath` Umgebungsvariablen für den Computer hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="40121-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="40121-120">Um den Pfad zur Benutzer `PSModulePath` Umgebungsvariablen hinzuzufügen, legen Sie für das Ziel den Wert "User" fest.</span><span class="sxs-lookup"><span data-stu-id="40121-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="40121-121">So entfernen Sie Speicherorte aus dem psmodulepath</span><span class="sxs-lookup"><span data-stu-id="40121-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="40121-122">Sie können Pfade aus der Variablen entfernen, indem Sie ähnliche Methoden verwenden: beispielsweise `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` wird der Pfad " **c:\modulepath** " aus der aktuellen Sitzung entfernt.</span><span class="sxs-lookup"><span data-stu-id="40121-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="40121-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="40121-123">See Also</span></span>

[<span data-ttu-id="40121-124">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="40121-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="40121-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="40121-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
