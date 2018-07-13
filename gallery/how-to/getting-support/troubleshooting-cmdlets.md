---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Problembehandlung für Cmdlets
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892473"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="dfa40-103">Problembehandlung für Cmdlets</span><span class="sxs-lookup"><span data-stu-id="dfa40-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="dfa40-104">Gewusst wie: Beheben des Fehlers „WARNUNG: Fehler beim Herunterladen des Pakets "Name Ihres Pakets"“</span><span class="sxs-lookup"><span data-stu-id="dfa40-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="dfa40-105">Es wurde berichtet, dass bei Ausführung von `Install-Module` oder `Update-Module` auf einigen Computern ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="dfa40-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="dfa40-106">Unseren Untersuchungen zufolge hängt dieses Problem mit der Netzwerkverbindung zusammen.</span><span class="sxs-lookup"><span data-stu-id="dfa40-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="dfa40-107">Der NuGet-Anbieter wurde vor Kurzem aktualisiert, sodass Pakete nun zuverlässig heruntergeladen werden können.</span><span class="sxs-lookup"><span data-stu-id="dfa40-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="dfa40-108">Befolgen Sie die unten stehenden Anweisungen, um den aktuellen Build des NuGet-Anbieters zu installieren und anschließend Ihr Modul zu installieren oder zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="dfa40-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="dfa40-109">Im nachfolgenden Beispiel wird das Modul „Azure“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="dfa40-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```