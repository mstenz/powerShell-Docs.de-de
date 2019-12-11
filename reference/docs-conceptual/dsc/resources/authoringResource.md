---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952847"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="d8f6f-103">Erstellen von benutzerdefinierten Windows PowerShell DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d8f6f-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="d8f6f-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d8f6f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d8f6f-105">Windows PowerShell DSC verfügt über integrierte Ressourcen, mit denen Sie Ihre Umgebung konfigurieren können</span><span class="sxs-lookup"><span data-stu-id="d8f6f-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="d8f6f-106">Dieses Thema enthält einen Überblick über die Entwicklung von Ressourcen sowie Links zu Themen mit speziellen Informationen und Beispielen.</span><span class="sxs-lookup"><span data-stu-id="d8f6f-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="d8f6f-107">Komponenten der DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d8f6f-107">DSC resource components</span></span>

<span data-ttu-id="d8f6f-108">Eine DSC-Ressource ist ein Windows PowerShell-Modul.</span><span class="sxs-lookup"><span data-stu-id="d8f6f-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="d8f6f-109">Das Modul enthält das Schema (die Definition der konfigurierbaren Eigenschaften) und die Implementierung (den Code, der die eigentliche durch eine Konfiguration angegebene Arbeit ausführt) für die Ressource.</span><span class="sxs-lookup"><span data-stu-id="d8f6f-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="d8f6f-110">Ein DSC-Ressourcenschema kann in einer MOF-Datei definiert werden, und die Implementierung erfolgt durch ein Skriptmodul.</span><span class="sxs-lookup"><span data-stu-id="d8f6f-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="d8f6f-111">Beginnend mit der Unterstützung von PowerShell-Klassen in Version 5 können das Schema und die Implementierung in einer Klasse definiert werden.</span><span class="sxs-lookup"><span data-stu-id="d8f6f-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="d8f6f-112">Die folgenden Themen beschreiben ausführlicher, wie Sie DSC-Ressourcen erstellen.</span><span class="sxs-lookup"><span data-stu-id="d8f6f-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="d8f6f-113">Schreiben einer benutzerdefinierten DSC-Ressource mit MOF</span><span class="sxs-lookup"><span data-stu-id="d8f6f-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="d8f6f-114">Implementieren einer DSC-Ressource in C#</span><span class="sxs-lookup"><span data-stu-id="d8f6f-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="d8f6f-115">Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen</span><span class="sxs-lookup"><span data-stu-id="d8f6f-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="d8f6f-116">Zusammengesetzte Ressourcen: Verwenden einer DSC-Konfiguration als Ressource</span><span class="sxs-lookup"><span data-stu-id="d8f6f-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="d8f6f-117">Verwenden des Ressourcen-Designers</span><span class="sxs-lookup"><span data-stu-id="d8f6f-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
