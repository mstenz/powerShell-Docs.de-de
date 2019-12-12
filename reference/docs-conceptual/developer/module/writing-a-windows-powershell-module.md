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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360619"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="7e065-102">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="7e065-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="7e065-103">Dieses Dokument ist für Administratoren, Skriptentwickler und Cmdlet-Entwickler geschrieben, die Ihre Windows PowerShell-Cmdlets Verpacken und verteilen müssen.</span><span class="sxs-lookup"><span data-stu-id="7e065-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="7e065-104">Mithilfe von Windows PowerShell-Modulen können Sie Windows PowerShell-Lösungen Verpacken und verteilen, ohne eine kompilierte Sprache zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7e065-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="7e065-105">Mit Windows PowerShell-Modulen können Sie Ihren Windows PowerShell-Code in eigenständige, wiederverwendbare Einheiten partitionieren, organisieren und abstrahieren.</span><span class="sxs-lookup"><span data-stu-id="7e065-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="7e065-106">Mit diesen wiederverwendbaren Einheiten können Sie Ihre Module problemlos direkt für andere freigeben.</span><span class="sxs-lookup"><span data-stu-id="7e065-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="7e065-107">Wenn Sie ein Skriptentwickler sind, können Sie auch Drittanbieter Module neu verpacken, um benutzerdefinierte skriptbasierte Anwendungen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7e065-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="7e065-108">Module, die mit Modulen in anderen Skriptsprachen wie z. b. perl und python vergleichbar sind, ermöglichen die Bereitstellung von Skript Erstellungs Lösungen, die wiederverwendbare, verteilbare Komponenten verwenden, mit dem zusätzlichen Vorteil, dass Sie mehrere Komponenten erneut Verpacken und abstrahieren können. Erstellen Sie benutzerdefinierte Lösungen.</span><span class="sxs-lookup"><span data-stu-id="7e065-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="7e065-109">Windows PowerShell behandelt in den meisten Fällen jeden gültigen Windows PowerShell-Skriptcode, der in einer psm1-Datei gespeichert ist, als Modul.</span><span class="sxs-lookup"><span data-stu-id="7e065-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="7e065-110">PowerShell behandelt auch automatisch jede binäre Cmdlet-Assembly als Modul.</span><span class="sxs-lookup"><span data-stu-id="7e065-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="7e065-111">Sie können jedoch auch ein Modul (oder genauer gesagt, ein Modul Manifest) verwenden, um eine gesamte Projekt Mappe zusammenzufassen.</span><span class="sxs-lookup"><span data-stu-id="7e065-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="7e065-112">In den folgenden Szenarien werden typische Verwendungsmöglichkeiten für Windows PowerShell-Module beschrieben.</span><span class="sxs-lookup"><span data-stu-id="7e065-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="7e065-113">Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="7e065-113">Libraries</span></span>

<span data-ttu-id="7e065-114">Module können zum Verpacken und Verteilen von zusammenhängenden Bibliotheken von Funktionen verwendet werden, die allgemeine Aufgaben ausführen.</span><span class="sxs-lookup"><span data-stu-id="7e065-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="7e065-115">In der Regel verwenden die Namen dieser Funktionen ein oder mehrere Nomen, die die allgemeine Aufgabe widerspiegeln, für die Sie verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7e065-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="7e065-116">Diese Funktionen können auch .NET Framework Klassen in ähneln, dass Sie öffentliche und private Member haben können.</span><span class="sxs-lookup"><span data-stu-id="7e065-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="7e065-117">Eine Bibliothek kann z. b. eine Reihe von Funktionen für Dateiübertragungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="7e065-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="7e065-118">In diesem Fall kann das Substantiv, das die allgemeine Aufgabe widerspiegelt, "file" lauten.</span><span class="sxs-lookup"><span data-stu-id="7e065-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="7e065-119">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="7e065-119">Configuration</span></span>

<span data-ttu-id="7e065-120">Module können verwendet werden, um Ihre Umgebung anzupassen, indem bestimmte Cmdlets, Anbieter, Funktionen und Variablen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="7e065-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="7e065-121">Entwicklung und Verteilung kompilierter Codes</span><span class="sxs-lookup"><span data-stu-id="7e065-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="7e065-122">Cmdlet-und Anbieter Entwickler können Module verwenden, um Ihren kompilierten Code zu testen und zu verteilen, ohne Snap-Ins erstellen zu müssen. Sie können die Assembly, die den kompilierten Code enthält, als Modul (ein binäres Modul) importieren, ohne Snap-Ins erstellen und registrieren zu müssen.</span><span class="sxs-lookup"><span data-stu-id="7e065-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e065-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7e065-123">See Also</span></span>

[<span data-ttu-id="7e065-124">Grundlegendes zu einem Windows PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="7e065-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="7e065-125">Schreiben eines PowerShell-Skript Moduls</span><span class="sxs-lookup"><span data-stu-id="7e065-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="7e065-126">Schreiben eines PowerShell-Binär Moduls</span><span class="sxs-lookup"><span data-stu-id="7e065-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="7e065-127">Schreiben eines PowerShell-Modul Manifests</span><span class="sxs-lookup"><span data-stu-id="7e065-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="7e065-128">Ändern des psmodulepath-Installations Pfads</span><span class="sxs-lookup"><span data-stu-id="7e065-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="7e065-129">Importieren eines PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="7e065-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="7e065-130">Installieren eines PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="7e065-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
