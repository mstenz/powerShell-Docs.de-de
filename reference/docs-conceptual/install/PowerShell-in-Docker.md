---
title: Verwenden von PowerShell in Docker
description: Informationen zur Verwendung von in einem Docker-Image vorinstallierter PowerShell.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80646374"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="d207b-103">Verwenden von PowerShell in Docker</span><span class="sxs-lookup"><span data-stu-id="d207b-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="d207b-104">Wir veröffentlichen Docker-Images mit vorinstallierter PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d207b-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="d207b-105">Dieser Artikel veranschaulicht die ersten Schritte mit PowerShell im Docker-Container.</span><span class="sxs-lookup"><span data-stu-id="d207b-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="d207b-106">Ermitteln verfügbarer Images</span><span class="sxs-lookup"><span data-stu-id="d207b-106">Finding available images</span></span>

<span data-ttu-id="d207b-107">Für die veröffentlichten Images ist mindestens Docker 17.05 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d207b-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="d207b-108">Es wird auch erwartet, dass Sie Docker ohne `sudo` oder lokale Administratorrechte ausführen können.</span><span class="sxs-lookup"><span data-stu-id="d207b-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="d207b-109">Befolgen Sie die offiziellen [Anweisungen][install] von Docker zur ordnungsgemäßen Installation von `docker`.</span><span class="sxs-lookup"><span data-stu-id="d207b-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="d207b-110">Die Releasecontainer leiten sich vom offiziellen Distributionsimage ab, wie z. B. `centos:7`, installieren dann die Abhängigkeiten und zuletzt das PowerShell-Paket.</span><span class="sxs-lookup"><span data-stu-id="d207b-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="d207b-111">Diese Container befinden sich unter [hub.docker.com/r/microsoft/powershell][docker-release].</span><span class="sxs-lookup"><span data-stu-id="d207b-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="d207b-112">Weitere Informationen zu diesen Docker-Images finden Sie im Repository [PowerShell-Docker][PowerShell-Docker] auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="d207b-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="d207b-113">Verwenden von PowerShell in einem Container</span><span class="sxs-lookup"><span data-stu-id="d207b-113">Using PowerShell in a container</span></span>

<span data-ttu-id="d207b-114">Die folgenden Schritte zeigen die Docker-Befehle, die zum Herunterladen des Images und zum Starten einer interaktiven PowerShell-Sitzung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="d207b-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="d207b-115">Entfernen des Images, sobald es nicht mehr benötigt wird</span><span class="sxs-lookup"><span data-stu-id="d207b-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="d207b-116">Der folgende Befehl dient zum Löschen des Docker-Images, wenn Sie dieses nicht mehr benötigen.</span><span class="sxs-lookup"><span data-stu-id="d207b-116">The following command is used to delete the Docker image when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="d207b-117">Rechtliche Hinweise und Lizenzierung</span><span class="sxs-lookup"><span data-stu-id="d207b-117">Legal and Licensing</span></span>

<span data-ttu-id="d207b-118">PowerShell wird unter der [MIT-Lizenz][] lizenziert.</span><span class="sxs-lookup"><span data-stu-id="d207b-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="d207b-119">Windows Docker-Datei- und Imagelizenzen</span><span class="sxs-lookup"><span data-stu-id="d207b-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="d207b-120">Indem Sie das Container-Betriebssystemimage für Windows-Container anfordern und verwenden, erklären Sie sich mit den ergänzenden Lizenzbedingungen einverstanden, die auf dem Docker-Hub verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="d207b-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="d207b-121">[Window Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="d207b-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="d207b-122">[Nano Server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="d207b-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="d207b-123">Telemetrie</span><span class="sxs-lookup"><span data-stu-id="d207b-123">Telemetry</span></span>

<span data-ttu-id="d207b-124">Standardmäßig sammelt PowerShell begrenzte Telemetriedaten ohne personenbezogene Informationen, um die Entwicklung künftiger Versionen von PowerShell zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d207b-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="d207b-125">Um das Senden von Telemetriedaten zu deaktivieren, erstellen Sie eine Umgebungsvariable namens `POWERSHELL_TELEMETRY_OPTOUT`, die auf den Wert `1` festgelegt wird, bevor Sie PowerShell am Installationsspeicherort starten.</span><span class="sxs-lookup"><span data-stu-id="d207b-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="d207b-126">Die von uns erfassten Telemetriedaten unterliegen den [Datenschutzbestimmungen von Microsoft][privacy].</span><span class="sxs-lookup"><span data-stu-id="d207b-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

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
