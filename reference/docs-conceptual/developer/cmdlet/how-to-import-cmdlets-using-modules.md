---
title: Importieren von Cmdlets mithilfe von Modulen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364459"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="0c383-102">Importieren von Cmdlets mit Modulen</span><span class="sxs-lookup"><span data-stu-id="0c383-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="0c383-103">In diesem Artikel wird beschrieben, wie Sie Cmdlets mithilfe eines binären Moduls in eine PowerShell-Sitzung importieren.</span><span class="sxs-lookup"><span data-stu-id="0c383-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="0c383-104">Die Member von Modulen können Cmdlets, Anbieter, Funktionen, Variablen, Aliase und vieles mehr enthalten.</span><span class="sxs-lookup"><span data-stu-id="0c383-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="0c383-105">Snap-Ins können nur Cmdlets und Anbieter enthalten.</span><span class="sxs-lookup"><span data-stu-id="0c383-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="0c383-106">Vorgehensweise beim Laden von Cmdlets mithilfe eines Moduls</span><span class="sxs-lookup"><span data-stu-id="0c383-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="0c383-107">Erstellen Sie einen Modul Ordner, der denselben Namen hat wie die Assemblydatei, in der die Cmdlets implementiert sind.</span><span class="sxs-lookup"><span data-stu-id="0c383-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="0c383-108">In diesem Verfahren wird der Modul Ordner im Ordner "Windows `system32`" erstellt.</span><span class="sxs-lookup"><span data-stu-id="0c383-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="0c383-109">Stellen Sie sicher, dass die `PSModulePath`-Umgebungsvariable den Pfad zum neuen Modul Ordner enthält.</span><span class="sxs-lookup"><span data-stu-id="0c383-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="0c383-110">Standardmäßig ist der Systemordner bereits der `PSModulePath`-Umgebungsvariablen hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0c383-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="0c383-111">Zum Anzeigen des `PSModulePath`geben Sie Folgendes ein: `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="0c383-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="0c383-112">Kopieren Sie die Cmdlet-Assembly in den Modul Ordner.</span><span class="sxs-lookup"><span data-stu-id="0c383-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="0c383-113">Fügen Sie eine Modul Manifest-Datei (`.psd1`) im Stamm Ordner des Moduls hinzu.</span><span class="sxs-lookup"><span data-stu-id="0c383-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="0c383-114">PowerShell verwendet das Modul Manifest, um das Modul zu importieren.</span><span class="sxs-lookup"><span data-stu-id="0c383-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="0c383-115">Weitere Informationen finden Sie unter Gewusst [wie: Schreiben eines PowerShell-Modul Manifests](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="0c383-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="0c383-116">Führen Sie den folgenden Befehl aus, um der Sitzung die Cmdlets hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="0c383-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="0c383-117">Mithilfe dieses Verfahrens können Sie die Cmdlets testen.</span><span class="sxs-lookup"><span data-stu-id="0c383-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="0c383-118">Der Sitzung werden alle Cmdlets in der Assembly hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0c383-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="0c383-119">Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="0c383-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c383-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0c383-120">See also</span></span>

[<span data-ttu-id="0c383-121">Schreiben eines PowerShell-Modul Manifests</span><span class="sxs-lookup"><span data-stu-id="0c383-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="0c383-122">Importieren eines PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="0c383-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="0c383-123">Import-Module</span><span class="sxs-lookup"><span data-stu-id="0c383-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="0c383-124">Installieren von Modulen</span><span class="sxs-lookup"><span data-stu-id="0c383-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="0c383-125">Ändern des psmodulepath-Installations Pfads</span><span class="sxs-lookup"><span data-stu-id="0c383-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="0c383-126">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="0c383-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
