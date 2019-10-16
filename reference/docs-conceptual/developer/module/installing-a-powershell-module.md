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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367069"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="db062-102">Installieren eines PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="db062-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="db062-103">Nachdem Sie das PowerShell-Modul erstellt haben, möchten Sie das Modul wahrscheinlich auf einem System installieren, damit Sie von Ihnen oder anderen Benutzern verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="db062-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="db062-104">Im Allgemeinen besteht dies darin, die Moduldateien (d. psm1. die binäre Assembly, das Modul Manifest und alle zugehörigen Dateien) in ein Verzeichnis auf diesem Computer zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="db062-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="db062-105">Bei einem sehr kleinen Projekt kann dies so einfach sein wie das Kopieren und Einfügen der Dateien mit Windows-Explorer auf einem einzelnen Remote Computer. bei größeren Lösungen möchten Sie jedoch möglicherweise einen komplexeren Installationsprozess verwenden.</span><span class="sxs-lookup"><span data-stu-id="db062-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="db062-106">Unabhängig davon, wie Sie Ihr Modul auf das System übernehmen, kann PowerShell eine Reihe von Techniken verwenden, mit denen Benutzer Ihre Module suchen und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="db062-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="db062-107">Das Hauptproblem bei der Installation besteht daher darin, sicherzustellen, dass PowerShell das Modul finden kann.</span><span class="sxs-lookup"><span data-stu-id="db062-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="db062-108">Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="db062-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="db062-109">Regeln für die Installation von Modulen</span><span class="sxs-lookup"><span data-stu-id="db062-109">Rules for Installing Modules</span></span>

<span data-ttu-id="db062-110">Die folgenden Informationen beziehen sich auf alle Module, einschließlich der Module, die Sie für Ihre eigene Verwendung erstellen, der Module, die Sie von anderen Anbietern erhalten, sowie von Modulen, die Sie an andere Benutzer verteilen.</span><span class="sxs-lookup"><span data-stu-id="db062-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="db062-111">Installieren von Modulen in psmodulepath</span><span class="sxs-lookup"><span data-stu-id="db062-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="db062-112">Installieren Sie nach Möglichkeit alle Module in einem Pfad, der in der **psmodulepath** -Umgebungsvariablen aufgelistet ist, oder fügen Sie den Modulpfad dem Wert der Umgebungsvariablen **psmodulepath** hinzu.</span><span class="sxs-lookup"><span data-stu-id="db062-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="db062-113">Die **psmodulepath** -Umgebungsvariable ($env:P smodulepath) enthält die Speicherorte von Windows PowerShell-Modulen.</span><span class="sxs-lookup"><span data-stu-id="db062-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="db062-114">Die Cmdlets basieren auf dem Wert dieser Umgebungsvariablen, um Module zu suchen.</span><span class="sxs-lookup"><span data-stu-id="db062-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="db062-115">Standardmäßig enthält der Wert der Umgebungsvariablen **psmodulepath** die folgenden System-und Benutzermodul Verzeichnisse, aber Sie können den Wert hinzufügen und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="db062-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="db062-116">`$PSHome\Modules` (%windir%\system32\WindowsPowerShell\v1.0\modules)</span><span class="sxs-lookup"><span data-stu-id="db062-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="db062-117">Dieser Speicherort ist für Module reserviert, die mit Windows ausgeliefert werden.</span><span class="sxs-lookup"><span data-stu-id="db062-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="db062-118">Installieren Sie keine Module an diesem Speicherort.</span><span class="sxs-lookup"><span data-stu-id="db062-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="db062-119">`$Home\Documents\WindowsPowerShell\Modules` (%USERPROFILE%\documents\windowspowershell\modules)</span><span class="sxs-lookup"><span data-stu-id="db062-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="db062-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\windowspowershell\modules)</span><span class="sxs-lookup"><span data-stu-id="db062-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="db062-121">Um den Wert der **psmodulepath** -Umgebungsvariablen abzurufen, verwenden Sie einen der folgenden Befehle.</span><span class="sxs-lookup"><span data-stu-id="db062-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="db062-122">Verwenden Sie das folgende Befehls Format, um dem Wert des Umgebungsvariablen Werts **psmodulepath** einen Modulpfad hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="db062-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="db062-123">Dieses Format verwendet die Methode "\* **tenvironmentvariable** " der Klasse " **System. Environment** ", um eine Sitzungs unabhängige Änderung an der **psmodulepath** -Umgebungsvariablen vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="db062-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="db062-124">Nachdem Sie den Pfad zu **psmodulepath**hinzugefügt haben, sollten Sie eine Umgebungs Meldung über die Änderung übertragen.</span><span class="sxs-lookup"><span data-stu-id="db062-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="db062-125">Durch das Senden der Änderung können andere Anwendungen, wie z. b. die Shell, die Änderung übernehmen.</span><span class="sxs-lookup"><span data-stu-id="db062-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="db062-126">Um die Änderung zu übertragen, lassen Sie Ihren Produkt Installationscode eine **WM_SETTINGCHANGE** -Nachricht senden, wobei `lParam` auf die Zeichenfolge "Environment" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="db062-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="db062-127">Stellen Sie sicher, dass Sie die Nachricht senden, nachdem der Installationscode des Moduls " **psmodulepath**" aktualisiert hat.</span><span class="sxs-lookup"><span data-stu-id="db062-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="db062-128">Richtigen Modul Verzeichnisnamen verwenden</span><span class="sxs-lookup"><span data-stu-id="db062-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="db062-129">Ein wohl geformtes Modul ist ein Modul, das in einem Verzeichnis gespeichert ist, das denselben Namen wie der Basis Name mindestens einer Datei im Modul Verzeichnis hat.</span><span class="sxs-lookup"><span data-stu-id="db062-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="db062-130">Wenn ein Modul nicht wohl geformt ist, wird es von Windows PowerShell nicht als Modul erkannt.</span><span class="sxs-lookup"><span data-stu-id="db062-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="db062-131">Der "Basisname" einer Datei ist der Name ohne die Dateinamenerweiterung.</span><span class="sxs-lookup"><span data-stu-id="db062-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="db062-132">In einem wohlgeformten Modul muss der Name des Verzeichnisses, das die Moduldateien enthält, mit dem Basis Namen von mindestens einer Datei im Modul identisch sein.</span><span class="sxs-lookup"><span data-stu-id="db062-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="db062-133">Beispielsweise heißt das Verzeichnis im Fabrikam-Beispielmodul, das die Moduldateien enthält, den Namen Fabrikam, und mindestens eine Datei hat den Basisnamen "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="db062-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="db062-134">In diesem Fall haben sowohl "fabrikam. psd1" als auch "fabrikam. dll" den Basisnamen "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="db062-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="db062-135">Auswirkungen falscher Installation</span><span class="sxs-lookup"><span data-stu-id="db062-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="db062-136">Wenn das Modul nicht wohl geformt ist und sein Speicherort nicht im Wert der **psmodulepath** -Umgebungsvariablen enthalten ist, funktionieren die grundlegenden Ermittlungs Features von Windows PowerShell, wie z. b. die folgenden, nicht.</span><span class="sxs-lookup"><span data-stu-id="db062-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="db062-137">Die Funktion zum automatischen Laden von Modulen kann das Modul nicht automatisch importieren.</span><span class="sxs-lookup"><span data-stu-id="db062-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="db062-138">Der Parameter "`ListAvailable`" des Cmdlets " [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) " kann das Modul nicht finden.</span><span class="sxs-lookup"><span data-stu-id="db062-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="db062-139">Das [Import-Module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet kann das Modul nicht finden.</span><span class="sxs-lookup"><span data-stu-id="db062-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="db062-140">Zum Importieren des Moduls müssen Sie den vollständigen Pfad zur Stamm Modul Datei oder zur Modul Manifest-Datei angeben.</span><span class="sxs-lookup"><span data-stu-id="db062-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="db062-141">Weitere Funktionen, wie z. b. die folgenden, funktionieren nicht, es sei denn, das Modul wird in die Sitzung importiert.</span><span class="sxs-lookup"><span data-stu-id="db062-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="db062-142">In wohlgeformten Modulen in der **psmodulepath** -Umgebungsvariablen funktionieren diese Features auch dann, wenn das Modul nicht in die Sitzung importiert wird.</span><span class="sxs-lookup"><span data-stu-id="db062-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="db062-143">Das [Get-Command-](/powershell/module/Microsoft.PowerShell.Core/Get-Command) Cmdlet kann Befehle im Modul nicht finden.</span><span class="sxs-lookup"><span data-stu-id="db062-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="db062-144">Die Cmdlets " [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) " und " [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) " können die Hilfe für das Modul nicht aktualisieren oder speichern.</span><span class="sxs-lookup"><span data-stu-id="db062-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="db062-145">Das Cmdlet " [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) " kann die Befehle im Modul nicht finden und anzeigen.</span><span class="sxs-lookup"><span data-stu-id="db062-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="db062-146">Die Befehle im Modul fehlen im Fenster "`Show-Command`" in Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="db062-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="db062-147">Installationsort von Modulen</span><span class="sxs-lookup"><span data-stu-id="db062-147">Where to Install Modules</span></span>

<span data-ttu-id="db062-148">In diesem Abschnitt wird erläutert, wo im Dateisystem Windows PowerShell-Module installiert werden.</span><span class="sxs-lookup"><span data-stu-id="db062-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="db062-149">Der Speicherort hängt davon ab, wie das Modul verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="db062-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="db062-150">Installieren von Modulen für einen bestimmten Benutzer</span><span class="sxs-lookup"><span data-stu-id="db062-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="db062-151">Wenn Sie ein eigenes Modul erstellen oder ein Modul von einer anderen Partei (z. b. eine Windows PowerShell-Communitywebsite) erstellen möchten, und Sie möchten, dass das Modul nur für Ihr Benutzerkonto verfügbar ist, installieren Sie das Modul in Ihrem benutzerspezifischen Modul Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="db062-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="db062-152">Das Verzeichnis für benutzerspezifische Module wird standardmäßig dem Wert der **psmodulepath** -Umgebungsvariablen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="db062-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="db062-153">Installieren von Modulen für alle Benutzer in Programmdateien</span><span class="sxs-lookup"><span data-stu-id="db062-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="db062-154">Wenn Sie möchten, dass ein Modul für alle Benutzerkonten auf dem Computer verfügbar ist, installieren Sie das Modul im Speicherort der Programmdateien.</span><span class="sxs-lookup"><span data-stu-id="db062-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="db062-155">Der Speicherort der Programmdateien wird standardmäßig in Windows PowerShell 4,0 und höher dem Wert der Umgebungsvariablen psmodulepath hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="db062-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="db062-156">Bei früheren Versionen von Windows PowerShell können Sie den Speicherort der Programmdateien ((%ProgramFiles%\windowspowershell\modules) manuell erstellen und diesen Pfad der Umgebungsvariablen psmodulepath hinzufügen, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="db062-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="db062-157">Installieren von Modulen in einem Produktverzeichnis</span><span class="sxs-lookup"><span data-stu-id="db062-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="db062-158">Wenn Sie das Modul an andere Parteien verteilen, verwenden Sie den oben beschriebenen Standard Speicherort für Programmdateien, oder erstellen Sie ein eigenes unternehmensspezifisches oder produktspezifisches Unterverzeichnis des Verzeichnisses "% Program Files%".</span><span class="sxs-lookup"><span data-stu-id="db062-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="db062-159">Beispielsweise wird von Fabrikam Technologies, einem fiktiven Unternehmen, ein Windows PowerShell-Modul für das Fabrikam Manager-Produkt versendet.</span><span class="sxs-lookup"><span data-stu-id="db062-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="db062-160">Der modulinstallerinstaller erstellt im Unterverzeichnis "Fabrikam Manager Product" ein Unterverzeichnis "modules".</span><span class="sxs-lookup"><span data-stu-id="db062-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="db062-161">Zum Aktivieren der Ermittlungs Funktionen des Windows PowerShell-Moduls für die Suche nach dem Modul "Fabrikam" fügt das Installationsprogramm des Fabrikam-Moduls den Speicherort des Moduls dem Wert der **psmodulepath** -Umgebungsvariablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="db062-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="db062-162">Installieren von Modulen im Verzeichnis "gemeinsame Dateien"</span><span class="sxs-lookup"><span data-stu-id="db062-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="db062-163">Wenn ein Modul von mehreren Komponenten eines Produkts oder von mehreren Produktversionen verwendet wird, installieren Sie das Modul in einem modulspezifischen Unterverzeichnis des Unterverzeichnisses "%ProgramFiles%\Common files\modules".</span><span class="sxs-lookup"><span data-stu-id="db062-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="db062-164">Im folgenden Beispiel wird das Modul "Fabrikam" in einem Unterverzeichnis "Fabrikam" des Unterverzeichnisses "`%ProgramFiles%\Common Files\Modules`" installiert.</span><span class="sxs-lookup"><span data-stu-id="db062-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="db062-165">Beachten Sie, dass sich jedes Modul in einem eigenen Unterverzeichnis im Unterverzeichnis "modules" befindet.</span><span class="sxs-lookup"><span data-stu-id="db062-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="db062-166">Das Installationsprogramm stellt dann sicher, dass der Wert der **psmodulepath** -Umgebungsvariablen den Pfad des Unterverzeichnisses der allgemeinen Datei Module enthält.</span><span class="sxs-lookup"><span data-stu-id="db062-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="db062-167">Installieren mehrerer Versionen eines Moduls</span><span class="sxs-lookup"><span data-stu-id="db062-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="db062-168">Wenn Sie mehrere Versionen desselben Moduls installieren möchten, verwenden Sie das folgende Verfahren.</span><span class="sxs-lookup"><span data-stu-id="db062-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="db062-169">Erstellen Sie ein Verzeichnis für jede Version des Moduls.</span><span class="sxs-lookup"><span data-stu-id="db062-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="db062-170">Fügen Sie die Versionsnummer in den Verzeichnisnamen ein.</span><span class="sxs-lookup"><span data-stu-id="db062-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="db062-171">Erstellen Sie ein Modul Manifest für jede Version des Moduls.</span><span class="sxs-lookup"><span data-stu-id="db062-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="db062-172">Geben Sie im Manifest im Wert des **moduleversion** -Schlüssels die Modulversionsnummer ein.</span><span class="sxs-lookup"><span data-stu-id="db062-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="db062-173">Speichern Sie die Manifest-Datei (. psd1) im Versions spezifischen Verzeichnis für das Modul.</span><span class="sxs-lookup"><span data-stu-id="db062-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="db062-174">Fügen Sie den Pfad des Modul Stamm Ordners zum Wert der **psmodulepath** -Umgebungsvariablen hinzu, wie in den folgenden Beispielen gezeigt.</span><span class="sxs-lookup"><span data-stu-id="db062-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="db062-175">Um eine bestimmte Version des Moduls zu importieren, kann der Endbenutzer die `MinimumVersion`-oder `RequiredVersion`-Parameter des [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) -Cmdlets verwenden.</span><span class="sxs-lookup"><span data-stu-id="db062-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="db062-176">Wenn das Modul Fabrikam beispielsweise in den Versionen 8,0 und 9,0 verfügbar ist, könnte die Fabrikam-Modul Verzeichnisstruktur wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="db062-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="db062-177">Das Installationsprogramm fügt dem Wert der Umgebungsvariablen **psmodulepath** beide Modul Pfade hinzu.</span><span class="sxs-lookup"><span data-stu-id="db062-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="db062-178">Wenn diese Schritte ausgeführt werden, ruft der **listavailable** -Parameter des [Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlets beide Fabrikam-Module ab.</span><span class="sxs-lookup"><span data-stu-id="db062-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="db062-179">Um ein bestimmtes Modul zu importieren, verwenden Sie die Parameter "`MinimumVersion`" oder "`RequiredVersion`" des Cmdlets " [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ".</span><span class="sxs-lookup"><span data-stu-id="db062-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="db062-180">Wenn beide Module in dieselbe Sitzung importiert werden und die Module Cmdlets mit denselben Namen enthalten, sind die zuletzt importierten Cmdlets in der Sitzung gültig.</span><span class="sxs-lookup"><span data-stu-id="db062-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="db062-181">Behandeln von Befehlsnamen Konflikten</span><span class="sxs-lookup"><span data-stu-id="db062-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="db062-182">Konflikte mit Befehlsnamen können auftreten, wenn die Befehle, die ein Modul exportiert, denselben Namen wie die Befehle in der Benutzersitzung haben.</span><span class="sxs-lookup"><span data-stu-id="db062-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="db062-183">Wenn eine Sitzung zwei Befehle mit demselben Namen enthält, führt Windows PowerShell den Befehlstyp aus, der Vorrang hat.</span><span class="sxs-lookup"><span data-stu-id="db062-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="db062-184">Wenn eine Sitzung zwei Befehle mit demselben Namen und demselben Typ enthält, führt Windows PowerShell den Befehl aus, der der Sitzung zuletzt hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="db062-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="db062-185">Um einen Befehl auszuführen, der nicht standardmäßig ausgeführt wird, können Benutzer den Befehlsnamen mit dem Modulnamen qualifizieren.</span><span class="sxs-lookup"><span data-stu-id="db062-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="db062-186">Wenn die Sitzung z. b. eine `Get-Date`-Funktion und das `Get-Date`-Cmdlet enthält, führt Windows PowerShell die Funktion standardmäßig aus.</span><span class="sxs-lookup"><span data-stu-id="db062-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="db062-187">Um das Cmdlet auszuführen, stellen Sie dem Befehl den Namen des Moduls voran, z. b.:</span><span class="sxs-lookup"><span data-stu-id="db062-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="db062-188">Um Namenskonflikte zu verhindern, können Modul Autoren den **defaultcommandprefix** -Schlüssel im Modul Manifest verwenden, um ein Substantiv-Präfix für alle Befehle anzugeben, die vom Modul exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="db062-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="db062-189">Benutzer können den **prefix** -Parameter des `Import-Module`-Cmdlets verwenden, um ein alternatives Präfix zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="db062-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="db062-190">Der Wert des **prefix** -Parameters hat Vorrang vor dem Wert des **defaultcommandprefix** -Schlüssels.</span><span class="sxs-lookup"><span data-stu-id="db062-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="db062-191">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="db062-191">See Also</span></span>

[<span data-ttu-id="db062-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="db062-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="db062-193">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="db062-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
