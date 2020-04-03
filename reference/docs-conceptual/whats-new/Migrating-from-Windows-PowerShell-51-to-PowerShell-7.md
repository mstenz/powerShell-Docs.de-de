---
title: Migrieren von Windows PowerShell 5.1 zu PowerShell 7
description: Informationen zum Update von PowerShell 5.1 auf PowerShell 7 für Ihre Windows-Plattformen.
ms.date: 03/25/2020
ms.openlocfilehash: e3881b1758f50119444969ad39541aec694cebe5
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500502"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="94017-103">Migrieren von Windows PowerShell 5.1 zu PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="94017-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="94017-104">PowerShell 7 wurde für Cloud-, lokale und Hybridumgebungen entwickelt und bietet Verbesserungen sowie [neue Features](What-s-New-in-PowerShell-70.md).</span><span class="sxs-lookup"><span data-stu-id="94017-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="94017-105">Parallele Installation und Ausführung mit Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="94017-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="94017-106">Verbesserte Kompatibilität mit vorhandenen Windows PowerShell-Modulen</span><span class="sxs-lookup"><span data-stu-id="94017-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="94017-107">Neue Sprachfeatures wie ternäre Operatoren und `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="94017-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="94017-108">Verbesserte Leistung</span><span class="sxs-lookup"><span data-stu-id="94017-108">Improved performance</span></span>
- <span data-ttu-id="94017-109">SSH-basiertes Remoting</span><span class="sxs-lookup"><span data-stu-id="94017-109">SSH-based remoting</span></span>
- <span data-ttu-id="94017-110">Plattformübergreifende Interoperabilität</span><span class="sxs-lookup"><span data-stu-id="94017-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="94017-111">Unterstützung für Docker-Container</span><span class="sxs-lookup"><span data-stu-id="94017-111">Support for Docker containers</span></span>

<span data-ttu-id="94017-112">PowerShell 7 funktioniert parallel mit Windows PowerShell, sodass Sie Editionen vor der Bereitstellung problemlos testen und vergleichen können.</span><span class="sxs-lookup"><span data-stu-id="94017-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="94017-113">Die Migration erfolgt einfach, schnell und betriebssicher</span><span class="sxs-lookup"><span data-stu-id="94017-113">Migration is simple, quick, and safe.</span></span> <span data-ttu-id="94017-114">.</span><span class="sxs-lookup"><span data-stu-id="94017-114">failure.</span></span>

<span data-ttu-id="94017-115">Die folgenden Windows-Betriebssysteme unterstützen PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="94017-115">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="94017-116">Windows 8.1 und 10</span><span class="sxs-lookup"><span data-stu-id="94017-116">Windows 8.1 and 10</span></span>
- <span data-ttu-id="94017-117">Windows Server 2012, 2012 R2, 2016, und 2019</span><span class="sxs-lookup"><span data-stu-id="94017-117">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="94017-118">PowerShell 7 lässt sich auch unter macOS und mehreren Linux-Distributionen ausführen.</span><span class="sxs-lookup"><span data-stu-id="94017-118">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="94017-119">Eine Liste der unterstützten Betriebssysteme und Informationen zum Supportlebenszyklus finden Sie unter [PowerShell-Supportlebenszyklus](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="94017-119">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="94017-120">Installieren von PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="94017-120">Installing PowerShell 7</span></span>

<span data-ttu-id="94017-121">Aus Gründen der Flexibilität und zur Unterstützung der Anforderungen von IT- und DevOps-Mitarbeitern sowie Entwicklern stehen mehrere Optionen zur Installation von PowerShell 7 zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="94017-121">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="94017-122">In den meisten Fällen können die Installationsoptionen auf die folgenden reduziert werden:</span><span class="sxs-lookup"><span data-stu-id="94017-122">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="94017-123">Bereitstellen von PowerShell mit dem [MSI-Paket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span><span class="sxs-lookup"><span data-stu-id="94017-123">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="94017-124">Bereitstellen von PowerShell mit dem [ZIP-Paket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span><span class="sxs-lookup"><span data-stu-id="94017-124">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="94017-125">Das MSI-Paket kann mit Verwaltungsprodukten wie [System Center Configuration Manager (SCCM)](/configmgr/apps/) bereitgestellt und aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="94017-125">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="94017-126">Laden Sie die Pakete von der [GitHub-Seite „Releases“](https://github.com/PowerShell/PowerShell/releases) herunter.</span><span class="sxs-lookup"><span data-stu-id="94017-126">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="94017-127">Zum Bereitstellen des MSI-Pakets sind Administratorberechtigungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="94017-127">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="94017-128">Das ZIP-Paket kann von beliebigen Benutzern bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="94017-128">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="94017-129">Das ZIP-Paket ist die einfachste Möglichkeit, PowerShell 7 zum Testen zu installieren, bevor eine vollständige Installation erfolgt.</span><span class="sxs-lookup"><span data-stu-id="94017-129">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="94017-130">Parallele Nutzung von PowerShell 7 mit Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="94017-130">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="94017-131">PowerShell 7 ist für die parallele Nutzung mit Windows PowerShell 5.1 konzipiert.</span><span class="sxs-lookup"><span data-stu-id="94017-131">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="94017-132">Die folgenden Features stellen sicher, dass Ihre Investition in PowerShell geschützt und die Migration zu PowerShell 7 einfach ist.</span><span class="sxs-lookup"><span data-stu-id="94017-132">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="94017-133">Trennung von Installationspfad und Namen der ausführbaren Datei</span><span class="sxs-lookup"><span data-stu-id="94017-133">Separate installation path and executable name</span></span>
- <span data-ttu-id="94017-134">Trennung von PSModulePath</span><span class="sxs-lookup"><span data-stu-id="94017-134">Separate PSModulePath</span></span>
- <span data-ttu-id="94017-135">Getrennte Profile für jede Version</span><span class="sxs-lookup"><span data-stu-id="94017-135">Separate profiles for each version</span></span>
- <span data-ttu-id="94017-136">Verbesserte Modulkompatibilität</span><span class="sxs-lookup"><span data-stu-id="94017-136">Improved module compatibility</span></span>
- <span data-ttu-id="94017-137">Neue Remoting-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="94017-137">New remoting endpoints</span></span>
- <span data-ttu-id="94017-138">Unterstützung von Gruppenrichtlinien</span><span class="sxs-lookup"><span data-stu-id="94017-138">Group policy support</span></span>
- <span data-ttu-id="94017-139">Getrennte Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="94017-139">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="94017-140">Trennung von Installationspfad und Namen der ausführbaren Datei</span><span class="sxs-lookup"><span data-stu-id="94017-140">Separate installation path and executable name</span></span>

<span data-ttu-id="94017-141">PowerShell 7 wird in ein neues Verzeichnis installiert und ermöglicht die parallele Ausführung mit Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="94017-141">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="94017-142">Installationsspeicherorte nach Version:</span><span class="sxs-lookup"><span data-stu-id="94017-142">Install locations by version:</span></span>

- <span data-ttu-id="94017-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="94017-143">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="94017-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="94017-144">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="94017-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="94017-145">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="94017-146">Der neue Speicherort wird Ihrer Umgebungsvariablen PATH hinzugefügt, sodass Sie sowohl Windows PowerShell 5.1 als auch PowerShell 7 ausführen können.</span><span class="sxs-lookup"><span data-stu-id="94017-146">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="94017-147">Wenn Sie von PowerShell Core 6.x zu PowerShell 7 migrieren, wird PowerShell 6 entfernt und PATH ersetzt.</span><span class="sxs-lookup"><span data-stu-id="94017-147">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="94017-148">In Windows PowerShell heißt die ausführbare Datei `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="94017-148">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="94017-149">Ab Version 6 heißt die ausführbare Datei `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="94017-149">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="94017-150">Der neue Name vereinfacht die parallele Ausführung beider Versionen.</span><span class="sxs-lookup"><span data-stu-id="94017-150">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="94017-151">Trennung von PSModulePath</span><span class="sxs-lookup"><span data-stu-id="94017-151">Separate PSModulePath</span></span>

<span data-ttu-id="94017-152">Standardmäßig werden Module in Windows PowerShell und PowerShell 7 an verschiedenen Speicherorten gespeichert.</span><span class="sxs-lookup"><span data-stu-id="94017-152">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="94017-153">PowerShell 7 kombiniert diese Speicherorte in der Umgebungsvariablen `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="94017-153">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="94017-154">Wenn Sie ein Modul nach Name importieren, prüft PowerShell den von `$Env:PSModulePath` angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="94017-154">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="94017-155">Dies ermöglicht PowerShell 7 das Laden von Core- und Desktop-Modulen.</span><span class="sxs-lookup"><span data-stu-id="94017-155">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="94017-156">Installationsumfang</span><span class="sxs-lookup"><span data-stu-id="94017-156">Install Scope</span></span>            |                <span data-ttu-id="94017-157">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="94017-157">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="94017-158">PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="94017-158">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="94017-159">PowerShell-Module</span><span class="sxs-lookup"><span data-stu-id="94017-159">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="94017-160">Vom Benutzer installierter</span><span class="sxs-lookup"><span data-stu-id="94017-160">User installed</span></span><br><span data-ttu-id="94017-161">Geltungsbereich AllUsers</span><span class="sxs-lookup"><span data-stu-id="94017-161">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="94017-162">Vom Benutzer installierter</span><span class="sxs-lookup"><span data-stu-id="94017-162">User installed</span></span><br><span data-ttu-id="94017-163">Geltungsbereich CurrentUser</span><span class="sxs-lookup"><span data-stu-id="94017-163">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="94017-164">In den folgenden Beispielen sind die Standardwerte von `$Env:PSModulePath` für jede Version angegeben.</span><span class="sxs-lookup"><span data-stu-id="94017-164">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="94017-165">Windows PowerShell 5.1:</span><span class="sxs-lookup"><span data-stu-id="94017-165">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="94017-166">PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="94017-166">For PowerShell 7:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

<span data-ttu-id="94017-167">Beachten Sie, dass PowerShell 7 die Windows PowerShell-Pfade und die PowerShell 7-Pfade enthält, um das automatische Laden von Modulen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="94017-167">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="94017-168">Zusätzliche Pfade sind möglicherweise vorhanden, wenn Sie die Umgebungsvariable PSModulePath geändert oder benutzerdefinierte Module oder Anwendungen installiert haben.</span><span class="sxs-lookup"><span data-stu-id="94017-168">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="94017-169">Weitere Informationen finden Sie unter [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences) in `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="94017-169">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="94017-170">Weitere Informationen zu Modulen finden Sie unter [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span><span class="sxs-lookup"><span data-stu-id="94017-170">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="94017-171">Getrennte Profile</span><span class="sxs-lookup"><span data-stu-id="94017-171">Separate profiles</span></span>

<span data-ttu-id="94017-172">Ein PowerShell-Profil ist ein Skript, das beim Start von PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="94017-172">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="94017-173">Dieses Skript passt Ihre Umgebung durch Hinzufügen von Befehlen, Aliasen, Funktionen, Variablen, Modulen und PowerShell-Laufwerken an.</span><span class="sxs-lookup"><span data-stu-id="94017-173">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="94017-174">Das Profilskript stellt diese Anpassungen in jeder Sitzung zur Verfügung, ohne dass sie manuell neu erstellt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="94017-174">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="94017-175">Der Pfad zum Speicherort des Profils hat sich in PowerShell 7 geändert.</span><span class="sxs-lookup"><span data-stu-id="94017-175">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="94017-176">In Windows PowerShell 5.1 lautet der Speicherort des Profils `$HOME\Documents\WindowsPowerShell`.</span><span class="sxs-lookup"><span data-stu-id="94017-176">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="94017-177">In PowerShell 7 lautet der Speicherort des Profils `$HOME\Documents\PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="94017-177">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="94017-178">Die Profildateinamen wurden ebenfalls geändert:</span><span class="sxs-lookup"><span data-stu-id="94017-178">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="94017-179">Weitere Informationen finden Sie unter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="94017-179">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="94017-180">Kompatibilität von PowerShell 7 mit Windows PowerShell 5.1-Modulen</span><span class="sxs-lookup"><span data-stu-id="94017-180">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="94017-181">Die meisten Module, die Sie in Windows PowerShell 5.1 verwenden, funktionieren bereits mit PowerShell 7, einschließlich Azure PowerShell und Active Directory.</span><span class="sxs-lookup"><span data-stu-id="94017-181">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="94017-182">Wir arbeiten weiterhin mit anderen Teams zusammen, um native PowerShell 7-Unterstützung für weitere Module wie Microsoft Graph, Office 365 und andere hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="94017-182">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="94017-183">Die aktuelle Liste der unterstützten Module finden Sie unter [Kompatibilität von PowerShell 7-Modulen](/powershell/scripting/whats-new/module-compatibility).</span><span class="sxs-lookup"><span data-stu-id="94017-183">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

> [!NOTE]
> <span data-ttu-id="94017-184">Unter Windows haben wir außerdem den Schalter **UseWindowsPowerShell** zu `Import-Module` hinzugefügt, um Benutzern mit inkompatiblen Modulen den Umstieg auf PowerShell 7 zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="94017-184">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="94017-185">Weitere Informationen zu dieser Funktionalität finden Sie unter [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span><span class="sxs-lookup"><span data-stu-id="94017-185">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="94017-186">PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="94017-186">PowerShell Remoting</span></span>

<span data-ttu-id="94017-187">PowerShell-Remoting ermöglicht Ihnen, jeden Windows PowerShell-Befehl auf einem oder mehreren Remotecomputern ausführen.</span><span class="sxs-lookup"><span data-stu-id="94017-187">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="94017-188">Sie können dauerhafte Verbindungen herstellen, interaktive Sitzungen starten und Skripts auf Remotecomputern ausführen.</span><span class="sxs-lookup"><span data-stu-id="94017-188">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="94017-189">WS-Management-Remoting</span><span class="sxs-lookup"><span data-stu-id="94017-189">WS-Management remoting</span></span>

<span data-ttu-id="94017-190">Bis Windows PowerShell 5.1 wird für die Verbindungsaushandlung und den Datentransport das WSMAN-Protokoll (WS-Management) verwendet.</span><span class="sxs-lookup"><span data-stu-id="94017-190">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="94017-191">WinRM (Windows Remote Management) verwendet das WSMAN-Protokoll.</span><span class="sxs-lookup"><span data-stu-id="94017-191">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="94017-192">Wenn WinRM aktiviert wurde, verwendet PowerShell 7 für Remoteverbindungen den vorhandenen Windows PowerShell 5.1-Endpunkt namens `Microsoft.PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="94017-192">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="94017-193">Um PowerShell 7 so zu aktualisieren, dass es seinen eigenen Endpunkt einbezieht, führen Sie das Cmdlet `Enable-PSRemoting` aus.</span><span class="sxs-lookup"><span data-stu-id="94017-193">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="94017-194">Informationen zum Herstellen einer Verbindung mit bestimmten Endpunkten finden Sie unter [WS-Management-Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="94017-194">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="94017-195">Um Windows PowerShell-Remoting zu verwenden, muss der Remotecomputer für die Remoteverwaltung konfiguriert sein.</span><span class="sxs-lookup"><span data-stu-id="94017-195">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="94017-196">Weitere Informationen und Anweisungen hierzu finden Sie unter [Informationen zu Remoteanforderungen](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="94017-196">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="94017-197">Weitere Informationen zum Arbeiten mit Remoteverbindungen finden Sie unter [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote) (Informationen zu Remotebefehlen).</span><span class="sxs-lookup"><span data-stu-id="94017-197">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="94017-198">SSH-basiertes Remoting</span><span class="sxs-lookup"><span data-stu-id="94017-198">SSH-based remoting</span></span>

<span data-ttu-id="94017-199">SSH-basiertes Remoting wurde in PowerShell 6.x hinzugefügt, um andere Betriebssysteme zu unterstützen, die keine nativen Windows-Komponenten wie **WinRM** verwenden können.</span><span class="sxs-lookup"><span data-stu-id="94017-199">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="94017-200">SSH-Remoting erstellt einen PowerShell-Hostprozess als SSH-Subsystem auf dem Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="94017-200">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="94017-201">Einzelheiten und Beispiele zum Einrichten von SSH-basiertem Remoting unter Windows und Linux finden Sie unter: [PowerShell-Remoting über SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="94017-201">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="94017-202">Der PowerShell-Katalog (PSGallery) enthält ein Modul und ein Cmdlet, mit dem SSH-basiertes Remoting automatisch konfiguriert kann.</span><span class="sxs-lookup"><span data-stu-id="94017-202">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="94017-203">Laden Sie das Modul `Microsoft.PowerShell.RemotingTools` aus [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) herunter, installieren Sie es, und führen Sie das Cmdlet `Enable-SSH` aus.</span><span class="sxs-lookup"><span data-stu-id="94017-203">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="94017-204">Die Cmdlets `New-PSSession`, `Enter-PSSession` und `Invoke-Command` weisen neue Parametersätze zur Unterstützung von SSH-Verbindungen auf.</span><span class="sxs-lookup"><span data-stu-id="94017-204">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="94017-205">Um eine Remotesitzung zu erstellen, geben Sie den Zielcomputer mit dem Parameter **HostName**an, und fügen Sie mit **UserName** den Benutzernamen hinzu.</span><span class="sxs-lookup"><span data-stu-id="94017-205">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="94017-206">Wenn Sie die Cmdlets interaktiv ausführen, werden Sie zur Kennworteingabe aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="94017-206">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="94017-207">Wenn Sie den Parameter **HostName** verwenden, geben Sie alternativ die Informationen zum Benutzernamen gefolgt vom At-Zeichen (@) und Computernamen an.</span><span class="sxs-lookup"><span data-stu-id="94017-207">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign ('@'), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="94017-208">Sie können die SSH-Schlüsselauthentifizierung auch mithilfe einer privaten Schlüsseldatei und des Parameters **KeyFilePath** einrichten.</span><span class="sxs-lookup"><span data-stu-id="94017-208">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="94017-209">Weitere Informationen finden Sie unter [OpenSSH-Schlüsselverwaltung](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="94017-209">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="94017-210">Unterstützung von Gruppenrichtlinien</span><span class="sxs-lookup"><span data-stu-id="94017-210">Group Policy supported</span></span>

<span data-ttu-id="94017-211">PowerShell enthält Gruppenrichtlinieneinstellungen, die Ihnen helfen, einheitliche Optionswerte für Server in einer Unternehmensumgebung festzulegen.</span><span class="sxs-lookup"><span data-stu-id="94017-211">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="94017-212">Dazu gehören folgende Einstellungen:</span><span class="sxs-lookup"><span data-stu-id="94017-212">These settings include:</span></span>

- <span data-ttu-id="94017-213">Konfiguration der Konsolensitzung: Legt einen Konfigurationsendpunkt fest, an dem PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="94017-213">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="94017-214">Modulprotokollierung aktivieren: Legt die Eigenschaft LogPipelineExecutionDetails von Modulen fest.</span><span class="sxs-lookup"><span data-stu-id="94017-214">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="94017-215">Protokollierung von PowerShell-Skriptblöcken: Aktiviert die ausführliche Protokollierung aller PowerShell-Skripts.</span><span class="sxs-lookup"><span data-stu-id="94017-215">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="94017-216">Skriptausführung aktivieren: Legt die PowerShell-Ausführungsrichtlinie fest.</span><span class="sxs-lookup"><span data-stu-id="94017-216">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="94017-217">PowerShell-Aufzeichnung aktivieren: ermöglicht die Erfassung der Ein- und Ausgabe von PowerShell-Befehlen in textbasierten Transkripten.</span><span class="sxs-lookup"><span data-stu-id="94017-217">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="94017-218">Standardquellpfad für "Update-Help" festlegen: Legt die Quelle für die aktualisierbare Hilfe auf ein Verzeichnis und nicht auf das Internet fest.</span><span class="sxs-lookup"><span data-stu-id="94017-218">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="94017-219">Weitere Informationen finden Sie unter [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span><span class="sxs-lookup"><span data-stu-id="94017-219">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="94017-220">PowerShell 7 bietet Gruppenrichtlinienvorlagen und in `$PSHOME` ein Installationsskript.</span><span class="sxs-lookup"><span data-stu-id="94017-220">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="94017-221">Gruppenrichtlinientools verwenden administrative Vorlagendateien (`.admx`, `.adml`), um Richtlinieneinstellungen auf der Benutzeroberfläche aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="94017-221">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="94017-222">Dies ermöglicht Administratoren die Verwaltung registrierungsbasierter Richtlinieneinstellungen.</span><span class="sxs-lookup"><span data-stu-id="94017-222">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="94017-223">Das Skript `InstallPSCorePolicyDefinitions.ps1` installiert administrative PowerShell Core-Vorlagen auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="94017-223">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a><span data-ttu-id="94017-224">Getrennte Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="94017-224">Separate Event Logs</span></span>

<span data-ttu-id="94017-225">Windows PowerShell und PowerShell 7 protokollieren Ereignisse in getrennten Ereignisprotokollen.</span><span class="sxs-lookup"><span data-stu-id="94017-225">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="94017-226">Verwenden Sie den folgenden Befehl, um eine Liste der PowerShell-Protokolle abzurufen.</span><span class="sxs-lookup"><span data-stu-id="94017-226">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="94017-227">Weitere Informationen finden Sie unter [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span><span class="sxs-lookup"><span data-stu-id="94017-227">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="94017-228">Verbesserte Bearbeitungsumgebung in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="94017-228">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="94017-229">[Visual Studio Code (VS Code)](https://code.visualstudio.com/) mit der [PowerShell-Erweiterung](https://code.visualstudio.com/docs/languages/powershell) ist die unterstützte Skriptumgebung für PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="94017-229">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="94017-230">Die Windows PowerShell Integrated Scripting Environment (ISE) unterstützt nur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94017-230">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="94017-231">Die aktualisierte PowerShell-Erweiterung umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="94017-231">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="94017-232">Neuen ISE-Kompatibilitätsmodus</span><span class="sxs-lookup"><span data-stu-id="94017-232">New ISE compatibility mode</span></span>
- <span data-ttu-id="94017-233">PSReadLine in der integrierten Konsole, einschließlich Syntaxhervorhebung, mehrzeilige Bearbeitung und Rückwärtssuche</span><span class="sxs-lookup"><span data-stu-id="94017-233">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="94017-234">Stabilitäts- und Leistungsverbesserungen</span><span class="sxs-lookup"><span data-stu-id="94017-234">Stability and performance improvements</span></span>
- <span data-ttu-id="94017-235">Neue CodeLens-Integration</span><span class="sxs-lookup"><span data-stu-id="94017-235">New CodeLens integration</span></span>
- <span data-ttu-id="94017-236">Verbesserte automatische Pfadvervollständigung</span><span class="sxs-lookup"><span data-stu-id="94017-236">Improved path auto-completion</span></span>

<span data-ttu-id="94017-237">Um den Umstieg auf Visual Studio Code zu erleichtern, verwenden Sie in der **Befehlspalette** die Funktion  **ISE-Modus aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="94017-237">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="94017-238">Über diese Option wird auf ein Layout im ISE-Stil umgestellt.</span><span class="sxs-lookup"><span data-stu-id="94017-238">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="94017-239">Das Layout im ISE-Stil bietet Ihnen alle neuen Features und Funktionen von PowerShell in einer vertrauten Benutzerumgebung.</span><span class="sxs-lookup"><span data-stu-id="94017-239">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="94017-240">Um auf das neue ISE-Layout umzustellen, drücken Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>, um die **Befehlspalette** zu öffnen. Geben Sie `PowerShell` ein, und wählen Sie **PowerShell: ISE-Modus aktivieren** aus.</span><span class="sxs-lookup"><span data-stu-id="94017-240">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="94017-241">Um das Layout auf das Originallayout festzulegen, öffnen Sie die **Befehlspalette**, und wählen Sie **PowerShell: ISE-Modus deaktivieren (Standard wiederherstellen)** aus.</span><span class="sxs-lookup"><span data-stu-id="94017-241">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="94017-242">Ausführliche Informationen zum Anpassen des Layouts von Visual Studio Code an ISE finden Sie unter [Replizieren der ISE-Benutzeroberfläche in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode).</span><span class="sxs-lookup"><span data-stu-id="94017-242">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="94017-243">Es ist nicht geplant, die ISE mit neuen Features zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="94017-243">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="94017-244">Die ISE ist jetzt in den neuesten Versionen von Windows 10 und Windows Server ein vom Benutzer deinstallierbares Feature.</span><span class="sxs-lookup"><span data-stu-id="94017-244">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="94017-245">Es ist nicht geplant, die ISE dauerhaft zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="94017-245">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="94017-246">Das PowerShell-Team und seine Partner konzentrieren sich auf die Verbesserung der Skripterstellung in der PowerShell-Erweiterung für Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="94017-246">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="94017-247">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="94017-247">Next Steps</span></span>

<span data-ttu-id="94017-248">Mit dem Wissen zur effektiven Migration jetzt [PowerShell 7 installieren](/powershell/scripting/install/installing-powershell-core-on-windows)!</span><span class="sxs-lookup"><span data-stu-id="94017-248">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
