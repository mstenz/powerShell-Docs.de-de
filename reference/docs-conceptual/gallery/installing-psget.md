---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installieren von PowerShellGet
ms.openlocfilehash: f42eb0df101eb63a5dc267196fa9f666747b8e35
ms.sourcegitcommit: 23ea4a36ee85f923684657de5313a5adf0b6b094
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2020
ms.locfileid: "83727794"
---
# <a name="installing-powershellget"></a><span data-ttu-id="28579-103">Installieren von PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="28579-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="28579-104">PowerShellGet ist ein Modul, das zum Lieferumfang der folgenden Releases gehört:</span><span class="sxs-lookup"><span data-stu-id="28579-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="28579-105">[Windows 10](https://www.microsoft.com/windows) oder höher</span><span class="sxs-lookup"><span data-stu-id="28579-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="28579-106">[Windows Server 2016](/windows-server/windows-server) oder höher</span><span class="sxs-lookup"><span data-stu-id="28579-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="28579-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) oder höher</span><span class="sxs-lookup"><span data-stu-id="28579-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="28579-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="28579-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="28579-109">Herunterladen der neuesten Version aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="28579-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="28579-110">Bevor Sie **PowerShellGet** aktualisieren, sollten Sie immer den neuesten **NuGet**-Anbieter installieren.</span><span class="sxs-lookup"><span data-stu-id="28579-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="28579-111">Führen Sie hierzu den folgenden Befehl in einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="28579-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="28579-112">Für Systeme mit PowerShell 5.0 (oder höher) können Sie das neueste PowerShellGet-Modul installieren</span><span class="sxs-lookup"><span data-stu-id="28579-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="28579-113">Zum Installieren von PowerShellGet führen Sie unter Windows 10, Windows Server 2016 auf einem beliebigen System mit WMF 5.0 oder 5.1 oder auf einem beliebigen System mit PowerShell 6 den folgenden Befehl aus einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="28579-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="28579-114">Verwenden Sie `Update-Module`, um neuere Versionen zu beziehen.</span><span class="sxs-lookup"><span data-stu-id="28579-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="28579-115">Computer mit PowerShell 3.0 oder PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="28579-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="28579-116">Diese Anweisungen gelten für Computer, auf denen die **PackageManagement-Vorschauversion** oder keine Version von **PowerShellGet** installiert ist.</span><span class="sxs-lookup"><span data-stu-id="28579-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="28579-117">Das Cmdlet `Save-Module` wird in beiden Anweisungssätzen verwendet.</span><span class="sxs-lookup"><span data-stu-id="28579-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="28579-118">`Save-Module` lädt ein Modul und alle Abhängigkeiten aus einem registrierten Repository herunter und speichert sie.</span><span class="sxs-lookup"><span data-stu-id="28579-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="28579-119">Die neueste Version des Moduls wird in einem bestimmten Pfad auf dem lokalen Computer gespeichert, wird aber nicht installiert.</span><span class="sxs-lookup"><span data-stu-id="28579-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="28579-120">Kopieren Sie die in Modulen gespeicherten Ordner in `$env:ProgramFiles\WindowsPowerShell\Modules`, um die Module in PowerShell 3.0 oder 4.0 zu installieren.</span><span class="sxs-lookup"><span data-stu-id="28579-120">To install the modules in PowerShell 3.0 or 4.0, copy the module saved folders to `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="28579-121">Weitere Informationen finden Sie unter [Save-Module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="28579-121">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

> [!NOTE]
> <span data-ttu-id="28579-122">PowerShell 3.0 und PowerShell 4.0 unterstützten nur eine Version eines Moduls</span><span class="sxs-lookup"><span data-stu-id="28579-122">PowerShell 3.0 and PowerShell 4.0 only supported one version of a module.</span></span> <span data-ttu-id="28579-123">Ab PowerShell 5.0 werden Module in `<modulename>\<version>` installiert.</span><span class="sxs-lookup"><span data-stu-id="28579-123">Starting in PowerShell 5.0, modules are installed in `<modulename>\<version>`.</span></span> <span data-ttu-id="28579-124">Dadurch können Sie mehrere Versionen nebeneinander installieren.</span><span class="sxs-lookup"><span data-stu-id="28579-124">This allowed you to install multiple versions side-by-side.</span></span> <span data-ttu-id="28579-125">Nachdem Sie das Modul mithilfe von `Save-Module` heruntergeladen haben, müssen Sie die Datei aus `<modulename>\<version>` in den Ordner `<modulename>` auf dem Zielcomputer kopieren.</span><span class="sxs-lookup"><span data-stu-id="28579-125">After downloading the module using `Save-Module` you must copy the files from the `<modulename>\<version>` to the `<modulename>` folder on the destination machine.</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="28579-126">Computer mit installierter PackageManagement-Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="28579-126">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="28579-127">Verwenden Sie `Save-Module` in einer PowerShell-Sitzung, um die Module in einem lokalen Verzeichnis zu speichern.</span><span class="sxs-lookup"><span data-stu-id="28579-127">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="28579-128">Stellen Sie sicher, dass die Module **PowerShellGet** und **PackageManagement** nicht in anderen Prozessen geladen sind.</span><span class="sxs-lookup"><span data-stu-id="28579-128">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="28579-129">Löschen Sie den Inhalt der Ordner „`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\`“ und „`$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`“.</span><span class="sxs-lookup"><span data-stu-id="28579-129">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="28579-130">Öffnen Sie die PowerShell-Konsole erneut mit erhöhten Rechten, und führen Sie die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="28579-130">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\<version>\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\<version>\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="28579-131">Computer ohne PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="28579-131">Computers without PowerShellGet</span></span>

<span data-ttu-id="28579-132">Für Computer ohne installierte Version von **PowerShellGet** wird zum Herunterladen der Module ein Computer benötigt, auf dem **PowerShellGet** installiert ist.</span><span class="sxs-lookup"><span data-stu-id="28579-132">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="28579-133">Verwenden Sie `Save-Module` auf dem Computer, auf dem **PowerShellGet** installiert ist, um die aktuelle Version von **PowerShellGet** herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="28579-133">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="28579-134">Es werden zwei Ordner heruntergeladen: **PowerShellGet** und **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="28579-134">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="28579-135">Jeder Ordner enthält einen Unterordner mit einer Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="28579-135">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="28579-136">Kopieren Sie die Ordner **PowerShellGet** und **PackageManagement** auf den Computer ohne **PowerShellGet**-Installation.</span><span class="sxs-lookup"><span data-stu-id="28579-136">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="28579-137">Das Zielverzeichnis lautet: `$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="28579-137">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
