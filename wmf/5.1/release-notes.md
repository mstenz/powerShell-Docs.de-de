---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: "Anmerkungen zu dieser Version – WMF 5.1"
ms.openlocfilehash: ce9bc7791facfcc2cce9468689e88a26154bda7d
ms.sourcegitcommit: 3f49bd2e0b786e69c71393c00ad85d05a8466753
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="fcb8b-103">Windows Management Framework (WMF) 5.1 – Anmerkungen zu dieser Version</span><span class="sxs-lookup"><span data-stu-id="fcb8b-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="fcb8b-104">WMF 5.1 umfasst PowerShell, WMI und WinRM sowie SIL-Komponenten (Softwareinventurprotokollierung), die mit Windows Server 2016 veröffentlicht wurden.</span><span class="sxs-lookup"><span data-stu-id="fcb8b-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="fcb8b-105">WMF 5.1 kann auf Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 und 2012 R2 installiert werden und bietet gegenüber WMF 5.0 RTM eine Reihe von Vorteilen. Dazu zählen u. a.:</span><span class="sxs-lookup"><span data-stu-id="fcb8b-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="fcb8b-106">Neue Cmdlets: lokale Benutzer und Gruppen; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="fcb8b-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="fcb8b-107">PowerShellGet-Verbesserungen wie z. B. die Durchsetzung von signierten Modulen und die Installation von JEA-Modulen</span><span class="sxs-lookup"><span data-stu-id="fcb8b-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="fcb8b-108">Bei PackageManagement wurde Unterstützung für Container, CBS-Setup, EXE-basiertes Setup und CAB-Pakete hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="fcb8b-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="fcb8b-109">Debuggingverbesserungen für DSC und PowerShell-Klassen</span><span class="sxs-lookup"><span data-stu-id="fcb8b-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="fcb8b-110">Sicherheitsverbesserungen wie u. a. die Durchsetzung von katalogsignierten Modulen vom Pullserver und bei Verwendung von PowerShellGet-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="fcb8b-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="fcb8b-111">Antworten auf verschiedene Benutzeranfragen und zu Problemen</span><span class="sxs-lookup"><span data-stu-id="fcb8b-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="fcb8b-112">**Wichtige Hinweise:**</span><span class="sxs-lookup"><span data-stu-id="fcb8b-112">**Important notes:**</span></span>

- <span data-ttu-id="fcb8b-113">**Für WMF 5.1 ist .NET Framework 4.5.2 erforderlich** (oder höher).</span><span class="sxs-lookup"><span data-stu-id="fcb8b-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="fcb8b-114">Die Installation ist erfolgreich, wichtige Features können jedoch nicht ausgeführt werden, wenn .NET 4.5.2 (oder höher) nicht installiert ist.</span><span class="sxs-lookup"><span data-stu-id="fcb8b-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="fcb8b-115">Anweisungen finden Sie im Thema [Installieren und Konfigurieren von WMF 5.1 (Preview)](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure).</span><span class="sxs-lookup"><span data-stu-id="fcb8b-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="fcb8b-116">WMF 5.1 Preview muss vor der Installation von WMF 5.1 RTM deinstalliert werden.</span><span class="sxs-lookup"><span data-stu-id="fcb8b-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="fcb8b-117">WMF 5.1 kann direkt über WMF 5.0 oder WMF 4.0 installiert werden.</span><span class="sxs-lookup"><span data-stu-id="fcb8b-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="fcb8b-118">Es ist __nicht erforderlich__, WMF 4.0 vor der Installation von WMF 5.1 unter Windows 7 und Windows Server 2008 R2 zu installieren.</span><span class="sxs-lookup"><span data-stu-id="fcb8b-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="fcb8b-119">Dieses Problem der Preview-Version von WMF 5.1 wurde behoben.</span><span class="sxs-lookup"><span data-stu-id="fcb8b-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


