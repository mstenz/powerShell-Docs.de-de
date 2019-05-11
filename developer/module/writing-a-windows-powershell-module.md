---
title: Schreiben eines Windows PowerShell-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229351"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="0dfc0-102">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="0dfc0-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="0dfc0-103">Dieses Dokument richtet sich an Administratoren, Skriptentwickler und Cmdlet-Entwickler, die zum Verpacken und verteilen ihre Windows PowerShell-Cmdlets müssen.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="0dfc0-104">Mit Windows PowerShell-Module, können Sie verpacken und verteilen Ihre Windows PowerShell-Lösungen ohne Verwendung einer kompilierten Sprache.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="0dfc0-105">Windows PowerShell-Module ermöglichen Ihnen die Partition, organisieren und abstrahieren von Ihren Windows PowerShell-Code in eigenständige, wieder verwendbaren Einheiten.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="0dfc0-106">Mit diesen wieder verwendbaren Einheiten können Sie ganz einfach Ihre Module direkt für andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="0dfc0-107">Wenn Sie ein Skriptentwickler sind, können Sie auch von Drittanbietern Module zum Erstellen von benutzerdefinierter Skript basierende Anwendungen erneut verpacken.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="0dfc0-108">Module, wie Module, die in anderen Skriptsprachen wie Perl und Python, bietet produktionsbereite skriptlösungen, die wiederverwendbare verteilbare Komponenten mit den zusätzlichen Vorteil, sodass Sie neu zu verpacken und mehrere Komponenten für das abstrakte Erstellen Sie benutzerdefinierte Lösungen.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="0dfc0-109">Auf die grundlegendste Windows PowerShell behandelt alle gültigen Windows PowerShell-Skriptcode, die in einer psm1-Datei als Modul gespeichert.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="0dfc0-110">PowerShell behandelt jede Assembly binäre Cmdlet auch automatisch als Modul.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="0dfc0-111">Sie können jedoch auch ein Modul (oder genauer gesagt, ein modulmanifest) zum Bündeln einer gesamten Projektmappe verwenden.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="0dfc0-112">Die folgenden Szenarien beschreiben typische Verwendungen für Windows PowerShell-Module.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="0dfc0-113">Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="0dfc0-113">Libraries</span></span>

<span data-ttu-id="0dfc0-114">Module können verwendet werden, Verpacken und verteilen zusammenhängende Bibliotheken mit Funktionen, die allgemeine Aufgaben ausführen.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="0dfc0-115">Im Allgemeinen haben die Namen dieser Funktionen eine oder mehrere Nomen, die die häufige Aufgabe widerspiegeln, der sie verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="0dfc0-116">Diese Funktionen können auch wie .NET Framework-Klassen sein, dass sie die öffentlichen und privaten Member besitzen können.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="0dfc0-117">Beispielsweise kann eine Bibliothek eine Reihe von Funktionen für die Übertragung von Dateien enthalten.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="0dfc0-118">In diesem Fall das Nomen reflektieren die Aufgabe "Datei". möglicherweise</span><span class="sxs-lookup"><span data-stu-id="0dfc0-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="0dfc0-119">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="0dfc0-119">Configuration</span></span>

<span data-ttu-id="0dfc0-120">Module können verwendet werden, um Ihre Umgebung anzupassen, durch das Hinzufügen von bestimmten Cmdlets, Anbieter, Funktionen und Variablen.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="0dfc0-121">Kompilierter Code-Entwicklung und Verteilung</span><span class="sxs-lookup"><span data-stu-id="0dfc0-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="0dfc0-122">Cmdlet- und Anbieternamen-Entwickler können die Module verwenden, um zu testen und Verteilen ihrer kompilierten Code ohne-Snap-ins erstellen zu müssen. Sie können die Assembly mit den kompilierten Code als Modul (einem binären Modul) importieren, ohne zum Erstellen und registrieren-Snap-ins.</span><span class="sxs-lookup"><span data-stu-id="0dfc0-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="0dfc0-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0dfc0-123">See Also</span></span>

[<span data-ttu-id="0dfc0-124">Grundlegendes zu einem Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="0dfc0-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="0dfc0-125">Gewusst wie: Schreiben ein PowerShell-Skript-Moduls</span><span class="sxs-lookup"><span data-stu-id="0dfc0-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="0dfc0-126">Gewusst wie: Schreiben ein Moduls für PowerShell-Binärdateien</span><span class="sxs-lookup"><span data-stu-id="0dfc0-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="0dfc0-127">Gewusst wie: Schreiben Sie ein PowerShell-Modulmanifest</span><span class="sxs-lookup"><span data-stu-id="0dfc0-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="0dfc0-128">Ändern den PSModulePath-Installationspfad</span><span class="sxs-lookup"><span data-stu-id="0dfc0-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="0dfc0-129">Importieren eines PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="0dfc0-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="0dfc0-130">Installieren eines PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="0dfc0-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
