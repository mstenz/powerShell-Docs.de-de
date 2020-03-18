---
title: Verwenden von PowerShell in Docker
description: Informationen zur Verwendung von in einem Docker-Image vorinstallierter PowerShell.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: 771214c719ef01fe2c8bc56a4b26c629fcad3856
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279657"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="db0e4-103">Verwenden von PowerShell in Docker</span><span class="sxs-lookup"><span data-stu-id="db0e4-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="db0e4-104">Wir veröffentlichen Docker-Images mit vorinstallierter PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db0e4-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="db0e4-105">Dieser Artikel veranschaulicht die ersten Schritte mit PowerShell im Docker-Container.</span><span class="sxs-lookup"><span data-stu-id="db0e4-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="db0e4-106">Ermitteln verfügbarer Images</span><span class="sxs-lookup"><span data-stu-id="db0e4-106">Finding available images</span></span>

<span data-ttu-id="db0e4-107">Für die veröffentlichten Images ist mindestens Docker 17.05 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="db0e4-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="db0e4-108">Es wird auch erwartet, dass Sie Docker ohne `sudo` oder lokale Administratorrechte ausführen können.</span><span class="sxs-lookup"><span data-stu-id="db0e4-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="db0e4-109">Befolgen Sie die offiziellen [Anweisungen][install] von Docker zur ordnungsgemäßen Installation von `docker`.</span><span class="sxs-lookup"><span data-stu-id="db0e4-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="db0e4-110">Die Releasecontainer leiten sich vom offiziellen Distributionsimage ab, wie z. B. `centos:7`, installieren dann die Abhängigkeiten und zuletzt das PowerShell-Paket.</span><span class="sxs-lookup"><span data-stu-id="db0e4-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="db0e4-111">Diese Container befinden sich unter [hub.docker.com/r/microsoft/powershell][docker-release].</span><span class="sxs-lookup"><span data-stu-id="db0e4-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="db0e4-112">Weitere Informationen zu diesen Docker-Images finden Sie im Repository [PowerShell-Docker][PowerShell-Docker] auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="db0e4-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="db0e4-113">Verwenden von PowerShell in einem Container</span><span class="sxs-lookup"><span data-stu-id="db0e4-113">Using PowerShell in a container</span></span>

<span data-ttu-id="db0e4-114">Die folgenden Schritte zeigen die Docker-Befehle, die zum Herunterladen des Images und zum Starten einer interaktiven PowerShell-Sitzung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="db0e4-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="db0e4-115">Entfernen des Images, sobald es nicht mehr benötigt wird</span><span class="sxs-lookup"><span data-stu-id="db0e4-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="db0e4-116">Der folgende Befehl dient zum Löschen des Docker-Containers, wenn Sie ihn nicht mehr benötigen.</span><span class="sxs-lookup"><span data-stu-id="db0e4-116">The following command is used to delete the Docker container when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="db0e4-117">Rechtliche Hinweise und Lizenzierung</span><span class="sxs-lookup"><span data-stu-id="db0e4-117">Legal and Licensing</span></span>

<span data-ttu-id="db0e4-118">PowerShell wird unter der [MIT-Lizenz][] lizenziert.</span><span class="sxs-lookup"><span data-stu-id="db0e4-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="db0e4-119">Windows Docker-Datei- und Imagelizenzen</span><span class="sxs-lookup"><span data-stu-id="db0e4-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="db0e4-120">Indem Sie das Container-Betriebssystemimage für Windows-Container anfordern und verwenden, erklären Sie sich mit den ergänzenden Lizenzbedingungen einverstanden, die auf dem Docker-Hub verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="db0e4-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="db0e4-121">[Window Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="db0e4-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="db0e4-122">[Nano Server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="db0e4-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="db0e4-123">Telemetrie</span><span class="sxs-lookup"><span data-stu-id="db0e4-123">Telemetry</span></span>

<span data-ttu-id="db0e4-124">Standardmäßig sammelt PowerShell begrenzte Telemetriedaten ohne personenbezogene Informationen, um die Entwicklung künftiger Versionen von PowerShell zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="db0e4-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="db0e4-125">Um das Senden von Telemetriedaten zu deaktivieren, erstellen Sie eine Umgebungsvariable namens `POWERSHELL_TELEMETRY_OPTOUT`, die auf den Wert `1` festgelegt wird, bevor Sie PowerShell am Installationsspeicherort starten.</span><span class="sxs-lookup"><span data-stu-id="db0e4-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="db0e4-126">Die von uns erfassten Telemetriedaten unterliegen den [Datenschutzbestimmungen von Microsoft][privacy].</span><span class="sxs-lookup"><span data-stu-id="db0e4-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT-Lizenz]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
