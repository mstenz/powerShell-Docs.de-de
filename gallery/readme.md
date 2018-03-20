---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Der PowerShell-Katalog | MSDN
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="4cf7e-103">Der PowerShell-Katalog | MSDN</span><span class="sxs-lookup"><span data-stu-id="4cf7e-103">The PowerShell Gallery</span></span>

<span data-ttu-id="4cf7e-104">Der PowerShell-Katalog ist das zentrale Repository für PowerShell-Inhalte.</span><span class="sxs-lookup"><span data-stu-id="4cf7e-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="4cf7e-105">Im Katalog finden Sie neue PowerShell-Befehle oder DSC-Ressourcen (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="4cf7e-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="4cf7e-106">Übersicht über PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4cf7e-106">PowerShellGet Overview</span></span>

<span data-ttu-id="4cf7e-107">Das PowerShellGet-Modul enthält Cmdlets zum Ermitteln, Installieren, Aktualisieren und Veröffentlichen von PowerShell-Artefakten wie Modulen, DSC-Ressourcen, Rollenfunktionen und Skripts über den [PowerShell-Katalog](https://www.PowerShellGallery.com) und andere private Repositorys.</span><span class="sxs-lookup"><span data-stu-id="4cf7e-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="4cf7e-108">Erste Schritte mit dem Katalog</span><span class="sxs-lookup"><span data-stu-id="4cf7e-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="4cf7e-109">Für die Installation von Elementen über den Katalog ist die neueste Version des PowerShellGet-Moduls erforderlich, die in Windows 10, im Windows Management Framework (WMF) 5.0 oder im MSI-basierten Installer (für PowerShell 3 und 4) verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="4cf7e-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="4cf7e-110">[**Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409) abrufen</span><span class="sxs-lookup"><span data-stu-id="4cf7e-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="4cf7e-111">[**WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) abrufen</span><span class="sxs-lookup"><span data-stu-id="4cf7e-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="4cf7e-112">**MSI-Installer abrufen**</span><span class="sxs-lookup"><span data-stu-id="4cf7e-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="4cf7e-113">Mit dem neuesten [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)-Modul haben Sie folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="4cf7e-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="4cf7e-114">Durchsuchen der Elemente im Katalog mit [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) und [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="4cf7e-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="4cf7e-115">Speichern von Elementen aus dem Katalog in Ihrem System mit [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) und [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="4cf7e-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="4cf7e-116">Installieren von Elementen aus dem Katalog mit [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) und [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="4cf7e-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="4cf7e-117">Hochladen von Elementen im Katalog mit [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) und [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="4cf7e-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="4cf7e-118">Hinzufügen Ihres eigenen benutzerdefinierten Repositorys mit [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="4cf7e-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="4cf7e-119">Sehen Sie sich die Seite [Erste Schritte](psgallery/psgallery_gettingstarted.md) an, um weitere Informationen zur Verwendung von PowerShellGet-Befehlen mit dem Katalog zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="4cf7e-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="4cf7e-120">Sie können auch *Update-Help -Module PowerShellGet* ausführen, um die lokale Hilfe für diese Befehle zu installieren.</span><span class="sxs-lookup"><span data-stu-id="4cf7e-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="4cf7e-121">Unterstützte Betriebssysteme</span><span class="sxs-lookup"><span data-stu-id="4cf7e-121">Supported Operating Systems</span></span>

<span data-ttu-id="4cf7e-122">Für das **PowerShellGet**-Modul ist **PowerShell 3.0 oder neuer** erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4cf7e-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="4cf7e-123">Aus diesem Grund erfordert **PowerShellGet** eines der folgenden Betriebssysteme:</span><span class="sxs-lookup"><span data-stu-id="4cf7e-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="4cf7e-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="4cf7e-124">Windows 10</span></span>
- <span data-ttu-id="4cf7e-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="4cf7e-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="4cf7e-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="4cf7e-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="4cf7e-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="4cf7e-127">Windows 7 SP1</span></span>
- <span data-ttu-id="4cf7e-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="4cf7e-128">Windows Server 2016</span></span>
- <span data-ttu-id="4cf7e-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4cf7e-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="4cf7e-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="4cf7e-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="4cf7e-131">Für **PowerShellGet** ist außerdem .NET Framework 4.5 oder höher erforderlich.</span><span class="sxs-lookup"><span data-stu-id="4cf7e-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="4cf7e-132">Von [hier](https://msdn.microsoft.com/library/5a4x27ek.aspx) können Sie .NET Framework 4.5 oder höher installieren.</span><span class="sxs-lookup"><span data-stu-id="4cf7e-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="4cf7e-133">Sie haben eine Frage?</span><span class="sxs-lookup"><span data-stu-id="4cf7e-133">Got a question?</span></span> <span data-ttu-id="4cf7e-134">Haben Sie Feedback?</span><span class="sxs-lookup"><span data-stu-id="4cf7e-134">Have feedback?</span></span>

<span data-ttu-id="4cf7e-135">Weitere Informationen zum PowerShell-Katalog und zu PowerShellGet finden Sie auf der Seite [Erste Schritte](psgallery/psgallery_gettingstarted.md).</span><span class="sxs-lookup"><span data-stu-id="4cf7e-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="4cf7e-136">Stellen Sie Feedback bereit, und melden Sie Probleme über [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="4cf7e-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

