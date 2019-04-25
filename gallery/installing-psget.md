---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installieren von PowerShellGet
ms.openlocfilehash: 23a53a9117c9f6a7ad157b635cd7ff4b3b3444c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075272"
---
# <a name="installing-powershellget"></a><span data-ttu-id="8892b-103">Installieren von PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8892b-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="8892b-104">PowerShellGet ist ein Modul, das zum Lieferumfang der folgenden Releases gehört:</span><span class="sxs-lookup"><span data-stu-id="8892b-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="8892b-105">[Windows 10](https://www.microsoft.com/windows) oder höher</span><span class="sxs-lookup"><span data-stu-id="8892b-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="8892b-106">[Windows Server 2016](/windows-server/windows-server) oder höher</span><span class="sxs-lookup"><span data-stu-id="8892b-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="8892b-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) oder höher</span><span class="sxs-lookup"><span data-stu-id="8892b-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="8892b-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="8892b-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="8892b-109">Abrufen des PowerShellGet-Moduls für PowerShell 3.0 und 4.0</span><span class="sxs-lookup"><span data-stu-id="8892b-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="8892b-110">PackageManagement-MSI</span><span class="sxs-lookup"><span data-stu-id="8892b-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="8892b-111">Herunterladen der neuesten Version aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="8892b-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="8892b-112">Bevor Sie PowerShellGet aktualisieren, sollten Sie immer den neuesten NuGet-Anbieter installieren.</span><span class="sxs-lookup"><span data-stu-id="8892b-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="8892b-113">Führen Sie hierzu den folgenden Befehl in einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="8892b-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="8892b-114">Für Systeme mit PowerShell 5.0 (oder höher) können Sie das neueste PowerShellGet-Modul installieren</span><span class="sxs-lookup"><span data-stu-id="8892b-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="8892b-115">Führen Sie hierzu unter Windows 10, Windows Server 2016 auf einem beliebigen System mit WMF 5.0 oder 5.1 oder auf einem beliebigen System mit PowerShell 6 den folgenden Befehl aus einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="8892b-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="8892b-116">Verwenden Sie `Update-Module`, um neuere Versionen zu beziehen.</span><span class="sxs-lookup"><span data-stu-id="8892b-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="8892b-117">Systeme mit PowerShell 3 oder PowerShell 4 mit installierter [PackageManagement-MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="8892b-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="8892b-118">Verwenden Sie das nachstehende PowerShellGet-Cmdlet aus einer PowerShell-Sitzung mit erhöhten Rechten, um die Module in einem lokalen Verzeichnis zu speichern.</span><span class="sxs-lookup"><span data-stu-id="8892b-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="8892b-119">Stellen Sie sicher, dass die Module „PowerShellGet“ und „PackageManagement“ nicht in anderen Prozessen geladen sind.</span><span class="sxs-lookup"><span data-stu-id="8892b-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="8892b-120">Löschen Sie die Inhalte der Ordner `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` und `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="8892b-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="8892b-121">Öffnen Sie die PS-Konsole erneut mit erhöhten Rechten, und führen Sie dann die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="8892b-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
