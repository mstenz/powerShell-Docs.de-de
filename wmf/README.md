---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="windows-management-framework"></a><span data-ttu-id="0c84a-103">Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="0c84a-103">Windows Management Framework</span></span>

<span data-ttu-id="0c84a-104">Windows Management Framework (WMF) ist der Mechanismus, der eine einheitliche Verwaltungsschnittstelle zwischen den verschiedenen Versionen von Windows und Windows Server bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="0c84a-104">Windows Management Framework (WMF) is the delivery mechanism that provides a consistent management interface across the various flavors of Windows and Windows Server.</span></span>
<span data-ttu-id="0c84a-105">Bei Installation von WMF erhalten Kunden ein nahtloses Verfahren zum gemeinsamen Betrieb verschiedener Kombinationen von Betriebssystemen in ihrer Umgebung.</span><span class="sxs-lookup"><span data-stu-id="0c84a-105">With the installation of WMF, customers get a seamless way to interoperate between mixes of OSes in their environment.</span></span>
<span data-ttu-id="0c84a-106">WMF stellt die Updates für die Verwaltungsfunktionalität in einer bestimmten Version von Windows und Windows Server zur Verfügung, damit diese in niedrigeren Versionen (in der Regel 2 niedrigeren Versionen) von Windows und Windows Server installiert werden.</span><span class="sxs-lookup"><span data-stu-id="0c84a-106">WMF makes the updates to management functionality, in a given release of Windows and Windows Server, available for installation on lower versions (typically, 2 lower versions) of Windows and Windows Server.</span></span>

<span data-ttu-id="0c84a-107">Bei der WMF-Installation werden die folgenden Features hinzugefügt bzw. aktualisiert:</span><span class="sxs-lookup"><span data-stu-id="0c84a-107">WMF installation adds and/or updates the following features:</span></span>

- <span data-ttu-id="0c84a-108">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0c84a-108">Windows PowerShell</span></span>
- <span data-ttu-id="0c84a-109">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="0c84a-109">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="0c84a-110">Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="0c84a-110">Windows PowerShell Integrated Script Environment (ISE)</span></span>
- <span data-ttu-id="0c84a-111">Windows-Remoteverwaltung (WinRM)</span><span class="sxs-lookup"><span data-stu-id="0c84a-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="0c84a-112">Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI)</span><span class="sxs-lookup"><span data-stu-id="0c84a-112">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="0c84a-113">Windows PowerShell-Webdienste (Verwaltung der OData-IIS-Erweiterung)</span><span class="sxs-lookup"><span data-stu-id="0c84a-113">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="0c84a-114">Protokollierung des Softwarebestands (Software Inventory Logging, SIL)</span><span class="sxs-lookup"><span data-stu-id="0c84a-114">Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="0c84a-115">CIM-Anbieter für Server-Manager</span><span class="sxs-lookup"><span data-stu-id="0c84a-115">Server Manager CIM Provider</span></span>

## <a name="wmf-release-notes"></a><span data-ttu-id="0c84a-116">Anmerkungen zur WMF-Version</span><span class="sxs-lookup"><span data-stu-id="0c84a-116">WMF Release Notes</span></span>
<span data-ttu-id="0c84a-117">Um die verschiedenen Verbesserungen an PowerShell und anderen Komponenten einer bestimmten WMF-Version kennenzulernen, klicken Sie auf die nachstehenden Links, um die Anmerkungen zur jeweiligen Version zu prüfen:</span><span class="sxs-lookup"><span data-stu-id="0c84a-117">To learn about various enhancements in PowerShell and other components of a given WMF, please refer to the links below to review the release notes:</span></span>


- [<span data-ttu-id="0c84a-118">WMF 5.1 (Preview)</span><span class="sxs-lookup"><span data-stu-id="0c84a-118">WMF 5.1 (Preview)</span></span>](5.1/release-notes.md)
- [<span data-ttu-id="0c84a-119">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="0c84a-119">WMF 5.0</span></span>](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a><span data-ttu-id="0c84a-120">Verfügbarkeit von WMF unter Windows-Betriebssystemen</span><span class="sxs-lookup"><span data-stu-id="0c84a-120">WMF Availability Across Windows Operating Systems</span></span>

><span data-ttu-id="0c84a-121">AUFGABE: Links zu bestimmten WMF DLC für die Spaltenüberschrift hinzufügen</span><span class="sxs-lookup"><span data-stu-id="0c84a-121">TODO: Add links to specific WMF DLC on the column header</span></span>

| <span data-ttu-id="0c84a-122">Betriebssystemversion</span><span class="sxs-lookup"><span data-stu-id="0c84a-122">Operating System Version</span></span> | [<span data-ttu-id="0c84a-123">WMF 5.1 Preview*</span><span class="sxs-lookup"><span data-stu-id="0c84a-123">WMF 5.1 Preview*</span></span>]() | [<span data-ttu-id="0c84a-124">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="0c84a-124">WMF 5.0</span></span>]() | [<span data-ttu-id="0c84a-125">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="0c84a-125">WMF 4.0</span></span>]() |  [<span data-ttu-id="0c84a-126">WMF 3.0</span><span class="sxs-lookup"><span data-stu-id="0c84a-126">WMF 3.0</span></span>]() | [<span data-ttu-id="0c84a-127">WMF (2.0)</span><span class="sxs-lookup"><span data-stu-id="0c84a-127">WMF (2.0)</span></span>]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| <span data-ttu-id="0c84a-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="0c84a-128">Windows Server 2016</span></span> | <span data-ttu-id="0c84a-129">Im Lieferumfang*</span><span class="sxs-lookup"><span data-stu-id="0c84a-129">Ships in-box*</span></span> | <span data-ttu-id="0c84a-130">Im Lieferumfang*</span><span class="sxs-lookup"><span data-stu-id="0c84a-130">Ships in-box*</span></span> |  |  |  |
| <span data-ttu-id="0c84a-131">Windows 10</span><span class="sxs-lookup"><span data-stu-id="0c84a-131">Windows 10</span></span> | <span data-ttu-id="0c84a-132">Im Lieferumfang*</span><span class="sxs-lookup"><span data-stu-id="0c84a-132">Ships in-box*</span></span> | <span data-ttu-id="0c84a-133">Im Lieferumfang*</span><span class="sxs-lookup"><span data-stu-id="0c84a-133">Ships in-box*</span></span>  | | | |  
| <span data-ttu-id="0c84a-134">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="0c84a-134">Windows Server 2012 R2</span></span>| <span data-ttu-id="0c84a-135">??</span><span class="sxs-lookup"><span data-stu-id="0c84a-135">??</span></span> | <span data-ttu-id="0c84a-136">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-136">Yes</span></span> | <span data-ttu-id="0c84a-137">Im Lieferumfang</span><span class="sxs-lookup"><span data-stu-id="0c84a-137">Ships in-box</span></span> |  |  |
| <span data-ttu-id="0c84a-138">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="0c84a-138">Windows 8.1</span></span> | <span data-ttu-id="0c84a-139">??</span><span class="sxs-lookup"><span data-stu-id="0c84a-139">??</span></span> | <span data-ttu-id="0c84a-140">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-140">Yes</span></span> |  <span data-ttu-id="0c84a-141">Im Lieferumfang</span><span class="sxs-lookup"><span data-stu-id="0c84a-141">Ships in-box</span></span> |  |  |
| <span data-ttu-id="0c84a-142">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="0c84a-142">Windows Server 2012</span></span> | <span data-ttu-id="0c84a-143">??</span><span class="sxs-lookup"><span data-stu-id="0c84a-143">??</span></span> | <span data-ttu-id="0c84a-144">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-144">Yes</span></span> | <span data-ttu-id="0c84a-145">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-145">Yes</span></span> |  <span data-ttu-id="0c84a-146">Im Lieferumfang</span><span class="sxs-lookup"><span data-stu-id="0c84a-146">Ships in-box</span></span> | |
| <span data-ttu-id="0c84a-147">Windows 8</span><span class="sxs-lookup"><span data-stu-id="0c84a-147">Windows 8</span></span> |  |  |  | <span data-ttu-id="0c84a-148">Im Lieferumfang</span><span class="sxs-lookup"><span data-stu-id="0c84a-148">Ships in-box</span></span> | |
| <span data-ttu-id="0c84a-149">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="0c84a-149">Windows Server 2008 R2 SP1</span></span> | <span data-ttu-id="0c84a-150">??</span><span class="sxs-lookup"><span data-stu-id="0c84a-150">??</span></span> | <span data-ttu-id="0c84a-151">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-151">Yes</span></span> | <span data-ttu-id="0c84a-152">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-152">Yes</span></span> |  <span data-ttu-id="0c84a-153">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-153">Yes</span></span>| <span data-ttu-id="0c84a-154">Im Lieferumfang</span><span class="sxs-lookup"><span data-stu-id="0c84a-154">Ships in-box</span></span> |
| <span data-ttu-id="0c84a-155">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="0c84a-155">Windows 7 SP1</span></span>  | <span data-ttu-id="0c84a-156">??</span><span class="sxs-lookup"><span data-stu-id="0c84a-156">??</span></span> | <span data-ttu-id="0c84a-157">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-157">Yes</span></span> | <span data-ttu-id="0c84a-158">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-158">Yes</span></span> | <span data-ttu-id="0c84a-159">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-159">Yes</span></span> | <span data-ttu-id="0c84a-160">Im Lieferumfang</span><span class="sxs-lookup"><span data-stu-id="0c84a-160">Ships in-box</span></span> |
| <span data-ttu-id="0c84a-161">Windows Server 2008 SP2</span><span class="sxs-lookup"><span data-stu-id="0c84a-161">Windows Server 2008 SP2</span></span> | | | | <span data-ttu-id="0c84a-162">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-162">Yes</span></span> | <span data-ttu-id="0c84a-163">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-163">Yes</span></span> |
| <span data-ttu-id="0c84a-164">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="0c84a-164">Windows Vista</span></span> | | | | | <span data-ttu-id="0c84a-165">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-165">Yes</span></span> |
| <span data-ttu-id="0c84a-166">WindowsServer 2003</span><span class="sxs-lookup"><span data-stu-id="0c84a-166">Windows Server 2003</span></span>| | | |  | <span data-ttu-id="0c84a-167">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-167">Yes</span></span> |
| <span data-ttu-id="0c84a-168">Windows XP</span><span class="sxs-lookup"><span data-stu-id="0c84a-168">Windows XP</span></span> | | | |  | <span data-ttu-id="0c84a-169">Ja</span><span class="sxs-lookup"><span data-stu-id="0c84a-169">Yes</span></span> |

><span data-ttu-id="0c84a-170">AUFGABE: * in der obigen Tabelle erläutern</span><span class="sxs-lookup"><span data-stu-id="0c84a-170">TODO: Explain * in the above table</span></span>
