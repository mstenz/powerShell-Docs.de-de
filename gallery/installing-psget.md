---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Installieren von PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143590"
---
# <a name="installing-powershellget"></a><span data-ttu-id="7c9aa-103">Installieren von PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="7c9aa-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="7c9aa-104">PowerShellGet ist ein Modul, das zum Lieferumfang der folgenden Releases gehört:</span><span class="sxs-lookup"><span data-stu-id="7c9aa-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="7c9aa-105">[Windows 10](https://www.microsoft.com/windows) oder höher</span><span class="sxs-lookup"><span data-stu-id="7c9aa-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="7c9aa-106">[Windows Server 2016](/windows-server/windows-server) oder höher</span><span class="sxs-lookup"><span data-stu-id="7c9aa-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="7c9aa-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) oder höher</span><span class="sxs-lookup"><span data-stu-id="7c9aa-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="7c9aa-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="7c9aa-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="7c9aa-109">Herunterladen der neuesten Version aus dem PowerShell-Katalog</span><span class="sxs-lookup"><span data-stu-id="7c9aa-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="7c9aa-110">Bevor Sie **PowerShellGet** aktualisieren, sollten Sie immer den neuesten **NuGet**-Anbieter installieren.</span><span class="sxs-lookup"><span data-stu-id="7c9aa-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="7c9aa-111">Führen Sie hierzu den folgenden Befehl in einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="7c9aa-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="7c9aa-112">Für Systeme mit PowerShell 5.0 (oder höher) können Sie das neueste PowerShellGet-Modul installieren</span><span class="sxs-lookup"><span data-stu-id="7c9aa-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="7c9aa-113">Zum Installieren von PowerShellGet führen Sie unter Windows 10, Windows Server 2016 auf einem beliebigen System mit WMF 5.0 oder 5.1 oder auf einem beliebigen System mit PowerShell 6 den folgenden Befehl aus einer PowerShell-Sitzung mit erhöhten Rechten aus.</span><span class="sxs-lookup"><span data-stu-id="7c9aa-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="7c9aa-114">Verwenden Sie `Update-Module`, um neuere Versionen zu beziehen.</span><span class="sxs-lookup"><span data-stu-id="7c9aa-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a><span data-ttu-id="7c9aa-115">Systeme mit PowerShell 3 oder PowerShell 4 mit installierter PackageManagement-Vorschau</span><span class="sxs-lookup"><span data-stu-id="7c9aa-115">For systems running PowerShell 3 or PowerShell 4, that have installed the PackageManagement Preview</span></span>

1. <span data-ttu-id="7c9aa-116">Verwenden Sie `Save-Module` in einer PowerShell-Sitzung mit erhöhten Rechten, um die Module in einem lokalen Verzeichnis zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7c9aa-116">From an elevated PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. <span data-ttu-id="7c9aa-117">Stellen Sie sicher, dass die Module **PowerShellGet** und **PackageManagement** nicht in anderen Prozessen geladen sind.</span><span class="sxs-lookup"><span data-stu-id="7c9aa-117">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="7c9aa-118">Löschen Sie den Inhalt der Ordner „`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\`“ und „`$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`“.</span><span class="sxs-lookup"><span data-stu-id="7c9aa-118">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="7c9aa-119">Öffnen Sie die PowerShell-Konsole erneut mit erhöhten Rechten, und führen Sie die folgenden Befehle aus.</span><span class="sxs-lookup"><span data-stu-id="7c9aa-119">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
