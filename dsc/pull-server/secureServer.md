---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Bewährte Methoden für Pullserver
ms.openlocfilehash: fe483a487f85f2e4edb0928fccfe98746ae11231
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58057704"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="caa74-103">Bewährte Methoden für Pullserver</span><span class="sxs-lookup"><span data-stu-id="caa74-103">Pull server best practices</span></span>

<span data-ttu-id="caa74-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="caa74-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="caa74-105">Der Pull-Server (Windows-Feature *DSC-Dienst*) ist eine von Windows Server unterstützte Komponente, jedoch sollen keine neuen Features oder Funktionen angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="caa74-106">Es wird empfohlen, verwaltete Clients auf [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) umzustellen (enthält Features zusätzlich zum Pull-Server unter Windows Server) oder auf eine der [hier](pullserver.md#community-solutions-for-pull-service) aufgeführten Communitylösungen.</span><span class="sxs-lookup"><span data-stu-id="caa74-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="caa74-107">Zusammenfassung: Dieser Artikel enthält Prozesse und Erweiterungen, die Techniker beim Vorbereiten von Lösungen helfen sollen.</span><span class="sxs-lookup"><span data-stu-id="caa74-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="caa74-108">Details sollten bewährte Methoden bereitstellen, die von Kunden ermittelt und dann vom Produktteam bestätigt wurden, um sicherzustellen, dass die Empfehlungen in die Zukunft gerichtet sind und als stabil angesehen werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="caa74-109">Dokumentinformation</span><span class="sxs-lookup"><span data-stu-id="caa74-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="caa74-110">Autor</span><span class="sxs-lookup"><span data-stu-id="caa74-110">Author</span></span> | <span data-ttu-id="caa74-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="caa74-111">Michael Greene</span></span>
<span data-ttu-id="caa74-112">Prüfer</span><span class="sxs-lookup"><span data-stu-id="caa74-112">Reviewers</span></span> | <span data-ttu-id="caa74-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="caa74-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="caa74-114">Veröffentlicht</span><span class="sxs-lookup"><span data-stu-id="caa74-114">Published</span></span> | <span data-ttu-id="caa74-115">April 2015</span><span class="sxs-lookup"><span data-stu-id="caa74-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="caa74-116">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="caa74-116">Abstract</span></span>

<span data-ttu-id="caa74-117">Dieses Dokument soll als offizieller Leitfaden für alle dienen, die die Implementierung eines Windows PowerShell DSC-Pullservers planen.</span><span class="sxs-lookup"><span data-stu-id="caa74-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="caa74-118">Ein Pullserver ist ein einfacher Dienst, der in wenigen Minuten bereitgestellt sein sollte.</span><span class="sxs-lookup"><span data-stu-id="caa74-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="caa74-119">Obwohl dieses Dokument technische Hilfe und Anleitungen zur Verfügung stellen soll, die in einer Bereitstellung genutzt werden können, stellt dieses eine Referenz für bewährte Methoden und die zu beachtenden Punkte vor der Bereitstellung dar.</span><span class="sxs-lookup"><span data-stu-id="caa74-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="caa74-120">Leser sollten über grundlegende DSC-Kenntnisse verfügen und die Bestimmungen kennen, mit denen die Komponenten beschrieben werden, die in einer DSC-Bereitstellung enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="caa74-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="caa74-121">Weitere Informationen finden Sie im Thema [Windows PowerShell DSC – Übersicht](/powershell/dsc/overview).</span><span class="sxs-lookup"><span data-stu-id="caa74-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview)  topic.</span></span>
<span data-ttu-id="caa74-122">Da sich DSC im gleichen Maße weiterentwickeln sollte, wie sich die Cloudinfrastruktur weiterentwickelt, wird die zugrunde liegende Technologie einschließlich des Pullservers sich ebenfalls weiterentwickeln und neue Funktionen einführen.</span><span class="sxs-lookup"><span data-stu-id="caa74-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="caa74-123">Dieses Dokument enthält eine Versionstabelle im Anhang, die Referenzen zu vorherigen Versionen und in die Zukunft gerichteten Lösungen bereitstellt, um in die Zukunft gerichtete Entwürfe zu fördern.</span><span class="sxs-lookup"><span data-stu-id="caa74-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="caa74-124">Die zwei Hauptabschnitte dieses Dokuments:</span><span class="sxs-lookup"><span data-stu-id="caa74-124">The two major sections of this document:</span></span>

- <span data-ttu-id="caa74-125">Konfigurationsplanung</span><span class="sxs-lookup"><span data-stu-id="caa74-125">Configuration Planning</span></span>
- <span data-ttu-id="caa74-126">Installationsanweisungen</span><span class="sxs-lookup"><span data-stu-id="caa74-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="caa74-127">Windows Management Framework-Versionen</span><span class="sxs-lookup"><span data-stu-id="caa74-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="caa74-128">Die Informationen in diesem Dokument sollen auf Windows Management Framework 5.0 angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="caa74-129">Obwohl WMF 5.0 nicht für die Bereitstellung und Ausführung eines Pullservers erforderlich ist, konzentriert sich dieses Dokument auf die Version 5.0.</span><span class="sxs-lookup"><span data-stu-id="caa74-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="caa74-130">Windows PowerShell zum Konfigurieren des gewünschten Zustands</span><span class="sxs-lookup"><span data-stu-id="caa74-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="caa74-131">Desired State Configuration (DSC) ist eine Managementplattform, die das Bereitstellen und Verwalten von Konfigurationsdaten mithilfe einer Branchensyntax namens „Managed Object Format“ (MOF) aktiviert, um „Common Information Models“ (CIM) zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="caa74-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="caa74-132">Das Open Source-Projekt „Open Management Infrastructure“ (OMI) ist vorhanden, um die Entwicklung dieser Standards plattformübergreifend zu unterstützen, einschließlich Linux und Betriebssysteme für die Netzwerkhardware.</span><span class="sxs-lookup"><span data-stu-id="caa74-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="caa74-133">Weitere Informationen finden Sie unter der [DMTF page linking to MOF specifications (DMTF-Seite mit Link zu den MOF-Spezifikationen)](https://www.dmtf.org/standards/cim) und [OMI Documents and Source (OMI-Dokumente und Quelle)](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="caa74-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="caa74-134">Windows PowerShell bietet eine Reihe an Spracherweiterungen für Desired State Configuration, die Sie zur Erstellung und Verwaltung deklarativer Konfigurationen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="caa74-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="caa74-135">Pullserverrolle</span><span class="sxs-lookup"><span data-stu-id="caa74-135">Pull server role</span></span>

<span data-ttu-id="caa74-136">Ein Pullserver bietet einen zentralisierten Dienst zum Speichern von Konfigurationen, die für Zielknoten zugänglich sein werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="caa74-137">Die Pullserverrolle kann als Webserverinstanz oder SMB-Dateifreigabe bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="caa74-138">Die Webserverfunktion enthält eine OData-Schnittstelle und kann optional Funktionen für die Zielknoten enthalten, die die Bestätigung des Erfolgs oder Misserfolgs der angewendeten Konfigurationen übermitteln.</span><span class="sxs-lookup"><span data-stu-id="caa74-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="caa74-139">Diese Funktion ist nützlich in Umgebungen, in denen eine große Anzahl von Knoten besteht.</span><span class="sxs-lookup"><span data-stu-id="caa74-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="caa74-140">Nach dem Konfigurieren eines Zielknotens (auch als Client bezeichnet), der auf den Pullserver verweist, werden die aktuellen Konfigurationsdaten und alle erforderlichen Skripts heruntergeladen und angewendet.</span><span class="sxs-lookup"><span data-stu-id="caa74-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="caa74-141">Dies kann eine einmalige Bereitstellung oder eine wiederkehrende Aufgabe sein und macht den Pullserver zu einer wichtigen Ressource zur Verwaltung von Skalierungsänderungen.</span><span class="sxs-lookup"><span data-stu-id="caa74-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="caa74-142">Weitere Informationen finden Sie unter [Desired State Configuration – Pulldienst](/powershell/dsc/pullServer) und</span><span class="sxs-lookup"><span data-stu-id="caa74-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/dsc/pullServer) and</span></span>

<span data-ttu-id="caa74-143">[Desired State Configuration – Pulldienst](/powershell/dsc/pullServer).</span><span class="sxs-lookup"><span data-stu-id="caa74-143">[Push and Pull Configuration Modes](/powershell/dsc/pullServer).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="caa74-144">Konfigurationsplanung</span><span class="sxs-lookup"><span data-stu-id="caa74-144">Configuration planning</span></span>

<span data-ttu-id="caa74-145">Für jede Bereitstellung einer Unternehmenssoftware können im Voraus Informationen gesammelt werden, um die Planung der korrekten Architektur zu unterstützen und um auf die erforderlichen Schritte zum Abschließen der Bereitstellung vorbereitet zu sein.</span><span class="sxs-lookup"><span data-stu-id="caa74-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="caa74-146">Die folgenden Abschnitte stellen Informationen zur Vorbereitung und Unternehmensverbindungen bereit, die wahrscheinlich im Voraus erfolgen müssen.</span><span class="sxs-lookup"><span data-stu-id="caa74-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="caa74-147">Softwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="caa74-147">Software requirements</span></span>

<span data-ttu-id="caa74-148">Das Bereitstellen eines Pullservers erfordert das DSC-Servicefeature von Windows Server.</span><span class="sxs-lookup"><span data-stu-id="caa74-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="caa74-149">Dieses Feature wurde in Windows Server 2012 eingeführt und durch fortlaufende Versionen von Windows Management Framework (WMF) aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="caa74-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="caa74-150">Softwaredownloads</span><span class="sxs-lookup"><span data-stu-id="caa74-150">Software downloads</span></span>

<span data-ttu-id="caa74-151">Neben der Installation der neuesten Inhalte von Windows Update werden zwei Downloads als bewährte Methoden für die Bereitstellung eines DSC-Pullservers empfohlen: Die neueste Version von Windows Management Framework und ein DSC-Modul zum Automatisieren der Bereitstellung von Pullservern.</span><span class="sxs-lookup"><span data-stu-id="caa74-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="caa74-152">WMF</span><span class="sxs-lookup"><span data-stu-id="caa74-152">WMF</span></span>

<span data-ttu-id="caa74-153">Windows Server 2012 R2 umfasst ein Feature namens DSC-Dienst.</span><span class="sxs-lookup"><span data-stu-id="caa74-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="caa74-154">Das DSC-Dienstfeature bietet die Pullserverfunktionalität, einschließlich der Binärdateien, die den OData-Endpunkt unterstützen.</span><span class="sxs-lookup"><span data-stu-id="caa74-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="caa74-155">WMF ist in Windows Server enthalten und wird in einem agilen Rhythmus zwischen den Windows Server-Versionen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="caa74-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="caa74-156">[Neue WMF 5.0-Versionen](https://www.microsoft.com/en-us/download/details.aspx?id=54616) können Updates des DSC-Dienstfeatures enthalten.</span><span class="sxs-lookup"><span data-stu-id="caa74-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="caa74-157">Aus diesem Grund ist es eine bewährte Methode, die neueste WMF-Version herunterzuladen und die Versionshinweise zu überprüfen, um festzustellen, ob die Version ein Update für das DSC-Dienstfeature enthält.</span><span class="sxs-lookup"><span data-stu-id="caa74-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="caa74-158">Sie sollten auch den Abschnitt über die Versionshinweise überprüfen, die angeben, ob der Status des Entwurfs für ein Update oder Szenario als stabil oder experimentell aufgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="caa74-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="caa74-159">Damit ein agiler Veröffentlichungszyklus möglich ist, können einzelne Features als stabil erklärt werden. Dies gibt an, dass das Feature zur Nutzung in einer Produktionsumgebung bereit ist, auch wenn WMF als Vorschau zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="caa74-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="caa74-160">Andere Features, die in der Vergangenheit durch WMF-Versionen aktualisiert wurden (weitere Informationen in den WMF-Versionshinweisen):</span><span class="sxs-lookup"><span data-stu-id="caa74-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="caa74-161">Windows PowerShell Windows PowerShell Integrated Scripting</span><span class="sxs-lookup"><span data-stu-id="caa74-161">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="caa74-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span><span class="sxs-lookup"><span data-stu-id="caa74-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="caa74-163">IIS-Erweiterung)  Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="caa74-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="caa74-164">Windows-Remoteverwaltung (WinRM) Windows-Verwaltungsinstrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="caa74-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="caa74-165">DSC-Ressource</span><span class="sxs-lookup"><span data-stu-id="caa74-165">DSC resource</span></span>

<span data-ttu-id="caa74-166">Eine Pullserverbereitstellung kann durch die Bereitstellung des Dienstes mithilfe eines DSC-Konfigurationsskripts vereinfacht werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="caa74-167">Dieses Dokument enthält Konfigurationsskripts, die verwendet werden können, um einen Serverknoten bereitzustellen, der für die Produktion geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="caa74-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="caa74-168">Für die Verwendung der Konfigurationsskripts ist ein DSC-Modul erforderlich, das nicht in Windows Server enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="caa74-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="caa74-169">Der erforderliche Modulname lautet **xPSDesiredStateConfiguration** und enthält die DSC-Ressource **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="caa74-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="caa74-170">Das Modul xPSDesiredStateConfiguration kann [hier](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="caa74-171">Verwenden Sie das Cmdlet `Install-Module` aus dem Modul **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="caa74-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="caa74-172">Das Modul **PowerShellGet** wird das Modul hier speichern:</span><span class="sxs-lookup"><span data-stu-id="caa74-172">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="caa74-173">Planungsaufgabe</span><span class="sxs-lookup"><span data-stu-id="caa74-173">Planning task</span></span>|
---|
<span data-ttu-id="caa74-174">Haben Sie Zugriff auf die Installationsdateien für Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="caa74-174">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="caa74-175">Wird die Bereitstellungsumgebung Internetzugang haben, damit WMF und das Modul aus dem Onlinekatalog heruntergeladen werden können?</span><span class="sxs-lookup"><span data-stu-id="caa74-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="caa74-176">Wie werden Sie nach der Installation des Betriebssystems die neuesten Sicherheitsupdates installieren?</span><span class="sxs-lookup"><span data-stu-id="caa74-176">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="caa74-177">Wird die Umgebung Internetzugang haben, um Updates zu erhalten oder wird sie über einen lokalen Windows Server Update Services-Server (WSUS) verfügen?</span><span class="sxs-lookup"><span data-stu-id="caa74-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="caa74-178">Haben Sie Zugang zu den Installationsdateien von Windows Server, die durch eine Einführung offline bereits Updates enthalten?</span><span class="sxs-lookup"><span data-stu-id="caa74-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="caa74-179">Hardwareanforderungen</span><span class="sxs-lookup"><span data-stu-id="caa74-179">Hardware requirements</span></span>

<span data-ttu-id="caa74-180">Pullserverbereitstellungen werden auf physischen und virtuellen Servern unterstützt.</span><span class="sxs-lookup"><span data-stu-id="caa74-180">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="caa74-181">Die Größenanforderungen für Pullserver decken sich mit den Anforderungen für Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="caa74-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="caa74-182">CPU: 1,4-GHz-64-Bit-Prozessor, Arbeitsspeicher: 512 MB, Festplattenspeicher: 32 GB, Netzwerk: Gigabit-Ethernet-Adapter.</span><span class="sxs-lookup"><span data-stu-id="caa74-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="caa74-183">Planungsaufgabe</span><span class="sxs-lookup"><span data-stu-id="caa74-183">Planning task</span></span>|
---|
<span data-ttu-id="caa74-184">Werden Sie auf einer physischen Hardware oder einer Virtualisierungsplattform bereitstellen?</span><span class="sxs-lookup"><span data-stu-id="caa74-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="caa74-185">Wie sieht der Prozess zum Anfordern eines neuen Servers für Ihre Zielumgebung aus?</span><span class="sxs-lookup"><span data-stu-id="caa74-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="caa74-186">Was ist die durchschnittliche Verarbeitungszeit, bis ein Server verfügbar wird?</span><span class="sxs-lookup"><span data-stu-id="caa74-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="caa74-187">Welche Servergröße werden Sie anfordern?</span><span class="sxs-lookup"><span data-stu-id="caa74-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="caa74-188">Konten</span><span class="sxs-lookup"><span data-stu-id="caa74-188">Accounts</span></span>

<span data-ttu-id="caa74-189">Es gibt keine Anforderungen an das Dienstkonto zur Bereitstellung einer Pullserverinstanz.</span><span class="sxs-lookup"><span data-stu-id="caa74-189">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="caa74-190">Es gibt jedoch Szenarios, in denen die Website im Kontext des lokalen Benutzerkontos ausgeführt werden könnte.</span><span class="sxs-lookup"><span data-stu-id="caa74-190">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="caa74-191">Zum Beispiel, wenn Zugang zur Speicherfreigabe für Websiteinhalte benötigt wird und der Windows Server oder das Gerät, das die Datenfreigabe hostet, nicht in eine Domäne eingebunden sind.</span><span class="sxs-lookup"><span data-stu-id="caa74-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="caa74-192">DNS-Datensätze</span><span class="sxs-lookup"><span data-stu-id="caa74-192">DNS records</span></span>

<span data-ttu-id="caa74-193">Sie benötigen einen Servernamen für die Konfiguration von Clients, damit diese mit einer Pullserverumgebung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="caa74-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="caa74-194">In Testumgebungen wird in der Regel der Serverhostname verwendet oder die IP-Adresse für den Server, wenn die DNS-Namensauflösung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="caa74-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="caa74-195">In Produktionsumgebungen oder in einer Laborumgebung, die eine Produktionsbereitstellung darstellen soll, wird empfohlen, einen DNS CNAME-Datensatz zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="caa74-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="caa74-196">Mit einem DNS-CNAME können Sie ein Alias erstellen, um auf Ihren Hosteintrag (A) zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="caa74-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="caa74-197">Die Absicht des zusätzlichen Namenseintrags ist eine verbesserte Flexibilität für den Fall, dass eine Änderung in der Zukunft erforderlich sein sollte.</span><span class="sxs-lookup"><span data-stu-id="caa74-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="caa74-198">Ein CNAME kann bei der Isolierung der Clientkonfiguration behilflich sein, damit Änderungen der Serverumgebung keine entsprechenden Änderungen der Clientkonfiguration erfordern. Diese Änderungen umfassen das Ersetzen eines Pullservers oder Hinzufügen zusätzlicher Pullserver.</span><span class="sxs-lookup"><span data-stu-id="caa74-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="caa74-199">Bedenken Sie die Lösungsarchitektur, wenn Sie einen Namen für den DNS-Datensatz auswählen.</span><span class="sxs-lookup"><span data-stu-id="caa74-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="caa74-200">Bei der Nutzung des Lastenausgleichs muss das Zertifikat zur Sicherung von Datenverkehr über HTTPS über denselben Namen verfügen wie der DNS-Datensatz.</span><span class="sxs-lookup"><span data-stu-id="caa74-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="caa74-201">Szenario</span><span class="sxs-lookup"><span data-stu-id="caa74-201">Scenario</span></span> |<span data-ttu-id="caa74-202">Bewährte Methode</span><span class="sxs-lookup"><span data-stu-id="caa74-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="caa74-203">Testumgebung</span><span class="sxs-lookup"><span data-stu-id="caa74-203">Test Environment</span></span> |<span data-ttu-id="caa74-204">Reproduzieren Sie nach Möglichkeit die geplante Produktionsumgebung.</span><span class="sxs-lookup"><span data-stu-id="caa74-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="caa74-205">Ein Serverhostname eignet sich für einfache Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="caa74-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="caa74-206">Wenn DNS nicht verfügbar ist, kann eine IP-Adresse anstatt eines Hostnamen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="caa74-207">Einzelknotenbereitstellung</span><span class="sxs-lookup"><span data-stu-id="caa74-207">Single Node Deployment</span></span> |<span data-ttu-id="caa74-208">Erstellen Sie einen DNS CNAME-Datensatz, der auf den Serverhostnamen verweist.</span><span class="sxs-lookup"><span data-stu-id="caa74-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="caa74-209">Weitere Informationen finden Sie unter [Configuring DNS Round Robin in Windows Server (Konfigurieren des DNS-Roundrobin in Windows Server)](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="caa74-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="caa74-210">Planungsaufgabe</span><span class="sxs-lookup"><span data-stu-id="caa74-210">Planning task</span></span>|
---|
<span data-ttu-id="caa74-211">Wissen Sie, an wen Sie sich zur Erstellung und Änderung der DNS-Datensätze wenden müssen?</span><span class="sxs-lookup"><span data-stu-id="caa74-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="caa74-212">Was ist die durchschnittliche Verarbeitungszeit für eine Anforderung eines DNS-Datensatzes?</span><span class="sxs-lookup"><span data-stu-id="caa74-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="caa74-213">Müssen Sie statische Hostnamendatensätze (A) für Server anfordern?</span><span class="sxs-lookup"><span data-stu-id="caa74-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="caa74-214">Was werden Sie als CNAME anfordern?</span><span class="sxs-lookup"><span data-stu-id="caa74-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="caa74-215">Wenn nötig, welche Art von Lastenausgleichslösung werden Sie verwenden?</span><span class="sxs-lookup"><span data-stu-id="caa74-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="caa74-216">(siehe Abschnitt „Lastenausgleich“ für weitere Informationen)</span><span class="sxs-lookup"><span data-stu-id="caa74-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="caa74-217">Public Key-Infrastruktur</span><span class="sxs-lookup"><span data-stu-id="caa74-217">Public Key Infrastructure</span></span>

<span data-ttu-id="caa74-218">In den meisten Unternehmen muss Netzwerkdatenverkehr, insbesondere Datenverkehr, der vertrauliche Daten wie die Serverkonfiguration enthält, heutzutage bei der Übertragung bestätigt und/oder verschlüsselt werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="caa74-219">Es ist zwar möglich, einen Pullserver mithilfe von HTTP bereitzustellen, was Clientanforderungen im Klartext vereinfacht, aber die bewährte Methode ist ein mit HTTPS gesicherter Datenverkehr.</span><span class="sxs-lookup"><span data-stu-id="caa74-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="caa74-220">Der Dienst kann mithilfe einer Reihe von Parametern in der DSC-Ressource **xPSDesiredStateConfiguration** zur Verwendung von HTTPS konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="caa74-221">Die Zertifikatanforderungen zur Sicherung von HTTPS-Datenverkehr für Pullserver unterscheiden sich nicht von der Sicherung anderer HTTPS-Websites.</span><span class="sxs-lookup"><span data-stu-id="caa74-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="caa74-222">Die **Webserver**-Vorlage in einem Windows Server Certificate Service erfüllt die erforderlichen Funktionen.</span><span class="sxs-lookup"><span data-stu-id="caa74-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="caa74-223">Planungsaufgabe</span><span class="sxs-lookup"><span data-stu-id="caa74-223">Planning task</span></span>|
---|
<span data-ttu-id="caa74-224">Wenn Zertifikatanforderungen nicht automatisiert sind, wen müssen Sie kontaktieren, um ein Zertifikat anzufordern?</span><span class="sxs-lookup"><span data-stu-id="caa74-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="caa74-225">Was ist die durchschnittliche Verarbeitungszeit für die Anforderung?</span><span class="sxs-lookup"><span data-stu-id="caa74-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="caa74-226">Wie wird Ihnen diese Zertifikatdatei übertragen?</span><span class="sxs-lookup"><span data-stu-id="caa74-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="caa74-227">Wie wird Ihnen der private Schlüssel des Zertifikats übertragen?</span><span class="sxs-lookup"><span data-stu-id="caa74-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="caa74-228">Wie lange dauert die Standardablaufzeit?</span><span class="sxs-lookup"><span data-stu-id="caa74-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="caa74-229">Haben Sie einen DNS-Namen für die Pullserverumgebung ausgewählt, die Sie für den Zertifikatnamen verwenden können?</span><span class="sxs-lookup"><span data-stu-id="caa74-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="caa74-230">Auswählen einer Architektur</span><span class="sxs-lookup"><span data-stu-id="caa74-230">Choosing an architecture</span></span>

<span data-ttu-id="caa74-231">Ein Pullserver kann mithilfe eines auf IIS gehosteten Webdiensts oder einer SMB-Datenfreigabe bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="caa74-232">In den meisten Fällen bietet die Webdienstoption mehr Flexibilität.</span><span class="sxs-lookup"><span data-stu-id="caa74-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="caa74-233">Es ist nicht ungewöhnlich, dass HTTPS-Datenverkehr die Netzwerkgrenzen durchläuft. Im Gegensatz dazu wird SMB-Datenverkehr häufig zwischen Netzwerken gefiltert oder blockiert.</span><span class="sxs-lookup"><span data-stu-id="caa74-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="caa74-234">Der Webdienst bietet außerdem die Option zum Einschließen eines Conformance Server oder Web Reporting Manager (beide Themen werden in einer künftigen Version dieses Dokuments behandelt), die einen Mechanismus für Clients bereitstellen, mit dem der Status an einen Server weitergeleitet werden kann, um somit für zentrale Sichtbarkeit zu sorgen.</span><span class="sxs-lookup"><span data-stu-id="caa74-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="caa74-235">SMB bietet eine Option für Umgebungen, bei der eine Richtlinie bestimmt, dass ein Webserver nicht verwendet werden sollte und für andere Umgebungsanforderungen, die eine Webserverrolle unerwünscht erscheinen lassen.</span><span class="sxs-lookup"><span data-stu-id="caa74-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="caa74-236">Sie müssen in beiden Fällen die Anforderungen für die Signierung und Verschlüsselung des Datenverkehrs bewerten.</span><span class="sxs-lookup"><span data-stu-id="caa74-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="caa74-237">HTTPS, SMB-Signaturen und IPSEC-Richtlinien sind Optionen, die in Betracht gezogen werden sollten.</span><span class="sxs-lookup"><span data-stu-id="caa74-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="caa74-238">Lastenausgleich</span><span class="sxs-lookup"><span data-stu-id="caa74-238">Load balancing</span></span>

<span data-ttu-id="caa74-239">Clients, die mit dem Webdienst interagieren, fordern Informationen an, die in einer einzelnen Antwort zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="caa74-240">Es sind keine sequenziellen Anforderungen erforderlich. Deshalb muss die Lastenausgleichsplattform nicht sicherstellen, dass Sitzungen zu jedem Zeitpunkt auf einem einzelnen Server beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="caa74-241">Planungsaufgabe</span><span class="sxs-lookup"><span data-stu-id="caa74-241">Planning task</span></span>|
---|
<span data-ttu-id="caa74-242">Welche Lösung wird für den serverübergreifenden Lastenausgleich für Datenverkehr verwendet werden?</span><span class="sxs-lookup"><span data-stu-id="caa74-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="caa74-243">Wenn Sie einen Hardwarelastenausgleich verwenden, wer wird eine Anforderung annehmen, um eine neue Konfiguration zum Gerät hinzuzufügen?</span><span class="sxs-lookup"><span data-stu-id="caa74-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="caa74-244">Was ist die durchschnittliche Verarbeitungszeit für eine Anforderung zur Konfiguration eines neuen, per Lastenausgleich verarbeiteten, Webdiensts?</span><span class="sxs-lookup"><span data-stu-id="caa74-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="caa74-245">Welche Information ist für die Anforderung erforderlich?</span><span class="sxs-lookup"><span data-stu-id="caa74-245">What information will be required for the request?</span></span>|
<span data-ttu-id="caa74-246">Müssen Sie eine zusätzliche IP-Adresse anfordern oder wird das für den Lastenausgleich verantwortliche Team sich darum kümmern?</span><span class="sxs-lookup"><span data-stu-id="caa74-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="caa74-247">Verfügen Sie über die benötigten DNS-Datensätze, und werden diese vom Team benötigt, das für die Konfiguration der Lastenausgleichslösung verantwortlich ist?</span><span class="sxs-lookup"><span data-stu-id="caa74-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="caa74-248">Erfordert die Lastenausgleichslösung, dass PKI vom Gerät verarbeitet wird, oder kann es den HTTPS-Datenverkehr per Lastenausgleich verarbeiten, so lange keine Sitzungserforderungen bestehen?</span><span class="sxs-lookup"><span data-stu-id="caa74-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="caa74-249">Bereitstellen von Konfigurationen und Modulen auf dem Pullserver</span><span class="sxs-lookup"><span data-stu-id="caa74-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="caa74-250">Als Teil der Konfigurationsplanung müssen Sie darüber nachdenken, welche DSC-Module und Konfigurationen von Pullservern gehostet werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="caa74-251">Für die Konfigurationsplanung ist es wichtig, grundlegende Kenntnisse zum Vorbereiten und Bereitstellen von Inhalten auf einem Pullserver zu haben.</span><span class="sxs-lookup"><span data-stu-id="caa74-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="caa74-252">Dieser Abschnitt wird in Zukunft erweitert und in einem Betriebshandbuch für DSC-Pullserver enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="caa74-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="caa74-253">Im Handbuch wird das tägliche Verfahren zum Verwalten von Modulen und Konfigurationen im Laufe der Zeit mithilfe der Automatisierung erläutert.</span><span class="sxs-lookup"><span data-stu-id="caa74-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="caa74-254">DSC-Module</span><span class="sxs-lookup"><span data-stu-id="caa74-254">DSC modules</span></span>

<span data-ttu-id="caa74-255">Clients, die eine Konfiguration anfordern, benötigen die erforderlichen DSC-Module.</span><span class="sxs-lookup"><span data-stu-id="caa74-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="caa74-256">Die automatische Verteilung von DSC-Modulen an Clients bei Bedarf ist eine Funktion des Pullservers.</span><span class="sxs-lookup"><span data-stu-id="caa74-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="caa74-257">Wenn Sie einen Pullserver zum ersten Mal vielleicht als Labor oder Machbarkeitsstudie bereitstellen, werden Sie wahrscheinlich von DSC-Modulen abhängig sein, die auf öffentlichen Repositorys verfügbar sind, wie z.B. dem PowerShell-Katalog oder den PowerShell.org GitHub-Repositorys für DSC-Module.</span><span class="sxs-lookup"><span data-stu-id="caa74-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="caa74-258">Beachten Sie, dass auch bei vertrauenswürdigen Onlinequellen wie dem PowerShell-Katalog jedes Modul, das aus einem öffentlichen Repository heruntergeladen wird, vor seiner Verwendung in der Produktion von jemandem kontrolliert werden sollte, der Erfahrung mit PowerShell hat und über Kenntnisse der Umgebung verfügt, in der die Module verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="caa74-259">Das Ausführen dieser Aufgabe ist ein guter Zeitpunkt, das Modul auf eine beliebige zusätzliche Nutzlast zu überprüfen, die entfernt werden kann, wie z.B. Dokumentation und Beispielskripts.</span><span class="sxs-lookup"><span data-stu-id="caa74-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="caa74-260">Dies verringert die Netzwerkbandbreite pro Client bei ihrer ersten Anforderung, wenn Module über das Netzwerk vom Server zum Client heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="caa74-261">Jedes Modul muss in einem bestimmten Format, einer ZIP-Datei mit dem Namen ModuleName_Version.zip, verpackt sein, die die Modulnutzlast enthält.</span><span class="sxs-lookup"><span data-stu-id="caa74-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="caa74-262">Nachdem die Datei auf den Server kopiert wurde, muss eine Prüfsummendatei erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="caa74-263">Wenn Clients eine Verbindung mit dem Server herstellen, wird die Prüfsumme verwendet, um zu überprüfen, ob der Inhalt des DSC-Moduls seit der Veröffentlichung nicht geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="caa74-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="caa74-264">Planungsaufgabe</span><span class="sxs-lookup"><span data-stu-id="caa74-264">Planning task</span></span>|
---|
<span data-ttu-id="caa74-265">Welche Szenarios sind wichtig zur Überprüfung, wenn Sie eine Test- oder Laborumgebung planen?</span><span class="sxs-lookup"><span data-stu-id="caa74-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="caa74-266">Gibt es öffentlich verfügbare Module, die Ressourcen enthalten, die alles abdecken, das Sie benötigen, oder müssen Sie Ihre eigenen Ressourcen erstellen?</span><span class="sxs-lookup"><span data-stu-id="caa74-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="caa74-267">Wird Ihre Umgebung Internetzugang haben, um öffentliche Module abrufen zu können?</span><span class="sxs-lookup"><span data-stu-id="caa74-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="caa74-268">Wer wird für die Prüfung von DSC-Modulen zuständig sein?</span><span class="sxs-lookup"><span data-stu-id="caa74-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="caa74-269">Was verwenden Sie als lokales Repository zum Speichern von DSC-Modulen, wenn Sie eine Produktionsumgebung planen?</span><span class="sxs-lookup"><span data-stu-id="caa74-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="caa74-270">Wird ein zentrales Team DSC-Module von Anwendungsteams akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="caa74-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="caa74-271">Wie wird das Verfahren aussehen?</span><span class="sxs-lookup"><span data-stu-id="caa74-271">What will the process be?</span></span>|
<span data-ttu-id="caa74-272">Werden Sie das Verpacken, Kopieren und Erstellen einer Prüfsumme für produktionsbereite DSC-Module für den Server aus Ihrem Quell-Repository automatisieren?</span><span class="sxs-lookup"><span data-stu-id="caa74-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="caa74-273">Wird Ihr Team auch für das Verwalten der Automatisierungsplattform verantwortlich sein?</span><span class="sxs-lookup"><span data-stu-id="caa74-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="caa74-274">DSC-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="caa74-274">DSC configurations</span></span>

<span data-ttu-id="caa74-275">Ein Pullserver dient zur Bereitstellung eines zentralisierten Mechanismus für die Verteilung von DSC-Konfigurationen auf Clientknoten.</span><span class="sxs-lookup"><span data-stu-id="caa74-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="caa74-276">Die Konfigurationen werden als MOF-Dokumente auf dem Server gespeichert.</span><span class="sxs-lookup"><span data-stu-id="caa74-276">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="caa74-277">Jedes Dokument wird mit einer eindeutigen **GUID** benannt.</span><span class="sxs-lookup"><span data-stu-id="caa74-277">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="caa74-278">Wenn Clients für die Verbindung mit einem Pullserver konfiguriert sind, wird ihnen auch die **GUID** für die Konfiguration zugewiesen, die sie anfordern sollten.</span><span class="sxs-lookup"><span data-stu-id="caa74-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="caa74-279">Dieses System des Verweisens auf Konfigurationen mit **GUID** garantiert globale Eindeutigkeit und ist flexibel, sodass eine Konfiguration mit Genauigkeit pro Knoten angewendet werden kann oder als eine Rollenkonfiguration, die viele Server umfasst, die identische Konfigurationen aufweisen sollten.</span><span class="sxs-lookup"><span data-stu-id="caa74-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="caa74-280">GUIDs</span><span class="sxs-lookup"><span data-stu-id="caa74-280">Guids</span></span>

<span data-ttu-id="caa74-281">Das Planen der Konfigurations-**GUIDs** lohnt sich besonders, wenn Sie eine Pullserverbereitstellung planen.</span><span class="sxs-lookup"><span data-stu-id="caa74-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="caa74-282">Es bestehen keine besonderen Anforderungen für die Behandlung von **GUIDs**, und der Prozess wird wahrscheinlich für jede Umgebung einzigartig sein.</span><span class="sxs-lookup"><span data-stu-id="caa74-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="caa74-283">Der Prozess kann einfach bis komplex sein: eine zentral gespeicherte CSV-Datei, eine einfache SQL-Tabelle, eine CMDB oder eine komplexe Lösung, die eine Integration mit einem anderen Tool oder einer Softwarelösung erfordert.</span><span class="sxs-lookup"><span data-stu-id="caa74-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="caa74-284">Es gibt zwei allgemeine Vorgehensweisen:</span><span class="sxs-lookup"><span data-stu-id="caa74-284">There are two general approaches:</span></span>

- <span data-ttu-id="caa74-285">**Zuweisen von GUIDs pro Server** – Hiermit kann sichergestellt werden, dass jede Serverkonfiguration einzeln gesteuert wird.</span><span class="sxs-lookup"><span data-stu-id="caa74-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="caa74-286">Dies bietet einen Grad an Genauigkeit um Updates und kann auch in Umgebungen mit wenigen Servern ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="caa74-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="caa74-287">**Zuweisen von GUIDs pro Serverrolle** – Alle Server, die die gleiche Funktion erfüllen, z.B. Webserver, verwenden dieselbe GUID, um auf die erforderlichen Konfigurationsdaten zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="caa74-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="caa74-288">Beachten Sie, dass wenn viele Server dieselbe GUID verwenden, alle gleichzeitig aktualisiert werden würden, wenn die Konfiguration geändert wird.</span><span class="sxs-lookup"><span data-stu-id="caa74-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="caa74-289">Die GUID sollte als vertraulich behandelt werden, da sie von jemanden mit böswilligen Absichten genutzt werden könnte, um Informationen über die Bereitstellung und Konfiguration von Servern in Ihrer Umgebung zu erlangen.</span><span class="sxs-lookup"><span data-stu-id="caa74-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="caa74-290">Weitere Informationen finden Sie unter [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/) (Sicheres Zuweisen von GUIDs in PowerShell Desired State Configuration Pullmodus).</span><span class="sxs-lookup"><span data-stu-id="caa74-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="caa74-291">Planungsaufgabe</span><span class="sxs-lookup"><span data-stu-id="caa74-291">Planning task</span></span>|
---|
<span data-ttu-id="caa74-292">Wer wird für das Kopieren der Konfigurationen in den Pullserverordner verantwortlich sein, sobald sie bereit sind?</span><span class="sxs-lookup"><span data-stu-id="caa74-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="caa74-293">Wie wird der Weiterleitungsprozess aussehen, wenn Konfigurationen von einem Anwendungsteam erstellt werden?</span><span class="sxs-lookup"><span data-stu-id="caa74-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="caa74-294">Werden Sie ein Repository zum Speichern von Konfigurationen nutzen, wenn sie über Teams hinweg verfasst werden?</span><span class="sxs-lookup"><span data-stu-id="caa74-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="caa74-295">Werden Sie das Kopieren von Konfigurationen auf den Server und das Erstellen einer Prüfsumme automatisieren, wenn sie bereit sind?</span><span class="sxs-lookup"><span data-stu-id="caa74-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="caa74-296">Wie werden Sie GUIDS den Servern oder Rollen zuordnen, und wo werden diese gespeichert?</span><span class="sxs-lookup"><span data-stu-id="caa74-296">How will you map Guids to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="caa74-297">Welchen Prozess werden Sie zum Konfigurieren der Clientcomputer verwenden, und wie wird er sich in Ihren Prozess zum Erstellen und Speichern von Konfigurations-GUIDs integrieren?</span><span class="sxs-lookup"><span data-stu-id="caa74-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="caa74-298">Installationsanweisungen</span><span class="sxs-lookup"><span data-stu-id="caa74-298">Installation Guide</span></span>

<span data-ttu-id="caa74-299">*Die in diesem Dokument angegebenen Skripts sind stabile Beispiele. Überprüfen Sie Skripts immer sorgfältig, bevor diese in einer Produktionsumgebung ausgeführt werden.*</span><span class="sxs-lookup"><span data-stu-id="caa74-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="caa74-300">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="caa74-300">Prerequisites</span></span>

<span data-ttu-id="caa74-301">Verwenden Sie den folgenden Befehl, um die PowerShell-Version auf Ihrem Server zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="caa74-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="caa74-302">Installieren Sie nach Möglichkeit die neueste Version von Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="caa74-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="caa74-303">Laden Sie als nächstes das `xPsDesiredStateConfiguration`-Modul mit dem folgenden Befehl herunter.</span><span class="sxs-lookup"><span data-stu-id="caa74-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="caa74-304">Der Befehl wird Sie nach Ihrer Genehmigung fragen, bevor Sie das Modul herunterladen.</span><span class="sxs-lookup"><span data-stu-id="caa74-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="caa74-305">Installations- und Konfigurationsskripts</span><span class="sxs-lookup"><span data-stu-id="caa74-305">Installation and configuration scripts</span></span>

<span data-ttu-id="caa74-306">Die beste Methode zur Bereitstellung eines DSC-Pullservers ist die Verwendung eines DSC-Konfigurationsskripts.</span><span class="sxs-lookup"><span data-stu-id="caa74-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="caa74-307">Dieses Dokument präsentiert Skripts, einschließlich beide grundlegenden Einstellungen, die nur den DSC-Webdienst konfigurieren und erweiterte Einstellungen, die einen durchgängigen Windows Server, einschließlich DSC-Webdienst konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="caa74-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="caa74-308">Hinweis:  Das `xPSDesiredStateConfiguration`-DSC-Modul erfordert derzeit das Gebietsschema EN-US für den Server.</span><span class="sxs-lookup"><span data-stu-id="caa74-308">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="caa74-309">Grundlegende Konfiguration für Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="caa74-309">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="caa74-310">Fortgeschrittene Konfiguration für Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="caa74-310">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="caa74-311">Überprüfen der Funktionalität des Pullservers</span><span class="sxs-lookup"><span data-stu-id="caa74-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="caa74-312">Konfigurieren von Clients</span><span class="sxs-lookup"><span data-stu-id="caa74-312">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="caa74-313">Weitere Referenzen, Ausschnitte und Beispiele</span><span class="sxs-lookup"><span data-stu-id="caa74-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="caa74-314">Dieses Beispiel zeigt die manuelle Initiierung einer Clientverbindung (WMF5 erforderlich) zum Testen.</span><span class="sxs-lookup"><span data-stu-id="caa74-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="caa74-315">Das Cmdlet [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) wird verwendet, um einen CNAME-Datensatz zu einer DNS-Zone hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="caa74-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="caa74-316">Die PowerShell-Funktion [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) (Erstellen einer Prüfsumme und Veröffentlichen von DSC MOF auf einem SMB-Pullserver) generiert automatisch die erforderlichen Prüfsumme, und kopiert dann die MOF-Konfiguration und die Prüfsummendateien auf den SMB-Pullserver.</span><span class="sxs-lookup"><span data-stu-id="caa74-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="caa74-317">Anhang ‒ Verstehen der ODATA-Dienstdateitypen</span><span class="sxs-lookup"><span data-stu-id="caa74-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="caa74-318">Eine Datendatei wird gespeichert, um während der Bereitstellung eines Pullservers Informationen zu erstellen, die den OData-Webdienst enthalten.</span><span class="sxs-lookup"><span data-stu-id="caa74-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="caa74-319">Wie unten beschrieben, hängt der Dateityp vom Betriebssystem ab.</span><span class="sxs-lookup"><span data-stu-id="caa74-319">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="caa74-320">**Windows Server 2012** Der Dateityp ist immer MDB.</span><span class="sxs-lookup"><span data-stu-id="caa74-320">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="caa74-321">**Windows Server 2012 R2** Der Dateityp wird standardmäßig auf EDB festgelegt, es sei denn, in der Konfiguration wird eine MDB-Datei angegeben.</span><span class="sxs-lookup"><span data-stu-id="caa74-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="caa74-322">Im [erweiterte Beispielskript](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) für die Installation eines Pullservers finden Sie außerdem ein Beispiel für die automatische Steuerung der web.config-Dateieinstellungen, um mögliche Fehler durch den Dateityp zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="caa74-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
