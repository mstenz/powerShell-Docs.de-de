---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Problembehandlung für Cmdlets
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "72352109"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="8d2e6-103">Problembehandlung für Cmdlets</span><span class="sxs-lookup"><span data-stu-id="8d2e6-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="8d2e6-104">Gewusst wie: Beheben des Fehlers „WARNUNG: Fehler beim Herunterladen des Pakets "Name Ihres Pakets"“</span><span class="sxs-lookup"><span data-stu-id="8d2e6-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="8d2e6-105">Es wurde berichtet, dass bei Ausführung von `Install-Module` oder `Update-Module` auf einigen Computern ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="8d2e6-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="8d2e6-106">Unseren Untersuchungen zufolge hängt dieses Problem mit der Netzwerkverbindung zusammen.</span><span class="sxs-lookup"><span data-stu-id="8d2e6-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="8d2e6-107">Der NuGet-Anbieter wurde vor Kurzem aktualisiert, sodass Pakete nun zuverlässig heruntergeladen werden können.</span><span class="sxs-lookup"><span data-stu-id="8d2e6-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="8d2e6-108">Befolgen Sie die unten stehenden Anweisungen, um den aktuellen Build des NuGet-Anbieters zu installieren und anschließend Ihr Modul zu installieren oder zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8d2e6-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="8d2e6-109">Im nachfolgenden Beispiel wird das Modul „Azure“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d2e6-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="8d2e6-110">Erforderliche Netzwerkendpunkte</span><span class="sxs-lookup"><span data-stu-id="8d2e6-110">Required network endpoints</span></span>

<span data-ttu-id="8d2e6-111">Die Install- und Update-Cmdlets erfordern einen Internetzugang, um eine Verbindung mit den vom PowerShell-Katalog verwendeten Netzwerkendpunkten herzustellen.</span><span class="sxs-lookup"><span data-stu-id="8d2e6-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="8d2e6-112">Stellen Sie sicher, dass Ihre Netzwerkzugriffsrichtlinien das Herstellen einer Verbindung mit den folgenden Endpunkten zulassen.</span><span class="sxs-lookup"><span data-stu-id="8d2e6-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="8d2e6-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="8d2e6-113">oneget.org</span></span>
- <span data-ttu-id="8d2e6-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="8d2e6-114">go.microsoft.com</span></span>
- <span data-ttu-id="8d2e6-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="8d2e6-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="8d2e6-116">www.powershellgallery.com</span><span class="sxs-lookup"><span data-stu-id="8d2e6-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="8d2e6-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="8d2e6-117">devopsgallerystorage.blob.core.windows.net</span></span>
