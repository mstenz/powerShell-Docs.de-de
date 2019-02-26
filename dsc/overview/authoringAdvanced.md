---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Erstellen erweiterter DSC-Ressourcen für Komposition und Zusammenarbeit
ms.openlocfilehash: 3e40ba94de0a53c1c9663553c4ec443b5e0df3fd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678778"
---
# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a><span data-ttu-id="e7cfe-103">Erstellen erweiterter DSC-Ressourcen für Komposition und Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="e7cfe-103">Advanced DSC Authoring for Composition and Collaboration</span></span>

<span data-ttu-id="e7cfe-104">In diesem Artikel werden die verschiedenen Ansätze beschrieben, die für das Kombinieren von Konfigurationen und Ressourcen verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="e7cfe-105">Die einzelnen Szenarios haben alle das gleiche Ziel: Reduzieren der Komplexität, wenn zum Erreichen des Endstatus einer Serverbereitstellung mehrere Konfigurationen bevorzugt werden.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="e7cfe-106">Ein Beispiel hierfür wären mehrere Teams, die zum Ergebnis einer Serverbereitstellung beitragen, wie z.B. ein Anwendungsbesitzer, der den Anwendungszustand beibehält, und ein zentrales Team, das die Änderungen in Sicherheitsbaselines veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="e7cfe-107">Die Einzelheiten der einzelnen Ansätze, einschließlich der Vorteile und Risiken, werden hier näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Pipeline](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="e7cfe-109">Techniken zur kollaborativen Dokumenterstellung</span><span class="sxs-lookup"><span data-stu-id="e7cfe-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="e7cfe-110">Im lokalen Konfigurations-Manager sind zwei Lösungen integriert, die dieses Konzept ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="e7cfe-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="e7cfe-111">Konzept</span><span class="sxs-lookup"><span data-stu-id="e7cfe-111">Concept</span></span> | <span data-ttu-id="e7cfe-112">Detaillierte Informationen</span><span class="sxs-lookup"><span data-stu-id="e7cfe-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="e7cfe-113">Teilkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="e7cfe-113">Partial Configurations</span></span> | [<span data-ttu-id="e7cfe-114">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="e7cfe-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="e7cfe-115">Zusammengesetzte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="e7cfe-115">Composite Resources</span></span> | [<span data-ttu-id="e7cfe-116">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="e7cfe-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="e7cfe-117">Grundlegendes zu den Auswirkungen der einzelnen Ansätze</span><span class="sxs-lookup"><span data-stu-id="e7cfe-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="e7cfe-118">Beide Lösungen können für die Verwaltung des Ergebnisses einer Serverbereitstellung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="e7cfe-119">Die Auswirkungen bei der Verwendung der einzelnen Ansätze unterscheiden sich jedoch erheblich voneinander.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="e7cfe-120">Teilkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="e7cfe-120">Partial Configurations</span></span>

<span data-ttu-id="e7cfe-121">Wenn Sie Teilkonfigurationen verwenden, wird der lokale Konfigurations-Manager so konfiguriert, dass mehrere Konfigurationen unabhängig voneinander verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="e7cfe-122">Konfigurationen werden unabhängig voneinander kompiliert und anschließend dem Knoten zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="e7cfe-123">Dies macht erforderlich, dass der lokale Konfigurations-Manager im Vorhinein mit dem Namen der jeweiligen Konfiguration konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="e7cfe-125">Durch Teilkonfigurationen haben mindestens zwei Teams die vollständige Kontrolle über die Konfiguration eines Servers, häufig ist die Kommunikation oder die Zusammenarbeit dabei nicht von Nutzen.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="e7cfe-126">Kunden haben zurückgemeldet, dass dies zu Ressourcenkonflikten, unbeabsichtigten Außerkraftsetzungen und letztlich zu einem Verlust der Kontrolle über die Konfiguration des Objekts führen kann.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="e7cfe-127">Ferner haben Kunden geäußert, dass es unwahrscheinlich ist, dass bei Verwendung dieses Modells die Konfigurationsänderungen der einzelnen Steuerungsteams vollständig über eine Releasepipeline getestet werden können. Dies wiederum führe zu unerwarteten Ergebnissen in der Produktion.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="e7cfe-128">**Es ist wichtig, dass für die Auswertung sämtlicher auf dem Server freigegebenen Änderungen eine einzelne Pipeline verwendet wird.**</span><span class="sxs-lookup"><span data-stu-id="e7cfe-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="e7cfe-129">In der nachfolgenden Abbildung gibt Team B seine Teilkonfiguration für Team A frei. Anschließend führt Team A Tests auf dem Server aus, bei denen beide Konfigurationen angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="e7cfe-130">In diesem Modell verfügt nur eine Stelle über die Berechtigung zur Vornahme von Änderungen in der Produktion.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="e7cfe-132">Wenn Team B Änderungen vornehmen muss, sollte das Team einen Pull Request an die Umgebung für die Quellcodeverwaltung von Team A übermitteln.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="e7cfe-133">Anschließend überprüft Team A die Änderungen mithilfe der Testautomatisierung und gibt diese für die Produktion frei, wenn davon auszugehen ist, dass die Änderungen in den Anwendungen oder den vom Server gehosteten Diensten keine Fehler verursachen.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="e7cfe-134">Zusammengesetzte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="e7cfe-134">Composite Resources</span></span>

<span data-ttu-id="e7cfe-135">Eine zusammengesetzte Ressource ist eine DSC-Konfiguration, die als Ressource verpackt ist.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="e7cfe-136">Bei der Konfiguration des LCM (lokaler Konfigurations-Manager) zum Akzeptieren zusammengesetzter Ressourcen müssen keine besonderen Anforderungen berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="e7cfe-137">Die Ressourcen werden in einer neuen Konfiguration verwendet, und eine einzige Kompilierung ergibt eine MOF-Datei.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="e7cfe-139">Für zusammengesetzte Ressourcen gibt es zwei gängige Szenarios.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="e7cfe-140">Das erste Szenario beinhaltet die Verringerung der Komplexität und das Abstrahieren eindeutiger Konzepte.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="e7cfe-141">Im zweiten Szenario wird zugelassen, dass Baselines nach dem Bestehen sämtlicher Tests für ein Anwendungsteam verpackt werden, damit diese über die zugehörige Releasepipeline sicher für die Produktion bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="e7cfe-142">Zusammengesetzte Ressourcen stufen die Komposition und die Zusammenarbeit über eine Pipeline hoch, während Betriebsbereitschaft geschaffen wird</span><span class="sxs-lookup"><span data-stu-id="e7cfe-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="e7cfe-143">Möglicherweise verwenden Sie bereits zusammengesetzte Ressourcen, ohne es zu bemerken.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="e7cfe-144">Ein Beispiel hierfür ist **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="e7cfe-145">Diese Ressource verwaltet den Status mehrerer Windows-Dienste, ohne diese einzeln aufzuführen.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="e7cfe-146">Die Eigenschaft „Name“ akzeptiert ein Array von Zeichenfolgen für die Angabe der Namen der einzelnen Dienste.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="e7cfe-147">Wenn die Konfiguration kompiliert wird, enthält die MOF-Datei für jeden der an ServiceSet übergebenen Namen einen eindeutigen Abschnitt („Dienst“).</span><span class="sxs-lookup"><span data-stu-id="e7cfe-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="e7cfe-148">Organisationen verfügen möglicherweise über „Agents“ oder „Middleware“, die auf allen Servern installiert werden sollten.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="e7cfe-149">Eine zusammengesetzte Ressource ist die optimale Lösung für die Verwaltung von Abhängigkeiten sowie die Einrichtung und Konfiguration dieser Tools und Dienstprogramme.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="e7cfe-150">Die Person bzw. das Team, die/das für serverübergreifende Lösungen verantwortlich ist, erstellt eine Konfiguration mit den entsprechenden Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="e7cfe-151">In einem nächsten Schritt wird die Konfiguration mithilfe von Anweisungen aus der Dokumentation zu zusammengesetzten Ressourcen als zusammengesetzte Ressource verpackt.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="e7cfe-152">Abschließend wird die zusammengesetzte Ressource an einem bestimmten Speicherort veröffentlicht (z.B. in einer Dateifreigabe oder einem NuGet-Feed), an dem die Anwendungsteams die Ressource in ihren Konfigurationen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="e7cfe-153">Jedes Mal, wenn das Team eine neue Version freigibt, wird die Versionsnummer im Modulmanifest für die zugehörige zusammengesetzte Ressource schrittweise erhöht.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="e7cfe-154">Die Anwendungsteams schließen die zusammengesetzte Ressource in die Konfiguration ein, die sie für die Verwaltung von Anwendungsabhängigkeiten erstellen.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="e7cfe-155">Wenn die Betriebs-/Sicherheitsteams eine neue Version ihrer Ressource freigeben, benachrichtigen sie die Anwendungsteams über die neue Änderung.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="e7cfe-156">Die Anwendungsteams lösen möglicherweise eine Freigabe für die Produktion aus, die nur eine Änderung an den Baselines beinhaltet.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="e7cfe-157">Dies bietet jedoch eine Möglichkeit zum Auswerten der Auswirkungen auf Anwendungen vor dem Risiko eines Dienstausfalls.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="e7cfe-158">Hinweis: Das Feedback in Bezug auf die Verwendung zusammengesetzter Ressourcen beinhaltete die Kritik, dass zum Vornehmen von Änderungen eine neue MOF-Datei kompiliert und freigegeben werden muss.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="e7cfe-159">Dies ist entwurfsbedingt.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-159">This is by design.</span></span>
<span data-ttu-id="e7cfe-160">Jedes neue Konfigurationsrelease sollte einen statischen Verweis auf eine bestimmte Version der einzelnen Ressourcen enthalten. Zudem sollte es durch Tests validiert werden, bevor der Serverknoten für die Produktion erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="e7cfe-161">Der Prozess des Testens und Freigebens von Änderungen aus der Quellcodeverwaltung schafft eine sichere Umgebung für die Freigabe von Änderungen in kleinen, aber häufigen Batches.</span><span class="sxs-lookup"><span data-stu-id="e7cfe-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="e7cfe-162">Weitere Informationen zur Verwendung von Releasepipelines für die Verwaltung der Kerninfrastruktur finden Sie in folgendem Whitepaper: [Das Releasepipeline-Modell](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="e7cfe-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>