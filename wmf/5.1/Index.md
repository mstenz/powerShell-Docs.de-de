---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Anmerkungen zu dieser Version – WMF 5.1
ms.openlocfilehash: 3081d200f0c6aac6074719bb1c204900aabf96c2
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522904"
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="cc31d-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="cc31d-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="cc31d-104">WMF ermöglicht es Benutzern, bestehende Windows-Systeme auf die Versionen der Komponenten von PowerShell, WMI, WinRM und der Softwareinventurprotokollierung zu aktualisieren, die mit Windows Server 2016 veröffentlicht wurden.</span><span class="sxs-lookup"><span data-stu-id="cc31d-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="cc31d-105">WMF 5.1 kann auf Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 und 2012 R2 installiert werden und bietet gegenüber WMF 5.0 RTM eine Reihe von Vorteilen. Dazu zählen u. a.:</span><span class="sxs-lookup"><span data-stu-id="cc31d-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="cc31d-106">Neue Cmdlets: lokale Benutzer und Gruppen; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="cc31d-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="cc31d-107">PowerShellGet-Verbesserungen wie z. B. die Durchsetzung von signierten Modulen und die Installation von JEA-Modulen</span><span class="sxs-lookup"><span data-stu-id="cc31d-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="cc31d-108">Bei PackageManagement wurde Unterstützung für Container, CBS-Setup, EXE-basiertes Setup und CAB-Pakete hinzugefügt</span><span class="sxs-lookup"><span data-stu-id="cc31d-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="cc31d-109">Debuggingverbesserungen für DSC und PowerShell-Klassen</span><span class="sxs-lookup"><span data-stu-id="cc31d-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="cc31d-110">Sicherheitsverbesserungen wie u. a. die Durchsetzung von katalogsignierten Modulen vom Pullserver und bei Verwendung von PowerShellGet-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="cc31d-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="cc31d-111">Antworten auf verschiedene Benutzeranfragen und zu Problemen</span><span class="sxs-lookup"><span data-stu-id="cc31d-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="cc31d-112">Weitere Informationen zu den Neuerungen in dieser Version finden Sie in den Themen, die unter [New Scenarios and Features (Neue Szenarios und Features)](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features) aufgelistet sind.</span><span class="sxs-lookup"><span data-stu-id="cc31d-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="cc31d-113">Das Thema [Install and Configure (Installieren und Konfigurieren)](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) listet die Anforderungen auf und enthält Installationsanweisungen für WMF.</span><span class="sxs-lookup"><span data-stu-id="cc31d-113">The [Install and Configure](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="cc31d-114">Das Thema [Compatibility (Kompatibilität)](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) listet auf, welche Versionen von WMF auf welchen Windows-Versionen installiert werden können.</span><span class="sxs-lookup"><span data-stu-id="cc31d-114">The [Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="cc31d-115">Das Thema [Product Compatibility (Produktkompatibilität)](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) listet die Microsoft-Anwendungen auf, die derzeit noch nicht für die Verwendung mit WMF 5.1 genehmigt wurden.</span><span class="sxs-lookup"><span data-stu-id="cc31d-115">[Product Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="cc31d-116">Weitere Details zu den Komponenten von WMF finden Sie in der MSDN-Dokumentation:</span><span class="sxs-lookup"><span data-stu-id="cc31d-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="cc31d-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="cc31d-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/powershell/)
- <span data-ttu-id="cc31d-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="cc31d-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="cc31d-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="cc31d-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="cc31d-120">[Softwareinventurprotokollierung](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="cc31d-120">[Software Inventory Logging](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span></span>
