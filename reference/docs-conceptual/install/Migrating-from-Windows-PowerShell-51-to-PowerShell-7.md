---
title: Migrieren von Windows PowerShell 5.1 zu PowerShell 7
description: Informationen zum Update von PowerShell 5.1 auf PowerShell 7 für Ihre Windows-Plattformen.
ms.date: 03/25/2020
ms.openlocfilehash: cb14a4f159b6dc33f31386da4264c0ebb640aef8
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809206"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a><span data-ttu-id="95ea8-103">Migrieren von Windows PowerShell 5.1 zu PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="95ea8-103">Migrating from Windows PowerShell 5.1 to PowerShell 7</span></span>

<span data-ttu-id="95ea8-104">PowerShell 7 wurde für Cloud-, lokale und Hybridumgebungen entwickelt und bietet Verbesserungen sowie [neue Features](../whats-new/What-s-New-in-PowerShell-70.md).</span><span class="sxs-lookup"><span data-stu-id="95ea8-104">Designed for cloud, on-premises, and hybrid environments, PowerShell 7 is packed with enhancements and [new features](../whats-new/What-s-New-in-PowerShell-70.md).</span></span>

- <span data-ttu-id="95ea8-105">Parallele Installation und Ausführung mit Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95ea8-105">Installs and runs side-by-side with Windows PowerShell</span></span>
- <span data-ttu-id="95ea8-106">Verbesserte Kompatibilität mit vorhandenen Windows PowerShell-Modulen</span><span class="sxs-lookup"><span data-stu-id="95ea8-106">Improved compatibility with existing Windows PowerShell modules</span></span>
- <span data-ttu-id="95ea8-107">Neue Sprachfeatures wie ternäre Operatoren und `ForEach-Object -Parallel`</span><span class="sxs-lookup"><span data-stu-id="95ea8-107">New language features, like ternary operators and `ForEach-Object -Parallel`</span></span>
- <span data-ttu-id="95ea8-108">Verbesserte Leistung</span><span class="sxs-lookup"><span data-stu-id="95ea8-108">Improved performance</span></span>
- <span data-ttu-id="95ea8-109">SSH-basiertes Remoting</span><span class="sxs-lookup"><span data-stu-id="95ea8-109">SSH-based remoting</span></span>
- <span data-ttu-id="95ea8-110">Plattformübergreifende Interoperabilität</span><span class="sxs-lookup"><span data-stu-id="95ea8-110">Cross-platform interoperability</span></span>
- <span data-ttu-id="95ea8-111">Unterstützung für Docker-Container</span><span class="sxs-lookup"><span data-stu-id="95ea8-111">Support for Docker containers</span></span>

<span data-ttu-id="95ea8-112">PowerShell 7 funktioniert parallel mit Windows PowerShell, sodass Sie Editionen vor der Bereitstellung problemlos testen und vergleichen können.</span><span class="sxs-lookup"><span data-stu-id="95ea8-112">PowerShell 7 works side-by-side with Windows PowerShell letting you easily test and compare between editions before deployment.</span></span> <span data-ttu-id="95ea8-113">Die Migration erfolgt einfach, schnell und betriebssicher</span><span class="sxs-lookup"><span data-stu-id="95ea8-113">Migration is simple, quick, and safe.</span></span>

<span data-ttu-id="95ea8-114">Die folgenden Windows-Betriebssysteme unterstützen PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="95ea8-114">PowerShell 7 is supported on the following Windows operating systems:</span></span>

- <span data-ttu-id="95ea8-115">Windows 8.1 und 10</span><span class="sxs-lookup"><span data-stu-id="95ea8-115">Windows 8.1 and 10</span></span>
- <span data-ttu-id="95ea8-116">Windows Server 2012, 2012 R2, 2016, und 2019</span><span class="sxs-lookup"><span data-stu-id="95ea8-116">Windows Server 2012, 2012 R2, 2016, and 2019</span></span>

<span data-ttu-id="95ea8-117">PowerShell 7 lässt sich auch unter macOS und mehreren Linux-Distributionen ausführen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-117">PowerShell 7 also runs on macOS and several Linux distributions.</span></span> <span data-ttu-id="95ea8-118">Eine Liste der unterstützten Betriebssysteme und Informationen zum Supportlebenszyklus finden Sie unter [PowerShell-Supportlebenszyklus](/powershell/scripting/powershell-support-lifecycle).</span><span class="sxs-lookup"><span data-stu-id="95ea8-118">For a list of supported operating systems and information about the support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

## <a name="installing-powershell-7"></a><span data-ttu-id="95ea8-119">Installieren von PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="95ea8-119">Installing PowerShell 7</span></span>

<span data-ttu-id="95ea8-120">Aus Gründen der Flexibilität und zur Unterstützung der Anforderungen von IT- und DevOps-Mitarbeitern sowie Entwicklern stehen mehrere Optionen zur Installation von PowerShell 7 zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="95ea8-120">For flexibility and to support the needs of IT, DevOps engineers, and developers, there are several options available to install PowerShell 7.</span></span> <span data-ttu-id="95ea8-121">In den meisten Fällen können die Installationsoptionen auf die folgenden reduziert werden:</span><span class="sxs-lookup"><span data-stu-id="95ea8-121">In most cases, the installation options can be reduced to the following methods:</span></span>

- <span data-ttu-id="95ea8-122">Bereitstellen von PowerShell mit dem [MSI-Paket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span><span class="sxs-lookup"><span data-stu-id="95ea8-122">Deploy PowerShell using the [MSI package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)</span></span>
- <span data-ttu-id="95ea8-123">Bereitstellen von PowerShell mit dem [ZIP-Paket](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span><span class="sxs-lookup"><span data-stu-id="95ea8-123">Deploy PowerShell using the [ZIP package](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)</span></span>

> [!NOTE]
> <span data-ttu-id="95ea8-124">Das MSI-Paket kann mit Verwaltungsprodukten wie [System Center Configuration Manager (SCCM)](/configmgr/apps/) bereitgestellt und aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="95ea8-124">The MSI package can be deployed and updated with management products such as [System Center Configuration Manager (SCCM)](/configmgr/apps/).</span></span> <span data-ttu-id="95ea8-125">Laden Sie die Pakete von der [GitHub-Seite „Releases“](https://github.com/PowerShell/PowerShell/releases) herunter.</span><span class="sxs-lookup"><span data-stu-id="95ea8-125">Download the packages from [GitHub Release page](https://github.com/PowerShell/PowerShell/releases).</span></span>

<span data-ttu-id="95ea8-126">Zum Bereitstellen des MSI-Pakets sind Administratorberechtigungen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="95ea8-126">Deploying the MSI package requires Administrator permission.</span></span> <span data-ttu-id="95ea8-127">Das ZIP-Paket kann von beliebigen Benutzern bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="95ea8-127">The ZIP package can be deployed by any user.</span></span> <span data-ttu-id="95ea8-128">Das ZIP-Paket ist die einfachste Möglichkeit, PowerShell 7 zum Testen zu installieren, bevor eine vollständige Installation erfolgt.</span><span class="sxs-lookup"><span data-stu-id="95ea8-128">The ZIP package is the easiest way to install PowerShell 7 for testing, before committing to a full installation.</span></span>

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a><span data-ttu-id="95ea8-129">Parallele Nutzung von PowerShell 7 mit Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="95ea8-129">Using PowerShell 7 side-by-side with Windows PowerShell 5.1</span></span>

<span data-ttu-id="95ea8-130">PowerShell 7 ist für die parallele Nutzung mit Windows PowerShell 5.1 konzipiert.</span><span class="sxs-lookup"><span data-stu-id="95ea8-130">PowerShell 7 is designed to coexist with Windows PowerShell 5.1.</span></span> <span data-ttu-id="95ea8-131">Die folgenden Features stellen sicher, dass Ihre Investition in PowerShell geschützt und die Migration zu PowerShell 7 einfach ist.</span><span class="sxs-lookup"><span data-stu-id="95ea8-131">The following features ensure that your investment in PowerShell is protected and your migration to PowerShell 7 is simple.</span></span>

- <span data-ttu-id="95ea8-132">Trennung von Installationspfad und Namen der ausführbaren Datei</span><span class="sxs-lookup"><span data-stu-id="95ea8-132">Separate installation path and executable name</span></span>
- <span data-ttu-id="95ea8-133">Trennung von PSModulePath</span><span class="sxs-lookup"><span data-stu-id="95ea8-133">Separate PSModulePath</span></span>
- <span data-ttu-id="95ea8-134">Getrennte Profile für jede Version</span><span class="sxs-lookup"><span data-stu-id="95ea8-134">Separate profiles for each version</span></span>
- <span data-ttu-id="95ea8-135">Verbesserte Modulkompatibilität</span><span class="sxs-lookup"><span data-stu-id="95ea8-135">Improved module compatibility</span></span>
- <span data-ttu-id="95ea8-136">Neue Remoting-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="95ea8-136">New remoting endpoints</span></span>
- <span data-ttu-id="95ea8-137">Unterstützung von Gruppenrichtlinien</span><span class="sxs-lookup"><span data-stu-id="95ea8-137">Group policy support</span></span>
- <span data-ttu-id="95ea8-138">Getrennte Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="95ea8-138">Separate Event logs</span></span>

### <a name="separate-installation-path-and-executable-name"></a><span data-ttu-id="95ea8-139">Trennung von Installationspfad und Namen der ausführbaren Datei</span><span class="sxs-lookup"><span data-stu-id="95ea8-139">Separate installation path and executable name</span></span>

<span data-ttu-id="95ea8-140">PowerShell 7 wird in ein neues Verzeichnis installiert und ermöglicht die parallele Ausführung mit Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="95ea8-140">PowerShell 7 installs to a new directory, enabling side-by-side execution with Windows PowerShell 5.1.</span></span>

<span data-ttu-id="95ea8-141">Installationsspeicherorte nach Version:</span><span class="sxs-lookup"><span data-stu-id="95ea8-141">Install locations by version:</span></span>

- <span data-ttu-id="95ea8-142">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span><span class="sxs-lookup"><span data-stu-id="95ea8-142">Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`</span></span>
- <span data-ttu-id="95ea8-143">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span><span class="sxs-lookup"><span data-stu-id="95ea8-143">PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`</span></span>
- <span data-ttu-id="95ea8-144">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="95ea8-144">PowerShell 7: `$env:ProgramFiles\PowerShell\7`</span></span>

<span data-ttu-id="95ea8-145">Der neue Speicherort wird Ihrer Umgebungsvariablen PATH hinzugefügt, sodass Sie sowohl Windows PowerShell 5.1 als auch PowerShell 7 ausführen können.</span><span class="sxs-lookup"><span data-stu-id="95ea8-145">The new location is added to your PATH allowing you to run both Windows PowerShell 5.1 and PowerShell 7.</span></span> <span data-ttu-id="95ea8-146">Wenn Sie von PowerShell Core 6.x zu PowerShell 7 migrieren, wird PowerShell 6 entfernt und PATH ersetzt.</span><span class="sxs-lookup"><span data-stu-id="95ea8-146">If you're migrating from PowerShell Core 6.x to PowerShell 7, PowerShell 6 is removed and the PATH replaced.</span></span>

<span data-ttu-id="95ea8-147">In Windows PowerShell heißt die ausführbare Datei `powershell.exe`.</span><span class="sxs-lookup"><span data-stu-id="95ea8-147">In Windows PowerShell, the PowerShell executable is named `powershell.exe`.</span></span> <span data-ttu-id="95ea8-148">Ab Version 6 heißt die ausführbare Datei `pwsh.exe`.</span><span class="sxs-lookup"><span data-stu-id="95ea8-148">In version 6 and above, the executable is named `pwsh.exe`.</span></span> <span data-ttu-id="95ea8-149">Der neue Name vereinfacht die parallele Ausführung beider Versionen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-149">The new name makes it easy to support side-by-side execution of both versions.</span></span>

### <a name="separate-psmodulepath"></a><span data-ttu-id="95ea8-150">Trennung von PSModulePath</span><span class="sxs-lookup"><span data-stu-id="95ea8-150">Separate PSModulePath</span></span>

<span data-ttu-id="95ea8-151">Standardmäßig werden Module in Windows PowerShell und PowerShell 7 an verschiedenen Speicherorten gespeichert.</span><span class="sxs-lookup"><span data-stu-id="95ea8-151">By default, Windows PowerShell and PowerShell 7 store modules in different locations.</span></span> <span data-ttu-id="95ea8-152">PowerShell 7 kombiniert diese Speicherorte in der Umgebungsvariablen `$Env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="95ea8-152">PowerShell 7 combines those locations in the `$Env:PSModulePath` environment variable.</span></span> <span data-ttu-id="95ea8-153">Wenn Sie ein Modul nach Name importieren, prüft PowerShell den von `$Env:PSModulePath` angegebenen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="95ea8-153">When importing a module by name, PowerShell checks the location specified by `$Env:PSModulePath`.</span></span> <span data-ttu-id="95ea8-154">Dies ermöglicht PowerShell 7 das Laden von Core- und Desktop-Modulen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-154">This allows PowerShell 7 to load both Core and Desktop modules.</span></span>

|            <span data-ttu-id="95ea8-155">Installationsumfang</span><span class="sxs-lookup"><span data-stu-id="95ea8-155">Install Scope</span></span>            |                <span data-ttu-id="95ea8-156">Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="95ea8-156">Windows PowerShell 5.1</span></span>                 |             <span data-ttu-id="95ea8-157">PowerShell 7.0</span><span class="sxs-lookup"><span data-stu-id="95ea8-157">PowerShell 7.0</span></span>             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="95ea8-158">PowerShell-Module</span><span class="sxs-lookup"><span data-stu-id="95ea8-158">PowerShell modules</span></span>                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| <span data-ttu-id="95ea8-159">Vom Benutzer installierter</span><span class="sxs-lookup"><span data-stu-id="95ea8-159">User installed</span></span><br><span data-ttu-id="95ea8-160">Geltungsbereich AllUsers</span><span class="sxs-lookup"><span data-stu-id="95ea8-160">AllUsers scope</span></span>    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| <span data-ttu-id="95ea8-161">Vom Benutzer installierter</span><span class="sxs-lookup"><span data-stu-id="95ea8-161">User installed</span></span><br><span data-ttu-id="95ea8-162">Geltungsbereich CurrentUser</span><span class="sxs-lookup"><span data-stu-id="95ea8-162">CurrentUser scope</span></span> | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

<span data-ttu-id="95ea8-163">In den folgenden Beispielen sind die Standardwerte von `$Env:PSModulePath` für jede Version angegeben.</span><span class="sxs-lookup"><span data-stu-id="95ea8-163">The following examples show the default values of `$Env:PSModulePath` for each version.</span></span>

- <span data-ttu-id="95ea8-164">Windows PowerShell 5.1:</span><span class="sxs-lookup"><span data-stu-id="95ea8-164">For Windows PowerShell 5.1:</span></span>

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- <span data-ttu-id="95ea8-165">PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="95ea8-165">For PowerShell 7:</span></span>

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

<span data-ttu-id="95ea8-166">Beachten Sie, dass PowerShell 7 die Windows PowerShell-Pfade und die PowerShell 7-Pfade enthält, um das automatische Laden von Modulen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-166">Notice that PowerShell 7 includes the Windows PowerShell paths and the PowerShell 7 paths to provide autoloading of modules.</span></span>

> [!NOTE]
> <span data-ttu-id="95ea8-167">Zusätzliche Pfade sind möglicherweise vorhanden, wenn Sie die Umgebungsvariable PSModulePath geändert oder benutzerdefinierte Module oder Anwendungen installiert haben.</span><span class="sxs-lookup"><span data-stu-id="95ea8-167">Additional paths may exist if you have changed the PSModulePath environment variable or installed custom modules or applications.</span></span>

<span data-ttu-id="95ea8-168">Weitere Informationen finden Sie unter [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences) in `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="95ea8-168">For more information, see `PSModulePath` in [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).</span></span>

<span data-ttu-id="95ea8-169">Weitere Informationen zu Modulen finden Sie unter [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span><span class="sxs-lookup"><span data-stu-id="95ea8-169">For more information about Modules, see [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).</span></span>

### <a name="separate-profiles"></a><span data-ttu-id="95ea8-170">Getrennte Profile</span><span class="sxs-lookup"><span data-stu-id="95ea8-170">Separate profiles</span></span>

<span data-ttu-id="95ea8-171">Ein PowerShell-Profil ist ein Skript, das beim Start von PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="95ea8-171">A PowerShell profile is a script that executes when PowerShell starts.</span></span> <span data-ttu-id="95ea8-172">Dieses Skript passt Ihre Umgebung durch Hinzufügen von Befehlen, Aliasen, Funktionen, Variablen, Modulen und PowerShell-Laufwerken an.</span><span class="sxs-lookup"><span data-stu-id="95ea8-172">This script customizes your environment by adding commands, aliases, functions, variables, modules, and PowerShell drives.</span></span> <span data-ttu-id="95ea8-173">Das Profilskript stellt diese Anpassungen in jeder Sitzung zur Verfügung, ohne dass sie manuell neu erstellt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-173">The profile script makes these customizations available in every session without having to manually recreate them.</span></span>

<span data-ttu-id="95ea8-174">Der Pfad zum Speicherort des Profils hat sich in PowerShell 7 geändert.</span><span class="sxs-lookup"><span data-stu-id="95ea8-174">The path to the location of the profile has changed in PowerShell 7.</span></span>

- <span data-ttu-id="95ea8-175">In Windows PowerShell 5.1 lautet der Speicherort des Profils `$HOME\Documents\WindowsPowerShell`.</span><span class="sxs-lookup"><span data-stu-id="95ea8-175">In Windows PowerShell 5.1, the location of the profile is `$HOME\Documents\WindowsPowerShell`.</span></span>
- <span data-ttu-id="95ea8-176">In PowerShell 7 lautet der Speicherort des Profils `$HOME\Documents\PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="95ea8-176">In PowerShell 7, the location of the profile is `$HOME\Documents\PowerShell`.</span></span>

<span data-ttu-id="95ea8-177">Die Profildateinamen wurden ebenfalls geändert:</span><span class="sxs-lookup"><span data-stu-id="95ea8-177">The profile filenames have also changed:</span></span>

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

<span data-ttu-id="95ea8-178">Weitere Informationen finden Sie unter [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="95ea8-178">For more information [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a><span data-ttu-id="95ea8-179">Kompatibilität von PowerShell 7 mit Windows PowerShell 5.1-Modulen</span><span class="sxs-lookup"><span data-stu-id="95ea8-179">PowerShell 7 compatibility with Windows PowerShell 5.1 modules</span></span>

<span data-ttu-id="95ea8-180">Die meisten Module, die Sie in Windows PowerShell 5.1 verwenden, funktionieren bereits mit PowerShell 7, einschließlich Azure PowerShell und Active Directory.</span><span class="sxs-lookup"><span data-stu-id="95ea8-180">Most of the modules you use in Windows PowerShell 5.1 already work with PowerShell 7, including Azure PowerShell and Active Directory.</span></span> <span data-ttu-id="95ea8-181">Wir arbeiten weiterhin mit anderen Teams zusammen, um native PowerShell 7-Unterstützung für weitere Module wie Microsoft Graph, Office 365 und andere hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-181">We're continuing to work with other teams to add native PowerShell 7 support for more modules including Microsoft Graph, Office 365, and others.</span></span> <span data-ttu-id="95ea8-182">Die aktuelle Liste der unterstützten Module finden Sie unter [Kompatibilität von PowerShell 7-Modulen](/powershell/scripting/whats-new/module-compatibility).</span><span class="sxs-lookup"><span data-stu-id="95ea8-182">For the current list of supported modules, see [PowerShell 7 module compatibility](/powershell/scripting/whats-new/module-compatibility).</span></span>

> [!NOTE]
> <span data-ttu-id="95ea8-183">Unter Windows haben wir außerdem den Schalter **UseWindowsPowerShell** zu `Import-Module` hinzugefügt, um Benutzern mit inkompatiblen Modulen den Umstieg auf PowerShell 7 zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="95ea8-183">On Windows, we've also added a **UseWindowsPowerShell** switch to `Import-Module` to ease the transition to PowerShell 7 for those using incompatible modules.</span></span> <span data-ttu-id="95ea8-184">Weitere Informationen zu dieser Funktionalität finden Sie unter [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span><span class="sxs-lookup"><span data-stu-id="95ea8-184">For more information on this functionality, see [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).</span></span>

### <a name="powershell-remoting"></a><span data-ttu-id="95ea8-185">PowerShell-Remoting</span><span class="sxs-lookup"><span data-stu-id="95ea8-185">PowerShell Remoting</span></span>

<span data-ttu-id="95ea8-186">PowerShell-Remoting ermöglicht Ihnen, jeden Windows PowerShell-Befehl auf einem oder mehreren Remotecomputern ausführen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-186">PowerShell remoting lets you run any PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="95ea8-187">Sie können dauerhafte Verbindungen herstellen, interaktive Sitzungen starten und Skripts auf Remotecomputern ausführen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-187">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

#### <a name="ws-management-remoting"></a><span data-ttu-id="95ea8-188">WS-Management-Remoting</span><span class="sxs-lookup"><span data-stu-id="95ea8-188">WS-Management remoting</span></span>

<span data-ttu-id="95ea8-189">Bis Windows PowerShell 5.1 wird für die Verbindungsaushandlung und den Datentransport das WSMAN-Protokoll (WS-Management) verwendet.</span><span class="sxs-lookup"><span data-stu-id="95ea8-189">Windows PowerShell 5.1 and below use the WS-Management (WSMAN) protocol for connection negotiation and data transport.</span></span> <span data-ttu-id="95ea8-190">WinRM (Windows Remote Management) verwendet das WSMAN-Protokoll.</span><span class="sxs-lookup"><span data-stu-id="95ea8-190">Windows Remote Management (WinRM) uses the WSMAN protocol.</span></span> <span data-ttu-id="95ea8-191">Wenn WinRM aktiviert wurde, verwendet PowerShell 7 für Remoteverbindungen den vorhandenen Windows PowerShell 5.1-Endpunkt namens `Microsoft.PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="95ea8-191">If WinRM has been enabled, PowerShell 7 uses the existing Windows PowerShell 5.1 endpoint named `Microsoft.PowerShell` for remoting connections.</span></span> <span data-ttu-id="95ea8-192">Um PowerShell 7 so zu aktualisieren, dass es seinen eigenen Endpunkt einbezieht, führen Sie das Cmdlet `Enable-PSRemoting` aus.</span><span class="sxs-lookup"><span data-stu-id="95ea8-192">To update PowerShell 7 to include its own endpoint, run the `Enable-PSRemoting` cmdlet.</span></span> <span data-ttu-id="95ea8-193">Informationen zum Herstellen einer Verbindung mit bestimmten Endpunkten finden Sie unter [WS-Management-Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="95ea8-193">For information about connecting to specific endpoints, see [WS-Management Remoting in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)</span></span>

<span data-ttu-id="95ea8-194">Um Windows PowerShell-Remoting zu verwenden, muss der Remotecomputer für die Remoteverwaltung konfiguriert sein.</span><span class="sxs-lookup"><span data-stu-id="95ea8-194">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="95ea8-195">Weitere Informationen und Anweisungen hierzu finden Sie unter [Informationen zu Remoteanforderungen](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span><span class="sxs-lookup"><span data-stu-id="95ea8-195">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="95ea8-196">Weitere Informationen zum Arbeiten mit Remoteverbindungen finden Sie unter [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote) (Informationen zu Remotebefehlen).</span><span class="sxs-lookup"><span data-stu-id="95ea8-196">For more information about working with remoting, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote)</span></span>

#### <a name="ssh-based-remoting"></a><span data-ttu-id="95ea8-197">SSH-basiertes Remoting</span><span class="sxs-lookup"><span data-stu-id="95ea8-197">SSH-based remoting</span></span>

<span data-ttu-id="95ea8-198">SSH-basiertes Remoting wurde in PowerShell 6.x hinzugefügt, um andere Betriebssysteme zu unterstützen, die keine nativen Windows-Komponenten wie **WinRM** verwenden können.</span><span class="sxs-lookup"><span data-stu-id="95ea8-198">SSH-based remoting was added in PowerShell Core 6.x to support other operating systems that can't use Windows native components like **WinRM**.</span></span> <span data-ttu-id="95ea8-199">SSH-Remoting erstellt einen PowerShell-Hostprozess als SSH-Subsystem auf dem Zielcomputer.</span><span class="sxs-lookup"><span data-stu-id="95ea8-199">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="95ea8-200">Einzelheiten und Beispiele zum Einrichten von SSH-basiertem Remoting unter Windows und Linux finden Sie unter: [PowerShell-Remoting über SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span><span class="sxs-lookup"><span data-stu-id="95ea8-200">For details and examples on setting up SSH-based remoting on Windows or Linux, see: [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

> [!NOTE]
> <span data-ttu-id="95ea8-201">Der PowerShell-Katalog (PSGallery) enthält ein Modul und ein Cmdlet, mit dem SSH-basiertes Remoting automatisch konfiguriert kann.</span><span class="sxs-lookup"><span data-stu-id="95ea8-201">The PowerShell Gallery (PSGallery) contains a module and cmdlet that automatically configures SSH-based remoting.</span></span> <span data-ttu-id="95ea8-202">Laden Sie das Modul `Microsoft.PowerShell.RemotingTools` aus [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) herunter, installieren Sie es, und führen Sie das Cmdlet `Enable-SSH` aus.</span><span class="sxs-lookup"><span data-stu-id="95ea8-202">Install the `Microsoft.PowerShell.RemotingTools` module from the [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) and run the `Enable-SSH` cmdlet.</span></span>

<span data-ttu-id="95ea8-203">Die Cmdlets `New-PSSession`, `Enter-PSSession` und `Invoke-Command` weisen neue Parametersätze zur Unterstützung von SSH-Verbindungen auf.</span><span class="sxs-lookup"><span data-stu-id="95ea8-203">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets have new parameter sets to support SSH connections.</span></span>

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="95ea8-204">Um eine Remotesitzung zu erstellen, geben Sie den Zielcomputer mit dem Parameter **HostName**an, und fügen Sie mit **UserName** den Benutzernamen hinzu.</span><span class="sxs-lookup"><span data-stu-id="95ea8-204">To create a remote session, specify the target computer with the **HostName** parameter and provide the user name with **UserName**.</span></span> <span data-ttu-id="95ea8-205">Wenn Sie die Cmdlets interaktiv ausführen, werden Sie zur Kennworteingabe aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="95ea8-205">When running the cmdlets interactively, you're prompted for a password.</span></span>

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

<span data-ttu-id="95ea8-206">Wenn Sie den Parameter **HostName** verwenden, geben Sie alternativ die Informationen zum Benutzernamen gefolgt vom At-Zeichen (`@`) und Computernamen an.</span><span class="sxs-lookup"><span data-stu-id="95ea8-206">Alternatively, when using the **HostName** parameter, provide the username information followed by the at sign (`@`), followed by the computer name.</span></span>

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

<span data-ttu-id="95ea8-207">Sie können die SSH-Schlüsselauthentifizierung auch mithilfe einer privaten Schlüsseldatei und des Parameters **KeyFilePath** einrichten.</span><span class="sxs-lookup"><span data-stu-id="95ea8-207">You may set up SSH key authentication using a private key file with the **KeyFilePath** parameter.</span></span>
<span data-ttu-id="95ea8-208">Weitere Informationen finden Sie unter [OpenSSH-Schlüsselverwaltung](/windows-server/administration/openssh/openssh_keymanagement).</span><span class="sxs-lookup"><span data-stu-id="95ea8-208">For more information, see [OpenSSH Key Management](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

### <a name="group-policy-supported"></a><span data-ttu-id="95ea8-209">Unterstützung von Gruppenrichtlinien</span><span class="sxs-lookup"><span data-stu-id="95ea8-209">Group Policy supported</span></span>

<span data-ttu-id="95ea8-210">PowerShell enthält Gruppenrichtlinieneinstellungen, die Ihnen helfen, einheitliche Optionswerte für Server in einer Unternehmensumgebung festzulegen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-210">PowerShell includes Group Policy settings to help you define consistent option values for servers in an enterprise environment.</span></span> <span data-ttu-id="95ea8-211">Dies umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="95ea8-211">These settings include:</span></span>

- <span data-ttu-id="95ea8-212">Konfiguration der Konsolensitzung: Legt einen Konfigurationsendpunkt fest, an dem PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="95ea8-212">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="95ea8-213">Modulprotokollierung aktivieren: Legt die Eigenschaft LogPipelineExecutionDetails von Modulen fest.</span><span class="sxs-lookup"><span data-stu-id="95ea8-213">Turn on Module Logging: Sets the LogPipelineExecutionDetails property of modules.</span></span>
- <span data-ttu-id="95ea8-214">Protokollierung von PowerShell-Skriptblöcken: Aktiviert die ausführliche Protokollierung aller PowerShell-Skripts.</span><span class="sxs-lookup"><span data-stu-id="95ea8-214">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="95ea8-215">Skriptausführung aktivieren: Legt die PowerShell-Ausführungsrichtlinie fest.</span><span class="sxs-lookup"><span data-stu-id="95ea8-215">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="95ea8-216">PowerShell-Aufzeichnung aktivieren: ermöglicht die Erfassung der Ein- und Ausgabe von PowerShell-Befehlen in textbasierten Transkripten.</span><span class="sxs-lookup"><span data-stu-id="95ea8-216">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="95ea8-217">Standardquellpfad für "Update-Help" festlegen: Legt die Quelle für die aktualisierbare Hilfe auf ein Verzeichnis und nicht auf das Internet fest.</span><span class="sxs-lookup"><span data-stu-id="95ea8-217">Set the default source path for Update-Help: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="95ea8-218">Weitere Informationen finden Sie unter [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span><span class="sxs-lookup"><span data-stu-id="95ea8-218">For more information, see [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).</span></span>

<span data-ttu-id="95ea8-219">PowerShell 7 bietet Gruppenrichtlinienvorlagen und in `$PSHOME` ein Installationsskript.</span><span class="sxs-lookup"><span data-stu-id="95ea8-219">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="95ea8-220">Gruppenrichtlinientools verwenden administrative Vorlagendateien (`.admx`, `.adml`), um Richtlinieneinstellungen auf der Benutzeroberfläche aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-220">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="95ea8-221">Dies ermöglicht Administratoren die Verwaltung registrierungsbasierter Richtlinieneinstellungen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-221">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="95ea8-222">Das Skript `InstallPSCorePolicyDefinitions.ps1` installiert administrative PowerShell Core-Vorlagen auf dem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="95ea8-222">The `InstallPSCorePolicyDefinitions.ps1` script installs PowerShell Core Administrative Templates on the local machine.</span></span>

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

### <a name="separate-event-logs"></a><span data-ttu-id="95ea8-223">Getrennte Ereignisprotokolle</span><span class="sxs-lookup"><span data-stu-id="95ea8-223">Separate Event Logs</span></span>

<span data-ttu-id="95ea8-224">Windows PowerShell und PowerShell 7 protokollieren Ereignisse in getrennten Ereignisprotokollen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-224">Windows PowerShell and PowerShell 7 log events to separate event logs.</span></span> <span data-ttu-id="95ea8-225">Verwenden Sie den folgenden Befehl, um eine Liste der PowerShell-Protokolle abzurufen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-225">Use the following command to get a list of the PowerShell logs.</span></span>

```powershell
Get-WinEvent -ListLog *PowerShell*
```

<span data-ttu-id="95ea8-226">Weitere Informationen finden Sie unter [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span><span class="sxs-lookup"><span data-stu-id="95ea8-226">For more information, see [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).</span></span>

## <a name="improved-editing-experience-with-visual-studio-code"></a><span data-ttu-id="95ea8-227">Verbesserte Bearbeitungsumgebung in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="95ea8-227">Improved editing experience with Visual Studio Code</span></span>

<span data-ttu-id="95ea8-228">[Visual Studio Code (VS Code)](https://code.visualstudio.com/) mit der [PowerShell-Erweiterung](https://code.visualstudio.com/docs/languages/powershell) ist die unterstützte Skriptumgebung für PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="95ea8-228">[Visual Studio Code (VSCode)](https://code.visualstudio.com/) with the [PowerShell Extension](https://code.visualstudio.com/docs/languages/powershell) is the supported scripting environment for PowerShell 7.</span></span> <span data-ttu-id="95ea8-229">Die Windows PowerShell Integrated Scripting Environment (ISE) unterstützt nur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95ea8-229">The Windows PowerShell Integrated Scripting Environment (ISE) only supports Windows PowerShell.</span></span>

<span data-ttu-id="95ea8-230">Die aktualisierte PowerShell-Erweiterung umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="95ea8-230">The updated PowerShell extension includes:</span></span>

- <span data-ttu-id="95ea8-231">Neuen ISE-Kompatibilitätsmodus</span><span class="sxs-lookup"><span data-stu-id="95ea8-231">New ISE compatibility mode</span></span>
- <span data-ttu-id="95ea8-232">PSReadLine in der integrierten Konsole, einschließlich Syntaxhervorhebung, mehrzeilige Bearbeitung und Rückwärtssuche</span><span class="sxs-lookup"><span data-stu-id="95ea8-232">PSReadLine in the Integrated Console, including syntax highlighting, multi-line editing, and back search</span></span>
- <span data-ttu-id="95ea8-233">Stabilitäts- und Leistungsverbesserungen</span><span class="sxs-lookup"><span data-stu-id="95ea8-233">Stability and performance improvements</span></span>
- <span data-ttu-id="95ea8-234">Neue CodeLens-Integration</span><span class="sxs-lookup"><span data-stu-id="95ea8-234">New CodeLens integration</span></span>
- <span data-ttu-id="95ea8-235">Verbesserte automatische Pfadvervollständigung</span><span class="sxs-lookup"><span data-stu-id="95ea8-235">Improved path auto-completion</span></span>

<span data-ttu-id="95ea8-236">Um den Umstieg auf Visual Studio Code zu erleichtern, verwenden Sie in der **Befehlspalette** die Funktion \*\* ISE-Modus aktivieren\*\*.</span><span class="sxs-lookup"><span data-stu-id="95ea8-236">To make the transition to Visual Studio Code easier, use the **Enable ISE Mode** function available in the **Command Palette**.</span></span> <span data-ttu-id="95ea8-237">Über diese Option wird auf ein Layout im ISE-Stil umgestellt.</span><span class="sxs-lookup"><span data-stu-id="95ea8-237">This function switches VSCode into an ISE-style layout.</span></span> <span data-ttu-id="95ea8-238">Das Layout im ISE-Stil bietet Ihnen alle neuen Features und Funktionen von PowerShell in einer vertrauten Benutzerumgebung.</span><span class="sxs-lookup"><span data-stu-id="95ea8-238">The ISE-style layout gives you all the new features and capabilities of PowerShell in a familiar user experience.</span></span>

<span data-ttu-id="95ea8-239">Um auf das neue ISE-Layout umzustellen, drücken Sie <kbd>STRG</kbd>+<kbd>UMSCHALT</kbd>+<kbd>P</kbd>, um die **Befehlspalette** zu öffnen. Geben Sie `PowerShell` ein, und wählen Sie folgende Option aus: **PowerShell: ISE-Modus aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="95ea8-239">To switch to the new ISE layout, press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> to open the **Command Palette**, type `PowerShell` and select **PowerShell: Enable ISE Mode**.</span></span>

<span data-ttu-id="95ea8-240">Um das Layout auf das Originallayout festzulegen, öffnen Sie die **Befehlspalette**, und wählen Sie folgende Option aus: **PowerShell: ISE-Modus deaktivieren (Standard wiederherstellen)**.</span><span class="sxs-lookup"><span data-stu-id="95ea8-240">To set the layout to the original layout, open the **Command Palette**, select **PowerShell: Disable ISE Mode (restore to defaults)**.</span></span>

<span data-ttu-id="95ea8-241">Ausführliche Informationen zum Anpassen des Layouts von Visual Studio Code an ISE finden Sie unter [Replizieren der ISE-Benutzeroberfläche in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode).</span><span class="sxs-lookup"><span data-stu-id="95ea8-241">For details about customizing the VSCode layout to ISE, see [How to Replicate the ISE Experience in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)</span></span>

> [!NOTE]
> <span data-ttu-id="95ea8-242">Es ist nicht geplant, die ISE mit neuen Features zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="95ea8-242">There no plans to update the ISE with new features.</span></span> <span data-ttu-id="95ea8-243">Die ISE ist jetzt in den neuesten Versionen von Windows 10 und Windows Server ein vom Benutzer deinstallierbares Feature.</span><span class="sxs-lookup"><span data-stu-id="95ea8-243">The ISE is now a user-uninstallable feature in the latest versions of Windows 10 and Windows Server.</span></span> <span data-ttu-id="95ea8-244">Es ist nicht geplant, die ISE dauerhaft zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="95ea8-244">There are no plans to permanently remove the ISE.</span></span> <span data-ttu-id="95ea8-245">Das PowerShell-Team und seine Partner konzentrieren sich auf die Verbesserung der Skripterstellung in der PowerShell-Erweiterung für Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="95ea8-245">The PowerShell Team and its partners are focused on improving the scripting experience in the PowerShell extension for Visual Studio Code.</span></span>

## <a name="next-steps"></a><span data-ttu-id="95ea8-246">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="95ea8-246">Next Steps</span></span>

<span data-ttu-id="95ea8-247">Mit dem Wissen zur effektiven Migration jetzt [PowerShell 7 installieren](/powershell/scripting/install/installing-powershell-core-on-windows)!</span><span class="sxs-lookup"><span data-stu-id="95ea8-247">Armed with the knowledge to effectively migrate, [install PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows) now!</span></span>
