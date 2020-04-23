---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Arbeiten mit lokalen PSRepositorys
ms.openlocfilehash: c1bd905674ae76a3badd3eff50780f0e1bb5fc64
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75415817"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="ee0bd-103">Arbeiten mit privaten PowerShellGet-Repositorys</span><span class="sxs-lookup"><span data-stu-id="ee0bd-103">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="ee0bd-104">Das PowerShellGet-Modul unterstützt andere Repositorys als den PowerShell-Katalog.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="ee0bd-105">Diese Cmdlets ermöglichen die folgenden Szenarien:</span><span class="sxs-lookup"><span data-stu-id="ee0bd-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="ee0bd-106">Unterstützung eines vertrauenswürdigen, bereits überprüften Satzes von PowerShell-Modulen für die Verwendung in Ihrer Umgebung</span><span class="sxs-lookup"><span data-stu-id="ee0bd-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="ee0bd-107">Testen einer CI/CD-Pipeline, die PowerShell-Module oder -Skripts erstellt</span><span class="sxs-lookup"><span data-stu-id="ee0bd-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="ee0bd-108">Bereitstellen von PowerShell-Skripts und -Modulen auf Systemen, die nicht auf das Internet zugreifen können</span><span class="sxs-lookup"><span data-stu-id="ee0bd-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="ee0bd-109">Bereitstellen von PowerShell-Skripts und -Modulen nur für Ihre Organisation</span><span class="sxs-lookup"><span data-stu-id="ee0bd-109">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="ee0bd-110">Dieser Artikel beschreibt, wie Sie ein lokales PowerShell-Repository einrichten.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-110">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="ee0bd-111">Der Artikel behandelt auch das im PowerShell-Katalog verfügbare [OfflinePowerShellGetDeploy][]-Modul.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-111">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="ee0bd-112">Dieses Modul enthält Cmdlets zum Installieren der neuesten Version von PowerShellGet in Ihrem lokalen Repository.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-112">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="ee0bd-113">Lokale Repositorytypen</span><span class="sxs-lookup"><span data-stu-id="ee0bd-113">Local repository types</span></span>

<span data-ttu-id="ee0bd-114">Lokale PSRepositorys können auf zwei Arten erstellt werden: NuGet-Server oder Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-114">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="ee0bd-115">Jeder Typ hat Vor- und Nachteile:</span><span class="sxs-lookup"><span data-stu-id="ee0bd-115">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="ee0bd-116">NuGet-Server</span><span class="sxs-lookup"><span data-stu-id="ee0bd-116">NuGet Server</span></span>

| <span data-ttu-id="ee0bd-117">Vorteile</span><span class="sxs-lookup"><span data-stu-id="ee0bd-117">Advantages</span></span>| <span data-ttu-id="ee0bd-118">Nachteile</span><span class="sxs-lookup"><span data-stu-id="ee0bd-118">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="ee0bd-119">Eng imitierte PowerShell-Katalog-Funktionalität</span><span class="sxs-lookup"><span data-stu-id="ee0bd-119">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="ee0bd-120">App mit mehreren Ebenen erfordert Planung des Betriebs und Support</span><span class="sxs-lookup"><span data-stu-id="ee0bd-120">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="ee0bd-121">NuGet integriert in Visual Studio, andere Tools</span><span class="sxs-lookup"><span data-stu-id="ee0bd-121">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="ee0bd-122">Authentifizierungsmodell und NuGet-Kontenverwaltung erforderlich</span><span class="sxs-lookup"><span data-stu-id="ee0bd-122">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="ee0bd-123">NuGet unterstützt Metadaten in `.Nupkg`-Paketen</span><span class="sxs-lookup"><span data-stu-id="ee0bd-123">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="ee0bd-124">Veröffentlichung erfordert Verwaltung und Wartung des API-Schlüssels</span><span class="sxs-lookup"><span data-stu-id="ee0bd-124">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="ee0bd-125">Ermöglicht Suche, Paketverwaltung usw.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-125">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="ee0bd-126">Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="ee0bd-126">File Share</span></span>

| <span data-ttu-id="ee0bd-127">Vorteile</span><span class="sxs-lookup"><span data-stu-id="ee0bd-127">Advantages</span></span>| <span data-ttu-id="ee0bd-128">Nachteile</span><span class="sxs-lookup"><span data-stu-id="ee0bd-128">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="ee0bd-129">Kann einfach eingerichtet, gesichert und verwaltet werden</span><span class="sxs-lookup"><span data-stu-id="ee0bd-129">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="ee0bd-130">Von PowerShellGet verwendete Metadaten sind nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="ee0bd-130">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="ee0bd-131">Einfaches Sicherheitsmodell – Benutzerberechtigungen für Freigabe</span><span class="sxs-lookup"><span data-stu-id="ee0bd-131">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="ee0bd-132">Keine Benutzeroberfläche außer einfacher Dateifreigabe</span><span class="sxs-lookup"><span data-stu-id="ee0bd-132">No UI beyond basic file share</span></span> |
| <span data-ttu-id="ee0bd-133">Keine Einschränkungen, wie z.B. das Ersetzen vorhandener Elemente</span><span class="sxs-lookup"><span data-stu-id="ee0bd-133">No constraints such as replacing existing items</span></span> | <span data-ttu-id="ee0bd-134">Eingeschränkte Sicherheit und keine Aufzeichnung darüber, wer Updates ausführt</span><span class="sxs-lookup"><span data-stu-id="ee0bd-134">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="ee0bd-135">PowerShellGet funktioniert mit jedem Typ und unterstützt das Suchen von Versionen und die Installation von Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-135">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="ee0bd-136">Einige Funktionen, die mit dem PowerShell-Katalog funktionieren, sind jedoch nicht für Basis-NuGet-Server oder Dateifreigaben verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-136">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="ee0bd-137">Alles ist ein Paket – keine Differenzierung von Skripts, Modulen, DSC-Ressourcen oder Rollenfunktionen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-137">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="ee0bd-138">Dateifreigabeserver können Paketmetadaten einschließlich Tags nicht sehen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-138">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="ee0bd-139">Erstellen eines lokalen Repositorys</span><span class="sxs-lookup"><span data-stu-id="ee0bd-139">Creating a local repository</span></span>

<span data-ttu-id="ee0bd-140">Im folgenden Artikel sind die Schritte zum Einrichten Ihres eigenen NuGet-Servers aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-140">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="ee0bd-141">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="ee0bd-141">[NuGet.Server][]</span></span>

<span data-ttu-id="ee0bd-142">Führen Sie die Schritte bis zum Punkt des Hinzufügens von Paketen aus.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-142">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="ee0bd-143">Die Schritte zum [Veröffentlichen eines Pakets](#publishing-to-a-local-repository) werden weiter unten in diesem Artikel behandelt.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-143">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="ee0bd-144">Stellen Sie bei einem Repository auf Dateifreigabebasis sicher, dass Ihre Benutzer über Berechtigungen zum Zugriff auf die Dateifreigabe verfügen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-144">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="ee0bd-145">Registrieren eines lokalen Repositorys</span><span class="sxs-lookup"><span data-stu-id="ee0bd-145">Registering a local repository</span></span>

<span data-ttu-id="ee0bd-146">Bevor ein Repository verwendet werden kann, muss es mithilfe des `Register-PSRepository`-Befehls registriert werden.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-146">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="ee0bd-147">In den folgenden Beispielen ist die **InstallationPolicy** unter der Annahme, dass Sie Ihrem eigenen Repository vertrauen, auf *Trusted* festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-147">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="ee0bd-148">Beachten Sie, wie unterschiedlich die beiden Befehle **ScriptSourceLocation** behandeln.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-148">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="ee0bd-149">Für Repositorys auf Dateifreigabebasis müssen **SourceLocation** und **ScriptSourceLocation** übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-149">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="ee0bd-150">Für ein webbasiertes Repository müssen sie unterschiedlich sein, also wird **SourceLocation** in diesem Beispiel ein nachstehender „/“ angefügt.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-150">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="ee0bd-151">Wenn das neu erstellte PSRepository das Standardrepository sein soll, müssen Sie die Registrierung aller anderen PSRepositorys aufheben.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-151">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="ee0bd-152">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ee0bd-152">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="ee0bd-153">Das Repository mit dem Namen PSGallery ist für die Verwendung durch den PowerShell-Katalog reserviert.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-153">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="ee0bd-154">Sie können die Registrierung von PSGallery aufheben, aber den Namen PSGallery nicht für ein anderes Repository wiederverwenden.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-154">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="ee0bd-155">Wenn Sie PSGallery wiederherstellen müssen, führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ee0bd-155">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="ee0bd-156">Veröffentlichung in einem lokalen Repository</span><span class="sxs-lookup"><span data-stu-id="ee0bd-156">Publishing to a local repository</span></span>

<span data-ttu-id="ee0bd-157">Nachdem Sie das lokale PSRepository registriert haben, können Sie in Ihrem lokalen PSRepository veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-157">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="ee0bd-158">Es gibt zwei Hauptveröffentlichungsszenarien: Veröffentlichen Ihres eigenen Moduls und Veröffentlichen eines Moduls aus der PSGallery.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-158">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="ee0bd-159">Veröffentlichung eines von Ihnen erstellten Moduls</span><span class="sxs-lookup"><span data-stu-id="ee0bd-159">Publishing a module you authored</span></span>

<span data-ttu-id="ee0bd-160">Veröffentlichen Sie Ihr Modul mit `Publish-Module` und `Publish-Script` genauso wie für den PowerShell-Katalog in Ihrem lokalen PSRepository.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-160">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="ee0bd-161">Geben Sie den Speicherort für Ihren Code an</span><span class="sxs-lookup"><span data-stu-id="ee0bd-161">Specify the location for your code</span></span>
- <span data-ttu-id="ee0bd-162">Geben Sie einen API-Schlüssel an</span><span class="sxs-lookup"><span data-stu-id="ee0bd-162">Supply an API key</span></span>
- <span data-ttu-id="ee0bd-163">Geben Sie den Namen des Repositorys an.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-163">Specify the repository name.</span></span> <span data-ttu-id="ee0bd-164">Zum Beispiel, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="ee0bd-164">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="ee0bd-165">Sie müssen ein Konto auf dem NuGet-Server erstellen und sich dann anmelden, um den API-Schlüssel zu generieren und zu speichern.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-165">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="ee0bd-166">Verwenden Sie für eine Dateifreigabe eine beliebige nicht leere Zeichenfolge für den NuGetApiKey-Wert.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-166">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="ee0bd-167">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="ee0bd-167">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'
```

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="ee0bd-168">Um die Sicherheit zu gewährleisten, sollten API-Schlüssel nicht in Skripts hartcodiert sein.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-168">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="ee0bd-169">Verwenden Sie ein sicheres Schlüsselverwaltungssystem.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-169">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="ee0bd-170">Veröffentlichung eines Moduls aus der PSGallery</span><span class="sxs-lookup"><span data-stu-id="ee0bd-170">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="ee0bd-171">Um ein Modul aus der PSGallery in Ihrem lokalen PSRepository zu veröffentlichen, können Sie das Cmdlet „Save-Package“ verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-171">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="ee0bd-172">Geben Sie den Namen des Pakets an</span><span class="sxs-lookup"><span data-stu-id="ee0bd-172">Specify the Name of the Package</span></span>
- <span data-ttu-id="ee0bd-173">Geben Sie „NuGet“ als Anbieter an</span><span class="sxs-lookup"><span data-stu-id="ee0bd-173">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="ee0bd-174">Geben Sie den PSGallery-Speicherort als Quelle an (https://www.powershellgallery.com/api/v2) )</span><span class="sxs-lookup"><span data-stu-id="ee0bd-174">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="ee0bd-175">Geben Sie den Pfad zu Ihrem lokalen Repository an</span><span class="sxs-lookup"><span data-stu-id="ee0bd-175">Specify the path to your local Repository</span></span>

<span data-ttu-id="ee0bd-176">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ee0bd-176">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="ee0bd-177">Wenn Ihr lokales PSRepository webbasiert ist, erfordert es einen zusätzlichen Schritt, der „nuget.exe“ zum Veröffentlichen verwendet.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-177">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="ee0bd-178">Weitere Informationen finden Sie in der Dokumentation zur Verwendung von [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="ee0bd-178">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="ee0bd-179">Installieren von PowerShellGet auf einem nicht verbundenen System</span><span class="sxs-lookup"><span data-stu-id="ee0bd-179">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="ee0bd-180">Das Bereitstellen von PowerShellGet ist schwierig in Umgebungen, die erfordern, dass Systeme nicht mit dem Internet verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-180">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="ee0bd-181">Der Bootstrapprozess von PowerShellGet installiert bei der ersten Verwendung die aktuelle Version.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-181">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="ee0bd-182">Das OfflinePowerShellGetDeploy-Modul im PowerShell-Katalog bietet Cmdlets, die diesen Bootstrapprozess unterstützen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-182">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="ee0bd-183">Um eine Offlinebereitstellung zu starten, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="ee0bd-183">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="ee0bd-184">OfflinePowerShellGetDeploy herunterladen und auf Ihrem mit dem Internet verbundenen System und Ihren nicht verbundenen Systemen installieren</span><span class="sxs-lookup"><span data-stu-id="ee0bd-184">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="ee0bd-185">PowerShellGet und seine Abhängigkeiten mithilfe des `Save-PowerShellGetForOffline`-Cmdlets auf das mit dem Internet verbundene System herunterladen</span><span class="sxs-lookup"><span data-stu-id="ee0bd-185">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="ee0bd-186">PowerShellGet und seine Abhängigkeiten von dem mit dem Internet verbundenen System auf das nicht verbundene System kopieren</span><span class="sxs-lookup"><span data-stu-id="ee0bd-186">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="ee0bd-187">Durch Verwendung von `Install-PowerShellGetOffline` auf dem nicht verbundenen System PowerShellGet und seine Abhängigkeiten in den richtigen Ordnern ablegen</span><span class="sxs-lookup"><span data-stu-id="ee0bd-187">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="ee0bd-188">Die folgenden Befehle legen mit `Save-PowerShellGetForOffline` alle Komponenten im Ordner `f:\OfflinePowerShellGet` ab.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-188">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="ee0bd-189">An diesem Punkt müssen Sie den Inhalt von `F:\OfflinePowerShellGet` Ihren nicht verbundenen Systemen verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-189">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="ee0bd-190">Führen Sie das `Install-PowerShellGetOffline`-Cmdlet aus, um PowerShellGet auf dem nicht verbundenen System zu installieren.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-190">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="ee0bd-191">Es ist wichtig, dass Sie PowerShellGet nicht in der PowerShell-Sitzung ausführen, bevor Sie diese Befehle ausführen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-191">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="ee0bd-192">Sobald PowerShellGet in die Sitzung geladen ist, können die Komponenten nicht aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-192">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="ee0bd-193">Wenn Sie PowerShellGet versehentlich starten, beenden Sie PowerShell, und starten Sie es neu.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-193">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="ee0bd-194">Nach dem Ausführen dieser Befehle können Sie PowerShellGet in Ihrem lokalen Repository veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-194">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="ee0bd-195">Verwenden von Paketierungslösungen zum Hosten von PowerShellGet-Repositorys</span><span class="sxs-lookup"><span data-stu-id="ee0bd-195">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="ee0bd-196">Sie können auch Paketierungslösungen wie Azure Artifacts verwenden, um ein privates oder öffentliches PowerShellGet-Repository zu hosten.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-196">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="ee0bd-197">Weitere Informationen und Anweisungen finden Sie in der [Azure Artifacts-Dokumentation](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).</span><span class="sxs-lookup"><span data-stu-id="ee0bd-197">For more information and instructions, see the [Azure Artifacts documentation](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee0bd-198">Um die Sicherheit zu gewährleisten, sollten API-Schlüssel nicht in Skripts hartcodiert sein.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-198">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="ee0bd-199">Verwenden Sie ein sicheres Schlüsselverwaltungssystem.</span><span class="sxs-lookup"><span data-stu-id="ee0bd-199">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
