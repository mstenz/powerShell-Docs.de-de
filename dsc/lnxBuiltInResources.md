---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Integrierte PowerShell DSC-Ressourcen für Linux"
ms.openlocfilehash: b85f32f7559d89bda566d35462cc613d73424c50
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="bc4a7-103">Integrierte PowerShell DSC-Ressourcen für Linux</span><span class="sxs-lookup"><span data-stu-id="bc4a7-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="bc4a7-104">Ressourcen sind Bausteine zum Schreiben eines PowerShell DSC-Skripts.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="bc4a7-105">DSC für Linux bietet verschiedene integrierte Funktionen für das Konfigurieren von Ressourcen wie Dateien und Ordnern, Paketen, Umgebungsvariablen sowie Diensten und Prozessen.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="bc4a7-106">Integrierte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bc4a7-106">Built-in resources</span></span> 

<span data-ttu-id="bc4a7-107">Die folgende Tabelle bietet eine Liste dieser Ressourcen sowie Links zu Themen, in denen diese Ressourcen ausführlich beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="bc4a7-108">[nxArchive Ressource](lnxArchiveResource.md): Bietet einen Mechanismus zum Entpacken von Archivdateien (.tar, .zip) in einem bestimmten Pfad.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="bc4a7-109">[nxEnvironment Ressource](lnxEnvironmentResource.md): Verwaltet Umgebungsvariablen auf Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span> 
* <span data-ttu-id="bc4a7-110">[nxFile Ressource](lnxFileResource.md): Verwaltet Linux-Dateien und -Verzeichnisse.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span> 
* <span data-ttu-id="bc4a7-111">[nxFileLine Ressource](lnxFileLineResource.md): Verwaltet einzelne Zeilen in einer Linux-Datei.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span> 
* <span data-ttu-id="bc4a7-112">[nxGroup Ressource](lnxGroupResource.md): Verwaltet lokale Linux-Gruppen.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span> 
* <span data-ttu-id="bc4a7-113">[nxPackage Ressource](lnxPackageResource.md): Verwaltet Pakete auf Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="bc4a7-114">[nxScript Ressource ](lnxScriptResource.md): Führt Skripts auf Zielknoten aus.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="bc4a7-115">[nxService Ressource](lnxServiceResource.md): Verwaltet Linux-Dienste (Daemons).</span><span class="sxs-lookup"><span data-stu-id="bc4a7-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="bc4a7-116">[nxSshAuthorizedKeys Ressource](lnxSshAuthorizedKeysResource.md): Verwaltet öffentliche SSH-Schlüssel für einen Linux-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span> 
* <span data-ttu-id="bc4a7-117">[nxUser Ressource](lnxUserResource.md): Verwaltet lokale Linux-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="bc4a7-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span> 
  
