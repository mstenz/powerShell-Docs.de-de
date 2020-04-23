---
title: Übermitteln von Pull Requests
description: In diesem Artikel wird erläutert, wie Pull Requests an das PowerShell-Docs-Team übermittelt werden.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 2600049b06da5ad4869b6ff335f00bc40c2d1c22
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "79060235"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="55689-103">Übermitteln von Pull Requests</span><span class="sxs-lookup"><span data-stu-id="55689-103">How to submit pull requests</span></span>

<span data-ttu-id="55689-104">Wenn Sie inhaltliche Änderungen vornehmen möchten, übermitteln Sie einen Pull Request (PR) aus Ihrer Fork.</span><span class="sxs-lookup"><span data-stu-id="55689-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="55689-105">Eine Pull Request muss überprüft werden, bevor er gemergt werden kann.</span><span class="sxs-lookup"><span data-stu-id="55689-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="55689-106">Um optimale Ergebnisse zu erzielen, überprüfen Sie die [Checkliste für die Bearbeitung](editorial-checklist.md), bevor Sie Ihren Pull Request einreichen.</span><span class="sxs-lookup"><span data-stu-id="55689-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="55689-107">Abzielen auf die richtige Branch</span><span class="sxs-lookup"><span data-stu-id="55689-107">Target the correct branch</span></span>

<span data-ttu-id="55689-108">Alle Pull Requests müssen den Branch `staging` als Ziel haben.</span><span class="sxs-lookup"><span data-stu-id="55689-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="55689-109">Änderungen dürfen auf keinen Fall an den Branch `live` übermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="55689-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="55689-110">Änderungen, die im Branch `staging` vorgenommen werden, werden in den Branch `live` gemergt, wobei alle Änderungen an `live` überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="55689-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="55689-111">Wenn Sie eine Änderung einreichen, die nur für eine unveröffentlichte Version von PowerShell gilt, suchen Sie nach einem Releasebranch für diese Version.</span><span class="sxs-lookup"><span data-stu-id="55689-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="55689-112">Ihr PR muss auf den Releasebranch abzielen.</span><span class="sxs-lookup"><span data-stu-id="55689-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="55689-113">Releasebranches weisen das folgende Namensmuster auf: `release-<version>`.</span><span class="sxs-lookup"><span data-stu-id="55689-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="55689-114">Verbessern des Pull Request-Prozesses für alle Beteiligten</span><span class="sxs-lookup"><span data-stu-id="55689-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="55689-115">Je einfacher und zielgerichteter Sie Ihren PR gestalten, desto schneller kann er überprüft und gemergt werden.</span><span class="sxs-lookup"><span data-stu-id="55689-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="55689-116">Vermeiden von Branches, die eine große Anzahl von Dateien aktualisieren oder unzusammenhängende Änderungen enthalten</span><span class="sxs-lookup"><span data-stu-id="55689-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="55689-117">Vermeiden Sie das Erstellen von PRs mit unzusammenhängenden Änderungen.</span><span class="sxs-lookup"><span data-stu-id="55689-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="55689-118">Trennen Sie kleinere Updates bestehender Artikel von neuen Artikeln oder größeren Neufassungen.</span><span class="sxs-lookup"><span data-stu-id="55689-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="55689-119">Arbeiten Sie an diesen Änderungen in separaten Bearbeitungsbranches.</span><span class="sxs-lookup"><span data-stu-id="55689-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="55689-120">Bei Massenänderungen werden PRs mit einer großen Anzahl geänderter Dateien erstellt.</span><span class="sxs-lookup"><span data-stu-id="55689-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="55689-121">Beschränken Sie Ihre PRs auf maximal 50 geänderte Dateien.</span><span class="sxs-lookup"><span data-stu-id="55689-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="55689-122">Große PRs sind schwer zu überprüfen und anfälliger für Fehler.</span><span class="sxs-lookup"><span data-stu-id="55689-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="55689-123">Umbenennen oder Löschen von Dateien</span><span class="sxs-lookup"><span data-stu-id="55689-123">Renaming or deleting files</span></span>

<span data-ttu-id="55689-124">Wenn Sie Dateien umbenennen oder löschen, muss dem PR ein Issue zugeordnet sein.</span><span class="sxs-lookup"><span data-stu-id="55689-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="55689-125">In diesem Issue muss die Notwendigkeit des Umbenennens oder Löschens der Dateien diskutiert werden.</span><span class="sxs-lookup"><span data-stu-id="55689-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="55689-126">Vermeiden Sie die Vermischung von Inhaltsergänzungen oder -änderungen mit Dateiumbenennungen und -löschungen.</span><span class="sxs-lookup"><span data-stu-id="55689-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="55689-127">Dateien, die umbenannt oder gelöscht werden, müssen der Masterumleitungsdatei hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="55689-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="55689-128">Nach Möglichkeit sollten Sie auch alle Dateien aktualisieren, die mit dem umbenannten oder gelöschten Inhalt verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="55689-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="55689-129">Dazu zählen auch Inhaltsverzeichnisdateien.</span><span class="sxs-lookup"><span data-stu-id="55689-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="55689-130">Validierungsdienst für auf die Dokumentation bezogene PRs</span><span class="sxs-lookup"><span data-stu-id="55689-130">Docs PR validation service</span></span>

<span data-ttu-id="55689-131">Dieser Dienst ist eine GitHub-App, die Validierungsregeln auf die Dateien in einem PR anwendet.</span><span class="sxs-lookup"><span data-stu-id="55689-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="55689-132">Sie müssen alle vom Validierungsdienst gemeldeten Fehler oder Warnungen (siehe Ausnahmen) beseitigen.</span><span class="sxs-lookup"><span data-stu-id="55689-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="55689-133">Die folgenden Warnungen können ignoriert werden:</span><span class="sxs-lookup"><span data-stu-id="55689-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="55689-134">Sie erkennen das folgende Verhalten:</span><span class="sxs-lookup"><span data-stu-id="55689-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="55689-135">Sie übermitteln einen PR.</span><span class="sxs-lookup"><span data-stu-id="55689-135">You submit a PR.</span></span>
1. <span data-ttu-id="55689-136">Im GitHub-Kommentar, der den Status Ihres PR anzeigt, sehen Sie den für das Repository aktivierten Status von „Überprüfungen“.</span><span class="sxs-lookup"><span data-stu-id="55689-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repo.</span></span> <span data-ttu-id="55689-137">Beachten Sie, dass in diesem Beispiel zwei Überprüfungen aktiviert sind: „Commit Validation“ und „OpenPublishing.Build“:</span><span class="sxs-lookup"><span data-stu-id="55689-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![einige Überprüfungen sind fehlgeschlagen](media/pull-requests/validation-failed.png)

   <span data-ttu-id="55689-139">Der Build kann fortgesetzt werden, auch wenn die Überprüfung des Commits fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="55689-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="55689-140">Klicken Sie auf **Details**, um weitere Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="55689-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="55689-141">Auf der Seite „Details“ werden alle fehlgeschlagenen Validierungsprüfungen angezeigt, und zwar mit Informationen zur Behebung der Issues.</span><span class="sxs-lookup"><span data-stu-id="55689-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="55689-142">Wenn die Validierung erfolgreich ist, wird dem PR der folgende Kommentar hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="55689-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![Buildvalidierung](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="55689-144">Wenn Sie ein externer Mitwirkender (kein Mitarbeiter von Microsoft) sind, haben Sie keinen Zugriff auf die detaillierten Buildberichte oder Vorschaulinks.</span><span class="sxs-lookup"><span data-stu-id="55689-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="55689-145">Wenn der PR von einem Mitglied des PowerShell-Docs-Teams überprüft wird, werden Sie möglicherweise aufgefordert, Änderungen vorzunehmen oder Probleme zu beheben, die im Validierungsbericht markiert sind.</span><span class="sxs-lookup"><span data-stu-id="55689-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="55689-146">Das PowerShell-Docs-Team kann Ihnen helfen zu verstehen, wie diese Probleme für künftige Einreichungen behoben und vermieden werden können.</span><span class="sxs-lookup"><span data-stu-id="55689-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="55689-147">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="55689-147">Next steps</span></span>

[<span data-ttu-id="55689-148">Styleguide für die PowerShell-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="55689-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="55689-149">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="55689-149">Additional resources</span></span>

[<span data-ttu-id="55689-150">Verwalten von Pull Requests</span><span class="sxs-lookup"><span data-stu-id="55689-150">How we manage pull requests</span></span>](managing-pull-requests.md)
