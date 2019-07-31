---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installieren von PowerShellGet
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601416"
---
# <a name="installing-powershellget"></a><span data-ttu-id="b0897-103">Installieren von PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="b0897-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="b0897-104">PowerShellGet ist ein Modul, das zum Lieferumfang der folgenden Releases gehört:</span><span class="sxs-lookup"><span data-stu-id="b0897-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="b0897-105">[Windows 10](https://www.microsoft.com/windows) oder höher</span><span class="sxs-lookup"><span data-stu-id="b0897-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="b0897-106">[Windows Server 2016](/windows-server/windows-server) oder höher</span><span class="sxs-lookup"><span data-stu-id="b0897-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="b0897-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) oder höher</span><span class="sxs-lookup"><span data-stu-id="b0897-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="b0897-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="b0897-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="b0897-109">Abrufen des PowerShellGet-Moduls für PowerShell 3.0 und 4.0</span><span class="sxs-lookup"><span data-stu-id="b0897-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="b0897-110">PackageManagement-MSI</span><span class="sxs-lookup"><span data-stu-id="b0897-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="b0897-111">Herunterladen der neuesten Version aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="b0897-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="b0897-112">Bevor Sie PowerShellGet aktualisieren, sollten Sie immer den neuesten NuGet-Anbieter installieren.</span><span class="sxs-lookup"><span data-stu-id="b0897-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="b0897-113">Führen Sie hierzu den folgenden Befehl in einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="b0897-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="b0897-114">Für Systeme mit PowerShell 5.0 (oder höher) können Sie das neueste PowerShellGet-Modul installieren</span><span class="sxs-lookup"><span data-stu-id="b0897-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="b0897-115">Führen Sie hierzu unter Windows 10, Windows Server 2016 auf einem beliebigen System mit WMF 5.0 oder 5.1 oder auf einem beliebigen System mit PowerShell 6 den folgenden Befehl aus einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="b0897-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- <span data-ttu-id="b0897-116">Verwenden Sie `Update-Module`, um neuere Versionen zu beziehen.</span><span class="sxs-lookup"><span data-stu-id="b0897-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="b0897-117">Systeme mit PowerShell 3 oder PowerShell 4 mit installierter [PackageManagement-MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="b0897-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="b0897-118">Verwenden Sie das nachstehende PowerShellGet-Cmdlet aus einer PowerShell-Sitzung mit erhöhten Rechten, um die Module in einem lokalen Verzeichnis zu speichern.</span><span class="sxs-lookup"><span data-stu-id="b0897-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="b0897-119">Stellen Sie sicher, dass die Module „PowerShellGet“ und „PackageManagement“ nicht in anderen Prozessen geladen sind.</span><span class="sxs-lookup"><span data-stu-id="b0897-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="b0897-120">Löschen Sie die Inhalte der Ordner `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` und `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="b0897-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="b0897-121">Öffnen Sie die PS-Konsole erneut mit erhöhten Rechten, und führen Sie dann die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="b0897-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
