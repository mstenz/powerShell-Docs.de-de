---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISESnippet-Objekt
ms.openlocfilehash: 62d470569deb051fca80005235d4c492319cf5ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028890"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="0263e-103">Das ISESnippet-Objekt</span><span class="sxs-lookup"><span data-stu-id="0263e-103">The ISESnippetObject</span></span>

<span data-ttu-id="0263e-104">Ein **ISESnippet**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISESnippet-Klasse.</span><span class="sxs-lookup"><span data-stu-id="0263e-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="0263e-105">Die Member der **$psISE.CurrentPowerShellTab.Snippets**-Sammlung sind Beispiele für **ISESnippet**-Objekte.</span><span class="sxs-lookup"><span data-stu-id="0263e-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="0263e-106">Die einfachste Möglichkeit zum Erstellen eines Codeausschnitts ist die Verwendung des [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0)-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0263e-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="0263e-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="0263e-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="0263e-108">Autor</span><span class="sxs-lookup"><span data-stu-id="0263e-108">Author</span></span>

<span data-ttu-id="0263e-109">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="0263e-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="0263e-110">Die schreibgeschützte Eigenschaft, die den Namen des Autors des Codeausschnitts abruft.</span><span class="sxs-lookup"><span data-stu-id="0263e-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="0263e-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="0263e-111">CodeFragment</span></span>

<span data-ttu-id="0263e-112">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="0263e-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="0263e-113">Die schreibgeschützte Eigenschaft, die das im Editor einzufügende Codefragment abruft.</span><span class="sxs-lookup"><span data-stu-id="0263e-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="0263e-114">Abkürzung</span><span class="sxs-lookup"><span data-stu-id="0263e-114">Shortcut</span></span>

<span data-ttu-id="0263e-115">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="0263e-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="0263e-116">Die schreibgeschützte Eigenschaft, die die Windows-Tastenkombination für das Menüelement abruft.</span><span class="sxs-lookup"><span data-stu-id="0263e-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="0263e-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0263e-117">See Also</span></span>

- [<span data-ttu-id="0263e-118">Das ISESnippetCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="0263e-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="0263e-119">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="0263e-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="0263e-120">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="0263e-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
