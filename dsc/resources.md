---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: DSC-Ressourcen
ms.openlocfilehash: 0994616673b5e447c69c09154bfdb9b9126a88c8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="7d217-103">DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="7d217-103">DSC Resources</span></span>

><span data-ttu-id="7d217-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7d217-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7d217-105">DSC-Ressourcen sind die Bausteine einer DSC-Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="7d217-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="7d217-106">Eine Ressource macht Eigenschaften verfügbar, die konfiguriert werden können (Schema), und enthält die PowerShell-Skriptfunktionen, die der lokale Konfigurations-Manager wie gewünscht ausführt.</span><span class="sxs-lookup"><span data-stu-id="7d217-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="7d217-107">Mit einer Ressource kann etwas Allgemeines wie eine Datei oder Spezifisches wie eine IIS-Servereinstellung modelliert werden.</span><span class="sxs-lookup"><span data-stu-id="7d217-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="7d217-108">Gruppen ähnlicher Ressourcen werden in einem DSC-Modul kombiniert, das alle erforderlichen Dateien in einer Struktur organisiert, die portierbar ist und Metadaten zum Bestimmen des Zwecks der Ressourcen enthält.</span><span class="sxs-lookup"><span data-stu-id="7d217-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="7d217-109">In den folgenden Themen werden DSC-Ressourcen beschrieben:</span><span class="sxs-lookup"><span data-stu-id="7d217-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="7d217-110">Integrierte DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="7d217-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="7d217-111">Erstellen benutzerdefinierter DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="7d217-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="7d217-112">Integrierte DSC-Ressourcen für Linux</span><span class="sxs-lookup"><span data-stu-id="7d217-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

