---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: Infodatei
ms.technology: powershell
ms.openlocfilehash: b0ef4ff685b82e1a4e9ab83a45736720df7b39a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="just-enough-administration"></a><span data-ttu-id="1f4b9-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="1f4b9-103">Just Enough Administration</span></span>
<span data-ttu-id="1f4b9-104">Just Enough Administration (JEA) ist eine Sicherheitstechnologie, die eine delegierte Verwaltung für sämtliche Elemente ermöglicht, die in PowerShell verwaltet werden können.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="1f4b9-105">Mit JEA ist Folgendes möglich:</span><span class="sxs-lookup"><span data-stu-id="1f4b9-105">With JEA, you can:</span></span>
- <span data-ttu-id="1f4b9-106">**Reduzieren Sie die Anzahl von Administratoren auf Ihren Computern**, indem Sie virtuelle Konten nutzen, die privilegierte Aktionen für normale Benutzer ausführen.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="1f4b9-107">**Beschränken Sie Benutzeraktionen**, indem Sie die Cmdlets, Funktionen und externen Befehle festlegen, die von Benutzern ausgeführt werden dürfen.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="1f4b9-108">**Verschaffen Sie sich genauere Kenntnis darüber, was Ihre Benutzer tun**, indem Sie Aufzeichnungen mitschneiden, die Ihnen genau zeigen, welche Befehle ein Benutzer während einer Sitzung ausgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-108">**Better understand what your users are doing** with "over the shoulder" transcriptions that show you exactly what commands a user executed during a session.</span></span>

<span data-ttu-id="1f4b9-109">**Warum ist das so wichtig?**</span><span class="sxs-lookup"><span data-stu-id="1f4b9-109">**Why is this important?**</span></span>  
<span data-ttu-id="1f4b9-110">Betrachten Sie das gängige Szenario, bei dem Ihre DNS-Server mit Ihren Active Directory-Domänencontrollern zusammengestellt sind.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-110">Consider the common scenario where your DNS servers are co-located with your Active Directory Domain Controllers.</span></span>
<span data-ttu-id="1f4b9-111">Ihre DNS-Administratoren müssen lokale Administratorrechte besitzen, um Probleme mit dem DNS-Server beheben zu können. Zu diesem Zweck müssen Sie sie zu Mitgliedern der Sicherheitsgruppe „Domänen-Admins“ machen, die über weit reichende Berechtigungen verfügt.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-111">Your DNS administrators need to have local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="1f4b9-112">Damit erhalten DNS-Administratoren letztendlich Kontrolle über Ihre gesamte Domäne sowie Zugriff auf alle Ressourcen auf diesem Computer.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-112">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="1f4b9-113">Mit JEA können Sie eine Rolle für die DNS-Administratoren konfigurieren, die ihnen Zugriff auf alle Befehle gewährt, die sie für ihre Arbeit benötigen – mehr jedoch nicht.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-113">With JEA in place, you can configure a role for your DNS administrators that gives them access to all the commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="1f4b9-114">Das bedeutet, dass Sie ihnen den entsprechenden Zugriff gewähren können, damit ein beschädigter DNS-Cache repariert werden kann, ohne gleichzeitig unbeabsichtigt Berechtigungen für Active Directory, das Durchsuchen des Dateisystems oder die Ausführung potenziell gefährlicher Skripts zu erteilen.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-114">This means you can provide the appropriate access to repair a poisoned DNS cache without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="1f4b9-115">Wenn die JEA-Sitzung so konfiguriert ist, dass einmalige privilegierte virtuelle Konten verwendet werden, können Ihre DNS-Administratoren überdies eine Verbindung mit dem Server als *nicht privilegierte* Benutzer herstellen und trotzdem Befehle ausführen, für die Berechtigungen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-115">Better yet, when the JEA session is configured to use one-time privileged virtual accounts, your DNS administrators can connect to the server using *unprivileged* credentials and still be able to run privileged commands.</span></span>

## <a name="availability"></a><span data-ttu-id="1f4b9-116">Verfügbarkeit</span><span class="sxs-lookup"><span data-stu-id="1f4b9-116">Availability</span></span>
<span data-ttu-id="1f4b9-117">JEA wird parallel zu Windows Server 2016 entwickelt und steht in älteren Windows-Versionen über Updates des Windows Management Frameworks zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-117">JEA is being developed in parallel to Windows Server 2016, and is available on older versions of Windows through Windows Management Framework updates.</span></span>
<span data-ttu-id="1f4b9-118">Das aktuelle JEA-Release ist auf den folgenden Plattformen verfügbar:</span><span class="sxs-lookup"><span data-stu-id="1f4b9-118">The current release of JEA is available on the following platforms:</span></span>

<span data-ttu-id="1f4b9-119">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="1f4b9-119">**Windows Server**</span></span>
- <span data-ttu-id="1f4b9-120">Windows Server 2016 Technical Preview 4 und höher</span><span class="sxs-lookup"><span data-stu-id="1f4b9-120">Windows Server 2016 Technical Preview 4 and higher</span></span>
- <span data-ttu-id="1f4b9-121">Windows Server 2012 R2, 2012 und 2008 R2\* mit installiertem [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)</span><span class="sxs-lookup"><span data-stu-id="1f4b9-121">Windows Server 2012 R2, 2012, and 2008 R2\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="1f4b9-122">**Windows Client**</span><span class="sxs-lookup"><span data-stu-id="1f4b9-122">**Windows Client**</span></span>
- <span data-ttu-id="1f4b9-123">Windows 10 mit installiertem November-Update (1511)</span><span class="sxs-lookup"><span data-stu-id="1f4b9-123">Windows 10 with the November Update (1511) installed</span></span>
- <span data-ttu-id="1f4b9-124">Windows 8.1, 8 und 7\* mit installiertem [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395)</span><span class="sxs-lookup"><span data-stu-id="1f4b9-124">Windows 8.1, 8, and 7\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="1f4b9-125">\* Unterstützung für virtuelle JEA-Sitzungen steht in Windows Server 2008 R2 und Windows 7 derzeit nicht zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-125">\* Support for virtual accounts in JEA sessions is currently not available on Windows Server 2008 R2 or Windows 7.</span></span>


## <a name="explore-the-experience-guide"></a><span data-ttu-id="1f4b9-126">Einführungsleitfaden zu JEA</span><span class="sxs-lookup"><span data-stu-id="1f4b9-126">Explore the experience guide</span></span>
<span data-ttu-id="1f4b9-127">Sind Sie bereit zu erfahren, wie Sie selbst einen JEA-Endpunkt erstellen, bereitstellen und verwenden?</span><span class="sxs-lookup"><span data-stu-id="1f4b9-127">Ready to learn how to author, deploy, and use your own JEA endpoint?</span></span>

<span data-ttu-id="1f4b9-128">Dieser Leitfaden bietet einen schnellen Einstieg und vermittelt anhand eines vorgefertigten JEA-Endpunkts eine Vorstellung von der Endbenutzererfahrung. Anschließend führt der Leitfaden Sie durch den Prozess der Neuerstellung eines Endpunkts, um dabei Konzepte wie Sitzungskonfigurationen und Rollenfunktionen zu erläutern.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-128">This guide gets you started quickly with a pre-built JEA endpoint to get an idea of what the end-user experience is like, then walks you through recreating an endpoint from scratch to help demonstrate concepts like session configurations and Role Capabilities.</span></span>

1.  <span data-ttu-id="1f4b9-129">[Einführung](introduction.md) </span><span class="sxs-lookup"><span data-stu-id="1f4b9-129">[Introduction](introduction.md) </span></span>  
<span data-ttu-id="1f4b9-130">Dieses Kapitel bietet eine kurze Übersicht darüber, warum JEA für Sie interessant ist.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-130">Briefly review why you should care about JEA</span></span>

2.  [<span data-ttu-id="1f4b9-131">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1f4b9-131">Prerequisites</span></span>](prerequisites.md)  
<span data-ttu-id="1f4b9-132">In diesem Kapitel wird die Einrichtung Ihrer Umgebung erklärt.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-132">Explains how to set up your environment</span></span>

3.  [<span data-ttu-id="1f4b9-133">Verwenden von JEA</span><span class="sxs-lookup"><span data-stu-id="1f4b9-133">Using JEA</span></span>](using-jea.md)  
<span data-ttu-id="1f4b9-134">Dieses Kapitel erleichtert Ihnen den Einstieg, indem die JEA-Benutzererfahrung von Operatoren erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-134">Helps you start by understanding the operator experience of using JEA</span></span>

4.  [<span data-ttu-id="1f4b9-135">Neuerstellen der Demo</span><span class="sxs-lookup"><span data-stu-id="1f4b9-135">Remake the Demo</span></span>](remake-the-demo-endpoint.md)  
<span data-ttu-id="1f4b9-136">Erstellen Sie eine JEA-Sitzungskonfiguration von Grund auf.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-136">Create a JEA Session Configuration from scratch</span></span>

5.  [<span data-ttu-id="1f4b9-137">Rollenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1f4b9-137">Role Capabilities</span></span>](role-capabilities.md)  
<span data-ttu-id="1f4b9-138">Erfahren Sie, wie Sie JEA-Funktionen mit JEA-Rollenfunktionsdateien anpassen.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-138">Learn about how to customize JEA capabilities with Role Capability Files</span></span>

6.  [<span data-ttu-id="1f4b9-139">End-to-End – Active Directory</span><span class="sxs-lookup"><span data-stu-id="1f4b9-139">End to End - Active Directory</span></span>](end-to-end---active-directory.md)  
<span data-ttu-id="1f4b9-140">Erstellen Sie einen völlig neuen Endpunkt zur Verwaltung von Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-140">Make a whole new endpoint for managing Active Directory</span></span>

7.  [<span data-ttu-id="1f4b9-141">Bereitstellung und Wartung mehrerer Computer</span><span class="sxs-lookup"><span data-stu-id="1f4b9-141">Multi-machine Deployment and Maintenance</span></span>](multi-machine-deployment-and-maintenance.md)  
<span data-ttu-id="1f4b9-142">Erfahren Sie, wie sich die Bereitstellung und die Dokumenterstellung in Abhängigkeit vom Umfang ändern.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-142">Discover how deployment and authoring changes with scale</span></span>

8.  [<span data-ttu-id="1f4b9-143">Berichterstellung zu JEA</span><span class="sxs-lookup"><span data-stu-id="1f4b9-143">Reporting on JEA</span></span>](reporting-on-jea.md)  
<span data-ttu-id="1f4b9-144">Erfahren Sie, wie Sie alle JEA-Aktionen und die gesamte Infrastruktur überprüfen und Berichte dafür erstellen.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-144">Discover how to audit and report on all JEA actions and infrastructure</span></span>

9.  <span data-ttu-id="1f4b9-145">Anhänge</span><span class="sxs-lookup"><span data-stu-id="1f4b9-145">Appendixes</span></span>
  - [<span data-ttu-id="1f4b9-146">Wichtige Konzepte in diesem Leitfaden</span><span class="sxs-lookup"><span data-stu-id="1f4b9-146">Key Concepts Used Throughout This Guide</span></span>](key-concepts-used-throughout-this-guide.md)  
  -  [<span data-ttu-id="1f4b9-147">Erstellen eines Domänencontrollers</span><span class="sxs-lookup"><span data-stu-id="1f4b9-147">Creating a Domain Controller</span></span>](creating-a-domain-controller.md)  
  -  [<span data-ttu-id="1f4b9-148">Blacklists</span><span class="sxs-lookup"><span data-stu-id="1f4b9-148">On Blacklisting</span></span>](on-blacklisting.md)  
  -  [<span data-ttu-id="1f4b9-149">Überlegungen zum Einschränken von Befehlen</span><span class="sxs-lookup"><span data-stu-id="1f4b9-149">Considerations When Limiting Commands</span></span>](considerations-when-limiting-commands.md)  
  -  [<span data-ttu-id="1f4b9-150">Häufige Fehler bei Rollenfunktionen</span><span class="sxs-lookup"><span data-stu-id="1f4b9-150">Common Role Capability Pitfalls</span></span>](common-role-capability-pitfalls.md)

## <a name="start-authoring-your-own-jea-endpoints"></a><span data-ttu-id="1f4b9-151">Ihre ersten eigenen JEA-Endpunkte</span><span class="sxs-lookup"><span data-stu-id="1f4b9-151">Start authoring your own JEA endpoints</span></span>
<span data-ttu-id="1f4b9-152">Die Erstellung eines JEA-Endpunkts ist ganz einfach – Sie benötigen nur ein JEA-fähiges System und einen Text-Editor (wie z. B. die PowerShell ISE).</span><span class="sxs-lookup"><span data-stu-id="1f4b9-152">It's easy to author a JEA endpoint -- all you need is a JEA-enabled system and a text editor (like PowerShell ISE).</span></span>
<span data-ttu-id="1f4b9-153">Ein guter Tipp für den Einstieg: Erstellen Sie Gerüstdateien mithilfe von [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) und [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx), ohne weitere Argumente.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-153">One helpful tip to get started is to create skeleton files using [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) and [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) without any other arguments.</span></span>
<span data-ttu-id="1f4b9-154">Diese Gerüstdateien enthalten alle anwendbaren Konfigurationsfelder sowie nützliche Kommentare, die erklären, wozu welches Feld verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-154">These skeleton files contain all of the applicable configuration fields along with helpful comments to explain what each field can be used for.</span></span>

<span data-ttu-id="1f4b9-155">Um die Erstellung von JEA-Endpunkten noch einfacher zu gestalten, lesen Sie den Blog [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx). In diesem Blog finden Sie eine GUI, mit deren Hilfe Sie Sitzungskonfigurations- und Rollenfunktionsdateien erstellen können.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-155">To make authoring JEA endpoints even easier, check out the [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) which provides a GUI with which you can author Session Configuration and Role Capability files.</span></span>
<span data-ttu-id="1f4b9-156">Die GUI unterstützt sogar die Erstellung von Rollenfunktionen basierend auf PowerShell-Protokollen, sodass Sie mit den Befehlen beginnen können, die Ihre Benutzer regelmäßig für ihre Arbeit ausführen.</span><span class="sxs-lookup"><span data-stu-id="1f4b9-156">It even supports generating Role Capabilities based on PowerShell logs to start you off with the commands your users regularly run to get their jobs done.</span></span>

