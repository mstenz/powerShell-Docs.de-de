---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installieren von PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328201"
---
# <a name="installing-powershellget"></a><span data-ttu-id="fa06f-103">Installieren von PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="fa06f-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="fa06f-104">PowerShellGet ist ein Modul, das zum Lieferumfang der folgenden Releases gehört:</span><span class="sxs-lookup"><span data-stu-id="fa06f-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="fa06f-105">[Windows 10](https://www.microsoft.com/windows) oder höher</span><span class="sxs-lookup"><span data-stu-id="fa06f-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="fa06f-106">[Windows Server 2016](/windows-server/windows-server) oder höher</span><span class="sxs-lookup"><span data-stu-id="fa06f-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="fa06f-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) oder höher</span><span class="sxs-lookup"><span data-stu-id="fa06f-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="fa06f-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="fa06f-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="fa06f-109">Herunterladen der neuesten Version aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="fa06f-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="fa06f-110">Bevor Sie **PowerShellGet** aktualisieren, sollten Sie immer den neuesten **NuGet**-Anbieter installieren.</span><span class="sxs-lookup"><span data-stu-id="fa06f-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="fa06f-111">Führen Sie hierzu den folgenden Befehl in einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="fa06f-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="fa06f-112">Für Systeme mit PowerShell 5.0 (oder höher) können Sie das neueste PowerShellGet-Modul installieren</span><span class="sxs-lookup"><span data-stu-id="fa06f-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="fa06f-113">Zum Installieren von PowerShellGet führen Sie unter Windows 10, Windows Server 2016 auf einem beliebigen System mit WMF 5.0 oder 5.1 oder auf einem beliebigen System mit PowerShell 6 den folgenden Befehl aus einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="fa06f-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="fa06f-114">Verwenden Sie `Update-Module`, um neuere Versionen zu beziehen.</span><span class="sxs-lookup"><span data-stu-id="fa06f-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="fa06f-115">Computer mit PowerShell 3.0 oder PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="fa06f-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="fa06f-116">Diese Anweisungen gelten für Computer, auf denen die **PackageManagement-Vorschauversion** oder keine Version von **PowerShellGet** installiert ist.</span><span class="sxs-lookup"><span data-stu-id="fa06f-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="fa06f-117">Das Cmdlet `Save-Module` wird in beiden Anweisungssätzen verwendet.</span><span class="sxs-lookup"><span data-stu-id="fa06f-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="fa06f-118">`Save-Module` lädt ein Modul und alle Abhängigkeiten aus einem registrierten Repository herunter und speichert sie.</span><span class="sxs-lookup"><span data-stu-id="fa06f-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="fa06f-119">Die neueste Version des Moduls wird in einem bestimmten Pfad auf dem lokalen Computer gespeichert, wird aber nicht installiert.</span><span class="sxs-lookup"><span data-stu-id="fa06f-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="fa06f-120">Weitere Informationen finden Sie unter [Save-Module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="fa06f-120">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="fa06f-121">Computer mit installierter PackageManagement-Vorschauversion</span><span class="sxs-lookup"><span data-stu-id="fa06f-121">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="fa06f-122">Verwenden Sie `Save-Module` in einer PowerShell-Sitzung, um die Module in einem lokalen Verzeichnis zu speichern.</span><span class="sxs-lookup"><span data-stu-id="fa06f-122">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="fa06f-123">Stellen Sie sicher, dass die Module **PowerShellGet** und **PackageManagement** nicht in anderen Prozessen geladen sind.</span><span class="sxs-lookup"><span data-stu-id="fa06f-123">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="fa06f-124">Löschen Sie den Inhalt der Ordner „`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\`“ und „`$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`“.</span><span class="sxs-lookup"><span data-stu-id="fa06f-124">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="fa06f-125">Öffnen Sie die PowerShell-Konsole erneut mit erhöhten Rechten, und führen Sie die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="fa06f-125">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="fa06f-126">Computer ohne PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="fa06f-126">Computers without PowerShellGet</span></span>

<span data-ttu-id="fa06f-127">Für Computer ohne installierte Version von **PowerShellGet** wird zum Herunterladen der Module ein Computer benötigt, auf dem **PowerShellGet** installiert ist.</span><span class="sxs-lookup"><span data-stu-id="fa06f-127">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="fa06f-128">Verwenden Sie `Save-Module` auf dem Computer, auf dem **PowerShellGet** installiert ist, um die aktuelle Version von **PowerShellGet** herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="fa06f-128">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="fa06f-129">Es werden zwei Ordner heruntergeladen: **PowerShellGet** und **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="fa06f-129">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="fa06f-130">Jeder Ordner enthält einen Unterordner mit einer Versionsnummer.</span><span class="sxs-lookup"><span data-stu-id="fa06f-130">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="fa06f-131">Kopieren Sie die Ordner **PowerShellGet** und **PackageManagement** auf den Computer ohne **PowerShellGet**-Installation.</span><span class="sxs-lookup"><span data-stu-id="fa06f-131">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="fa06f-132">Das Zielverzeichnis lautet: `$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="fa06f-132">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
