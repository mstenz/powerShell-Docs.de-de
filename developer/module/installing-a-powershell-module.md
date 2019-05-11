---
title: Installieren eines PowerShell-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229453"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="124f7-102">Installieren eines PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="124f7-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="124f7-103">Nachdem Sie Ihre PowerShell-Modul erstellt haben, möchten Sie wahrscheinlich das Modul auf einem System installieren, damit Sie oder andere Personen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="124f7-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="124f7-104">Im Allgemeinen besteht aus den Moduldateien (z. B. die. psm1, oder die binäre Assembly, das modulmanifest und anderen zugehörigen Dateien) auf ein Verzeichnis auf diesem Computer kopieren.</span><span class="sxs-lookup"><span data-stu-id="124f7-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="124f7-105">Für einen sehr kleinen Projekten kann dies so einfach wie das Kopieren und Einfügen von Dateien mit dem Windows-Explorer auf einem einzelnen Remotecomputer sein; Möglicherweise möchten Sie jedoch, für größere Lösungen einen komplexeren Installationsprozess verwenden.</span><span class="sxs-lookup"><span data-stu-id="124f7-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="124f7-106">Unabhängig davon, wie Sie Ihr Modul auf dem System erhalten können PowerShell über eine Reihe von Techniken verwenden, mit denen Benutzer suchen und verwenden Ihre Module.</span><span class="sxs-lookup"><span data-stu-id="124f7-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="124f7-107">Aus diesem Grund ist das das größte Problem dar, für die Installation sicherstellen, dass PowerShell auf Ihrem Modul suchen kann.</span><span class="sxs-lookup"><span data-stu-id="124f7-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="124f7-108">Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="124f7-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="124f7-109">Regeln für die Installation von Modulen</span><span class="sxs-lookup"><span data-stu-id="124f7-109">Rules for Installing Modules</span></span>

<span data-ttu-id="124f7-110">Die folgende Informationen bezieht sich auf alle Module, einschließlich Module, die Sie erstellen, für die eigene Verwendung, Module, die Sie von anderen Seiten zu erhalten und Module, die Sie an andere Benutzer verteilen.</span><span class="sxs-lookup"><span data-stu-id="124f7-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="124f7-111">Installieren Sie in der PSModulePath-Module</span><span class="sxs-lookup"><span data-stu-id="124f7-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="124f7-112">Wann immer möglich, installieren Sie alle Module in einen Pfad, der in aufgeführt ist die **PSModulePath** Umgebungsvariable oder Hinzufügen von der Modulpfad zu der **PSModulePath** umgebungsvariablenwert.</span><span class="sxs-lookup"><span data-stu-id="124f7-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="124f7-113">Die **PSModulePath** Umgebungsvariablen ($Env: PSModulePath) enthält die Speicherorte der Windows PowerShell-Module.</span><span class="sxs-lookup"><span data-stu-id="124f7-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="124f7-114">Cmdlets basieren auf den Wert der diese Umgebungsvariable, um Module zu suchen.</span><span class="sxs-lookup"><span data-stu-id="124f7-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="124f7-115">In der Standardeinstellung die **PSModulePath** umgebungsvariablenwert enthält die folgenden und die Benutzerverzeichnisse-Modul, aber Sie können hinzufügen und bearbeiten Sie den Wert.</span><span class="sxs-lookup"><span data-stu-id="124f7-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="124f7-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="124f7-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="124f7-117">Dieser Speicherort ist für Module reserviert, die mit Windows ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="124f7-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="124f7-118">Installieren Sie Module nicht an diesen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="124f7-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="124f7-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="124f7-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="124f7-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="124f7-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="124f7-121">Den Wert des abzurufenden der **PSModulePath** Umgebungsvariable, verwenden Sie eine der folgenden Befehle.</span><span class="sxs-lookup"><span data-stu-id="124f7-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="124f7-122">Wert von einem Modulpfad hinzuzufügende der **PSModulePath** Umgebungsvariable Wert können Sie das folgende Befehlsformat.</span><span class="sxs-lookup"><span data-stu-id="124f7-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="124f7-123">Dieses Format wird verwendet die **SetEnvironmentVariable** Methode der **"System.Environment"** Klasse, um eine Sitzung unabhängige Änderung an der **PSModulePath** Umgebung Variable.</span><span class="sxs-lookup"><span data-stu-id="124f7-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="124f7-124">Nachdem Sie den Pfad zum hinzugefügt haben **PSModulePath**, sollten Sie eine Umgebung-Nachricht über die Änderung übertragen.</span><span class="sxs-lookup"><span data-stu-id="124f7-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="124f7-125">Übertragen die Änderung kann andere Anwendungen, z. B. der Shell, um die Änderung zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="124f7-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="124f7-126">Die Änderung gesendet wird, haben Sie Ihre Installation-Produktcode, die beim Senden einer **WM_SETTINGCHANGE** -Nachricht mit `lParam` auf die Zeichenfolge "Umgebung" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="124f7-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="124f7-127">Achten Sie darauf, dass Sie zum Senden der Nachricht, nachdem der Code für die Installation der Module aktualisiert hat **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="124f7-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="124f7-128">Verwenden Sie den richtige Modul Verzeichnisnamen</span><span class="sxs-lookup"><span data-stu-id="124f7-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="124f7-129">Eine wohlgeformte-Modul ist ein Modul, das in einem Verzeichnis gespeichert ist, die den gleichen Namen wie der Basisname der mindestens eine Datei im Modulverzeichnis gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="124f7-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="124f7-130">Wenn ein Modul nicht wohlgeformt ist, werden Sie von Windows PowerShell nicht als Modul erkannt.</span><span class="sxs-lookup"><span data-stu-id="124f7-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="124f7-131">"Name der Basisname" eine Datei ist der Name ohne die Dateinamenerweiterung.</span><span class="sxs-lookup"><span data-stu-id="124f7-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="124f7-132">In einem wohlgeformten-Modul muss der Namen des Verzeichnisses, das die Moduldateien enthält, der Basisname der mindestens eine Datei im Modul übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="124f7-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="124f7-133">Im Beispiel Fabrikam-Modul, beispielsweise das Verzeichnis, das die Moduldateien enthält, heißt "Fabrikam" und mindestens eine Datei wurde den Basisnamen "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="124f7-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="124f7-134">In diesem Fall müssen sowohl für Fabrikam.psd1 Fabrikam.dll den Basisnamen "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="124f7-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="124f7-135">Auswirkungen der falsche Installation</span><span class="sxs-lookup"><span data-stu-id="124f7-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="124f7-136">Wenn das Modul nicht ordnungsgemäß formatiert ist und der Speicherort sich nicht im Wert des befindet der **PSModulePath** Umgebungsvariable, grundlegende Suchfunktionen von Windows PowerShell, wie die folgende, funktionieren nicht.</span><span class="sxs-lookup"><span data-stu-id="124f7-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="124f7-137">Das Modul Automatisches Laden von Feature kann nicht für das Modul automatisch importiert werden.</span><span class="sxs-lookup"><span data-stu-id="124f7-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="124f7-138">Die `ListAvailable` Parameter, der die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet wurde das Modul nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="124f7-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="124f7-139">Die [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet wurde das Modul nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="124f7-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="124f7-140">Um das Modul zu importieren, müssen Sie den vollständigen Pfad zu der Stamm-Moduldatei oder modulmanifestdatei angeben.</span><span class="sxs-lookup"><span data-stu-id="124f7-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="124f7-141">Zusätzliche Features wie die folgende, funktionieren nicht, es sei denn, das Modul in die Sitzung importiert wird.</span><span class="sxs-lookup"><span data-stu-id="124f7-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="124f7-142">In wohlgeformte Module in der **PSModulePath** Umgebungsvariable, diese Features funktionieren, auch wenn das Modul nicht in die Sitzung importiert wird.</span><span class="sxs-lookup"><span data-stu-id="124f7-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="124f7-143">Die [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet Befehle in das Modul nicht finden kann.</span><span class="sxs-lookup"><span data-stu-id="124f7-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="124f7-144">Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlets kann nicht aktualisiert oder Speichern der Hilfe für das Modul.</span><span class="sxs-lookup"><span data-stu-id="124f7-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="124f7-145">Die [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) Cmdlet kann nicht gefunden und die Befehle im Modul angezeigt.</span><span class="sxs-lookup"><span data-stu-id="124f7-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="124f7-146">Die Befehle im Modul fehlen die `Show-Command` Fenster in Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="124f7-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="124f7-147">Zur Installation von Modulen</span><span class="sxs-lookup"><span data-stu-id="124f7-147">Where to Install Modules</span></span>

<span data-ttu-id="124f7-148">In diesem Abschnitt wird erläutert, wo im Dateisystem Windows PowerShell-Module zu installieren.</span><span class="sxs-lookup"><span data-stu-id="124f7-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="124f7-149">Der Speicherort hängt davon ab, wie das Modul verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="124f7-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="124f7-150">Installation von Modulen für einen bestimmten Benutzer</span><span class="sxs-lookup"><span data-stu-id="124f7-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="124f7-151">Wenn Sie Ihr eigenes Modul erstellen, oder fordern Sie ein Modul von einer anderen Partei, wie z. B. eine Windows PowerShell-Community-Website, und das Modul nur für Ihr Benutzerkonto verfügbar sein soll, installieren Sie das Modul in Ihrem Verzeichnis der benutzerspezifischen Module.</span><span class="sxs-lookup"><span data-stu-id="124f7-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="124f7-152">Benutzerspezifische Modulverzeichnis wird hinzugefügt, auf den Wert des der **PSModulePath** Umgebungsvariable standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="124f7-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="124f7-153">Installation von Modulen für alle Benutzer in Program Files</span><span class="sxs-lookup"><span data-stu-id="124f7-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="124f7-154">Wenn Sie ein Modul für alle Benutzerkonten auf dem Computer verfügbar sein soll, installieren Sie das Modul in den Speicherort der Programmdateien an.</span><span class="sxs-lookup"><span data-stu-id="124f7-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="124f7-155">Der Speicherort der Programmdateien wird standardmäßig in Windows PowerShell 4.0 und höher den Wert der PSModulePath-Umgebungsvariablen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="124f7-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="124f7-156">Informationen zu früheren Versionen von Windows PowerShell manuell die Programmdateien Speicherort ((%ProgramFiles%\WindowsPowerShell\Modules) erstellen und diesen Pfad der Umgebungsvariablen PSModulePath hinzufügen, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="124f7-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="124f7-157">Installation von Modulen in einem Produktverzeichnis</span><span class="sxs-lookup"><span data-stu-id="124f7-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="124f7-158">Wenn Sie das Modul an andere Parteien verteilen, verwenden Sie die oben beschriebenen Programmdateien Standardspeicherort, oder erstellen Sie Ihre eigenen unternehmensspezifischen oder produktspezifische Unterverzeichnis von Verzeichnis "% ProgramFiles%".</span><span class="sxs-lookup"><span data-stu-id="124f7-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="124f7-159">Z. B. wird Fabrikam Technologies, einem fiktiven Unternehmen, ein Windows PowerShell-Modul für die Fabrikam-Manager-Produkt ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="124f7-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="124f7-160">Die Modul-Installationsprogramm erstellt ein Unterverzeichnis Module im Unterverzeichnis "Fabrikam-Manager-Produkt".</span><span class="sxs-lookup"><span data-stu-id="124f7-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="124f7-161">Um die Suchfunktionen von Windows PowerShell-Modul finden Sie das Fabrikam-Modul zu aktivieren, fügt der Fabrikam-Modulinstallation der Speicherort auf den Wert des der **PSModulePath** -Umgebungsvariablen angegeben.</span><span class="sxs-lookup"><span data-stu-id="124f7-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="124f7-162">Installieren von Modulen in das Verzeichnis für gemeinsame Dateien</span><span class="sxs-lookup"><span data-stu-id="124f7-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="124f7-163">Wenn ein Modul von mehreren Komponenten eines Produkts oder mehrere Versionen eines Produkts verwendet wird, installieren Sie das Modul in einem Unterverzeichnis modulspezifischen des Unterverzeichnisses Files\Modules %ProgramFiles%\Common.</span><span class="sxs-lookup"><span data-stu-id="124f7-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="124f7-164">Im folgenden Beispiel wird das Fabrikam-Modul in einem Unterverzeichnis "Fabrikam" des installiert die `%ProgramFiles%\Common Files\Modules` Unterverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="124f7-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="124f7-165">Beachten Sie, dass jedes Modul in ein eigenes Unterverzeichnis im Unterverzeichnis "Module" befindet.</span><span class="sxs-lookup"><span data-stu-id="124f7-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="124f7-166">Klicken Sie dann das Installationsprogramm den Wert des gewährleistet die **PSModulePath** Umgebungsvariable enthält den Pfad des Unterverzeichnisses Module gemeinsame Dateien.</span><span class="sxs-lookup"><span data-stu-id="124f7-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="124f7-167">Installieren mehrerer Versionen eines Moduls</span><span class="sxs-lookup"><span data-stu-id="124f7-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="124f7-168">Um mehrere Versionen desselben Moduls zu installieren, verwenden Sie das folgende Verfahren aus.</span><span class="sxs-lookup"><span data-stu-id="124f7-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="124f7-169">Erstellen Sie ein Verzeichnis für jede Version des Moduls an.</span><span class="sxs-lookup"><span data-stu-id="124f7-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="124f7-170">Schließen Sie die Versionsnummer in den Namen des Verzeichnisses an.</span><span class="sxs-lookup"><span data-stu-id="124f7-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="124f7-171">Erstellen Sie ein modulmanifest für jede Version des Moduls an.</span><span class="sxs-lookup"><span data-stu-id="124f7-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="124f7-172">In den Wert des der **"moduleversion"** -Schlüssel im Manifest, geben Sie die Versionsnummer des Moduls.</span><span class="sxs-lookup"><span data-stu-id="124f7-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="124f7-173">Speichern Sie die Manifestdatei (psd1), in dem versionsspezifischen-Verzeichnis für das Modul.</span><span class="sxs-lookup"><span data-stu-id="124f7-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="124f7-174">Den Pfad des Stammordners Modul hinzufügen, auf den Wert des der **PSModulePath** Umgebungsvariablen wie in den folgenden Beispielen gezeigt.</span><span class="sxs-lookup"><span data-stu-id="124f7-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="124f7-175">Um eine bestimmte Version des Moduls zu importieren, können Sie der Endbenutzer die `MinimumVersion` oder `RequiredVersion` Parameter von der [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="124f7-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="124f7-176">Wenn das Fabrikam-Modul in Versionen 8.0 und 9.0 verfügbar ist, kann die Verzeichnisstruktur der Fabrikam-Modul z. B. folgendermaßen aussehen.</span><span class="sxs-lookup"><span data-stu-id="124f7-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="124f7-177">Das Installationsprogramm fügt beide die Modulpfade zu den **PSModulePath** umgebungsvariablenwert.</span><span class="sxs-lookup"><span data-stu-id="124f7-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="124f7-178">Nachdem diese Schritte abgeschlossen ist, sind die **ListAvailable** Parameter, der die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet wird sowohl der Fabrikam-Module.</span><span class="sxs-lookup"><span data-stu-id="124f7-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="124f7-179">Um ein bestimmtes Modul zu importieren, verwenden die `MinimumVersion` oder `RequiredVersion` Parameter von der [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="124f7-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="124f7-180">Wenn beide Module sind in der gleichen Sitzung importiert, und die Module Cmdlets, mit dem gleichen Namen enthalten, gelten die Sitzung die Cmdlets, die zuletzt importiert werden.</span><span class="sxs-lookup"><span data-stu-id="124f7-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="124f7-181">Konflikte bei Befehlsnamen Behandlung</span><span class="sxs-lookup"><span data-stu-id="124f7-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="124f7-182">Konflikte bei Befehlsnamen können auftreten, wenn die Befehle, die ein Modul exportiert den gleichen Namen wie Befehle in der Sitzung des Benutzers verfügen.</span><span class="sxs-lookup"><span data-stu-id="124f7-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="124f7-183">Wenn eine Sitzung zwei Befehle, die den gleichen Namen haben enthält, führt Windows PowerShell den Befehlstyp, der Vorrang hat.</span><span class="sxs-lookup"><span data-stu-id="124f7-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="124f7-184">Wenn eine Sitzung zwei Befehle, die den gleichen Namen und den gleichen Typ aufweisen enthält, führt Windows PowerShell den Befehl aus, der die der Sitzung zuletzt hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="124f7-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="124f7-185">Zum Ausführen eines Befehls, das nicht standardmäßig ausgeführt wird, können Benutzer den Namen des Befehls mit dem Modulnamen qualifizieren.</span><span class="sxs-lookup"><span data-stu-id="124f7-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="124f7-186">Wenn die Sitzung enthält z. B. eine `Get-Date` Funktion und die `Get-Date` Windows PowerShell-Cmdlet führt die Funktion standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="124f7-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="124f7-187">Stellen Sie den Befehl mit den Namen des Moduls, wie z. B. zum Ausführen des Cmdlets:</span><span class="sxs-lookup"><span data-stu-id="124f7-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="124f7-188">Modulautoren können um Namenskonflikte zu vermeiden, verwenden die **DefaultCommandPrefix** Schlüssel im modulmanifest an ein nomenpräfix für alle Befehle aus dem Modul exportiert.</span><span class="sxs-lookup"><span data-stu-id="124f7-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="124f7-189">Benutzer können die **Präfix** Parameter, der die `Import-Module` Cmdlet, um ein anderes Präfix verwenden.</span><span class="sxs-lookup"><span data-stu-id="124f7-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="124f7-190">Der Wert des der **Präfix** Parameter hat Vorrang vor den Wert des der **DefaultCommandPrefix** Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="124f7-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="124f7-191">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="124f7-191">See Also</span></span>

[<span data-ttu-id="124f7-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="124f7-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="124f7-193">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="124f7-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
