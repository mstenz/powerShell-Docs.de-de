---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Integrierte PowerShell DSC-Ressourcen für Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047358"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="63e9e-103">Integrierte PowerShell DSC-Ressourcen für Linux</span><span class="sxs-lookup"><span data-stu-id="63e9e-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="63e9e-104">Ressourcen sind Bausteine zum Schreiben eines PowerShell DSC-Skripts.</span><span class="sxs-lookup"><span data-stu-id="63e9e-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="63e9e-105">DSC für Linux bietet verschiedene integrierte Funktionen für das Konfigurieren von Ressourcen wie Dateien und Ordnern, Paketen, Umgebungsvariablen sowie Diensten und Prozessen.</span><span class="sxs-lookup"><span data-stu-id="63e9e-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="63e9e-106">Integrierte Ressourcen</span><span class="sxs-lookup"><span data-stu-id="63e9e-106">Built-in resources</span></span>

<span data-ttu-id="63e9e-107">Die folgende Tabelle bietet eine Liste dieser Ressourcen sowie Links zu Themen, in denen diese Ressourcen ausführlich beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="63e9e-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="63e9e-108">[nxArchive Ressource](lnxArchiveResource.md): Bietet einen Mechanismus zum Entpacken von Archivdateien (.tar, .zip) in einem bestimmten Pfad.</span><span class="sxs-lookup"><span data-stu-id="63e9e-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="63e9e-109">[nxEnvironment Ressource](lnxEnvironmentResource.md): Verwaltet Umgebungsvariablen auf Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="63e9e-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="63e9e-110">[nxFile Ressource](lnxFileResource.md): Verwaltet Linux-Dateien und -Verzeichnisse.</span><span class="sxs-lookup"><span data-stu-id="63e9e-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="63e9e-111">[nxFileLine Ressource](lnxFileLineResource.md): Verwaltet einzelne Zeilen in einer Linux-Datei.</span><span class="sxs-lookup"><span data-stu-id="63e9e-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="63e9e-112">[nxGroup Ressource](lnxGroupResource.md): Verwaltet lokale Linux-Gruppen.</span><span class="sxs-lookup"><span data-stu-id="63e9e-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="63e9e-113">[nxPackage Ressource](lnxPackageResource.md): Verwaltet Pakete auf Linux-Knoten.</span><span class="sxs-lookup"><span data-stu-id="63e9e-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="63e9e-114">[nxScript Ressource ](lnxScriptResource.md): Führt Skripts auf Zielknoten aus.</span><span class="sxs-lookup"><span data-stu-id="63e9e-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="63e9e-115">[nxService Ressource](lnxServiceResource.md): Verwaltet Linux-Dienste (Daemons).</span><span class="sxs-lookup"><span data-stu-id="63e9e-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="63e9e-116">[nxSshAuthorizedKeys Ressource](lnxSshAuthorizedKeysResource.md): Verwaltet öffentliche SSH-Schlüssel für einen Linux-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="63e9e-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="63e9e-117">[nxUser Ressource](lnxUserResource.md): Verwaltet lokale Linux-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="63e9e-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>