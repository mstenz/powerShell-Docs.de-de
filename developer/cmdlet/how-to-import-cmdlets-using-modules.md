---
title: 'Gewusst wie: Importieren von Modulen mit Cmdlets | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859146"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="e6d21-102">Importieren von Cmdlets mit Modulen</span><span class="sxs-lookup"><span data-stu-id="e6d21-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="e6d21-103">Dieses Thema beschreibt, wie Sie Cmdlets in einer Windows PowerShell-Sitzung zu importieren, mit einem binären Modul.</span><span class="sxs-lookup"><span data-stu-id="e6d21-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="e6d21-104">Die Elemente der Module zählen die Cmdlets, Anbieter, Funktionen, Variablen, Aliase und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="e6d21-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="e6d21-105">-Snap-ins können nur Cmdlets und Anbieter enthalten.</span><span class="sxs-lookup"><span data-stu-id="e6d21-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="e6d21-106">Gewusst wie: Laden Sie ein Modul mit cmdlets</span><span class="sxs-lookup"><span data-stu-id="e6d21-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="e6d21-107">Erstellen Sie einen Ordner "Module", die den gleichen Namen wie die Assemblydatei hat in der die Cmdlets implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="e6d21-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="e6d21-108">In diesem Verfahren wird der Ordner "Module" erstellt, der `system32` Ordner.</span><span class="sxs-lookup"><span data-stu-id="e6d21-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="e6d21-109">Stellen Sie sicher, dass die `PSModulePath` Umgebungsvariable enthält den Pfad zu Ihrem Ordner "Module".</span><span class="sxs-lookup"><span data-stu-id="e6d21-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="e6d21-110">Wird standardmäßig der Ordner "System" wurde bereits hinzugefügt der `PSModulePath` -Umgebungsvariablen angegeben.</span><span class="sxs-lookup"><span data-stu-id="e6d21-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="e6d21-111">Kopieren Sie die Cmdlet-Assembly, in dem Ordner "Module".</span><span class="sxs-lookup"><span data-stu-id="e6d21-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="e6d21-112">Führen Sie den folgenden Befehl zum Hinzufügen der Cmdlets für die Sitzung ein:</span><span class="sxs-lookup"><span data-stu-id="e6d21-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="e6d21-113">Dieses Verfahren kann verwendet werden, um Ihre Cmdlets zu testen.</span><span class="sxs-lookup"><span data-stu-id="e6d21-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="e6d21-114">Alle Cmdlets hinzugefügt in der Assembly mit der Sitzung.</span><span class="sxs-lookup"><span data-stu-id="e6d21-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="e6d21-115">Weitere Informationen zu Modulen, die verschiedenen Arten von Modulen, die verschiedenen Methoden zum Laden von Modulen und wie Sie die Elemente eines Moduls zu beschränken, die exportiert werden, finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="e6d21-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6d21-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e6d21-116">See Also</span></span>

[<span data-ttu-id="e6d21-117">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e6d21-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="e6d21-118">Installieren von Modulen</span><span class="sxs-lookup"><span data-stu-id="e6d21-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)