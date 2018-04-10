---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Problembehandlung von Cmdlets | MSDN
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="4bbfd-103">Wie lässt sich das Problem „WARNUNG: Fehler beim Herunterladen des Pakets ‚Name Ihres Pakets‘“ lösen?</span><span class="sxs-lookup"><span data-stu-id="4bbfd-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="4bbfd-104">Uns wurde mitgeteilt, dass bei „Install-Module“ oder „Update-Module“ auf einigen Computern Fehler ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="4bbfd-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="4bbfd-105">Unseren Untersuchungen zufolge hängt dieses Problem mit der Netzwerkverbindung zusammen.</span><span class="sxs-lookup"><span data-stu-id="4bbfd-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="4bbfd-106">Der NuGet-Anbieter wurde vor Kurzem aktualisiert, sodass Pakete nun zuverlässig heruntergeladen werden können.</span><span class="sxs-lookup"><span data-stu-id="4bbfd-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="4bbfd-107">Befolgen Sie die unten stehenden Anweisungen, um den aktuellen Build des NuGet-Anbieters zu installieren und anschließend Ihr Modul zu installieren oder zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4bbfd-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="4bbfd-108">Im nachfolgenden Beispiel wird das Modul „Azure“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="4bbfd-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```