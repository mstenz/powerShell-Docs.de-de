---
ms.openlocfilehash: 84b29953f09eb62eb30f52d84b087eb4f1f90eed
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470648"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="361ce-101">Microsoft Open-Source-Verhaltenskodex</span><span class="sxs-lookup"><span data-stu-id="361ce-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="361ce-102">Dieses Projekt hat den [Microsoft Open Source Code of Conduct (Microsoft Open-Source-Verhaltenskodex)](https://opensource.microsoft.com/codeofconduct/) übernommen.</span><span class="sxs-lookup"><span data-stu-id="361ce-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="361ce-103">Weitere Informationen finden Sie unter [Code of Conduct FAQ (FAQ zum Verhaltenskodex)](https://opensource.microsoft.com/codeofconduct/faq/). Alternativ können Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com](mailto:opencode@microsoft.com) wenden.</span><span class="sxs-lookup"><span data-stu-id="361ce-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="361ce-106">Buildstatus</span><span class="sxs-lookup"><span data-stu-id="361ce-106">Build Status</span></span>

| <span data-ttu-id="361ce-107">Live-Branch</span><span class="sxs-lookup"><span data-stu-id="361ce-107">Live Branch</span></span> | <span data-ttu-id="361ce-108">Staging-Branch</span><span class="sxs-lookup"><span data-stu-id="361ce-108">Staging Branch</span></span> |
|:------------|:---------------|
| <span data-ttu-id="361ce-109">[![live-badge][]][live-badge]</span><span class="sxs-lookup"><span data-stu-id="361ce-109">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="361ce-110">[![staging-badge][]][staging-badge]</span><span class="sxs-lookup"><span data-stu-id="361ce-110">[![staging-badge][]][staging-badge]</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="361ce-111">PowerShell-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="361ce-111">PowerShell Documentation</span></span>

<span data-ttu-id="361ce-112">Willkommen im Repository der offiziellen PowerShell-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="361ce-112">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="361ce-113">Repository-Struktur</span><span class="sxs-lookup"><span data-stu-id="361ce-113">Repository Structure</span></span>

<span data-ttu-id="361ce-114">In diesem Repository befinden sich diese Ordner auf oberster Ebene, die jeweils eine Dokumentenmappe enthalten, die in der [Microsoft-Dokumentation](https://docs.microsoft.com/powershell) veröffentlicht wird.</span><span class="sxs-lookup"><span data-stu-id="361ce-114">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="361ce-115">[/developer/](https://docs.microsoft.com/powershell/developer/) enthält in Zukunft die Dokumentation des PowerShell SDKs</span><span class="sxs-lookup"><span data-stu-id="361ce-115">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="361ce-116">Diese Inhalte werden derzeit aus MSDN migriert.</span><span class="sxs-lookup"><span data-stu-id="361ce-116">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="361ce-117">[/dsc/](https://docs.microsoft.com/powershell/dsc/) für die Funktion Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="361ce-117">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="361ce-118">[/gallery/](https://docs.microsoft.com/powershell/gallery) für den [PowerShell-Katalog](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="361ce-118">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="361ce-119">[/jea/](https://docs.microsoft.com/powershell/jea/) für die Funktion Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="361ce-119">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="361ce-120">[/reference/](https://docs.microsoft.com/powershell/scripting/) für die konzeptuellen Themen und den Modulverweis von PowerShell für die Versionen 3.0, 4.0, 5.0, 5.1 und 6.0.</span><span class="sxs-lookup"><span data-stu-id="361ce-120">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="361ce-121">Dieser Inhalt ist auch die Quelle von Hilfeinhalten, die vom `Get-Help`-Cmdlet abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="361ce-121">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="361ce-122">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) enthält Versionshinweise für Windows Management Framework, das Paket, das für die Verteilung neuer Versionen von PowerShell an frühere Versionen von Windows verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="361ce-122">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="361ce-123">Beiträge</span><span class="sxs-lookup"><span data-stu-id="361ce-123">Contributing</span></span>

<span data-ttu-id="361ce-124">Beiträge zu diesem Repository werden aktiv über [Pullanforderungen](https://help.github.com/articles/using-pull-requests/) im *Staging*-Branch zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="361ce-124">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="361ce-125">Beachten Sie, dass Sie vor der Übermittlung einer Pullanforderung [einen Beitragslizenzvertrags unterschreiben](https://cla.microsoft.com/) müssen, um sicherzustellen, dass die Community Ihre Einsendungen kostenlos verwenden darf.</span><span class="sxs-lookup"><span data-stu-id="361ce-125">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="361ce-126">Weitere Informationen zu Beiträgen finden Sie in unserem [Handbuch für Mitwirkende](CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="361ce-126">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="361ce-127">Das Handbuch für Mitwirkende enthält ausführliche Informationen zum Erstellen von Beiträgen zur Dokumentation, Stil- und Formatierungsvorgaben sowie Vorschlagen von Tools.</span><span class="sxs-lookup"><span data-stu-id="361ce-127">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="361ce-128">Verwenden Sie die Vorlagen für Probleme und Pullanforderungen, um die Dokumentation über Versionen hinweg konsistent zu halten.</span><span class="sxs-lookup"><span data-stu-id="361ce-128">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="361ce-129">Lizenzen</span><span class="sxs-lookup"><span data-stu-id="361ce-129">Licenses</span></span>

<span data-ttu-id="361ce-130">Es gibt zwei Lizenzdateien für dieses Projekt.</span><span class="sxs-lookup"><span data-stu-id="361ce-130">There are two license files for this project.</span></span>
<span data-ttu-id="361ce-131">Die MIT-Lizenz gilt für den Code, der in diesem Repository enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="361ce-131">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="361ce-132">Die Creative Commons-Lizenz gilt für die Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="361ce-132">The Creative Commons license applies to the documentation.</span></span>