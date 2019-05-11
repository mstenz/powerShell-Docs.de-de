---
title: 'Gewusst wie: Schreiben ein PowerShell-Binärdateien-Moduls | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229336"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="a09fc-102">Schreiben eines PowerShell-Binärmoduls</span><span class="sxs-lookup"><span data-stu-id="a09fc-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="a09fc-103">Ein binäres Modul kann es sich um eine beliebige Assembly (DLL) sein, die Cmdlet-Klassen enthält.</span><span class="sxs-lookup"><span data-stu-id="a09fc-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="a09fc-104">Standardmäßig werden alle Cmdlets in der Assembly importiert, wenn das binäre Modul importiert wird.</span><span class="sxs-lookup"><span data-stu-id="a09fc-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="a09fc-105">Allerdings können Sie die Cmdlets beschränken, die importiert werden, erstellen Sie ein modulmanifest, dessen stammmodul die Assembly ist.</span><span class="sxs-lookup"><span data-stu-id="a09fc-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="a09fc-106">(Z. B. der Schlüssel CmdletsToExport des Manifests dienen nur diese Cmdlets zu exportieren, die erforderlich sind.) Darüber hinaus kann ein binäres Modul enthalten, zusätzliche Dateien, eine Verzeichnisstruktur und andere Angaben hilfreiches Verwaltungstool, für die ein einzelnes Cmdlet nicht.</span><span class="sxs-lookup"><span data-stu-id="a09fc-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="a09fc-107">Das folgende Verfahren beschreibt die zum Erstellen und ein binäres PowerShell-Modul installieren.</span><span class="sxs-lookup"><span data-stu-id="a09fc-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="a09fc-108">Das Erstellen und installieren ein binäres PowerShell-Modul</span><span class="sxs-lookup"><span data-stu-id="a09fc-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="a09fc-109">Erstellen Sie eine binäre PowerShell-Projektmappe (z. B. ein Cmdlet in geschriebenen C#), mit den Funktionen benötigt werden, und stellen Sie sicher, dass es ordnungsgemäß ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a09fc-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="a09fc-110">Hinsichtlich der Code ist der Kern von einem binären Modul einfach eine Cmdlet-Assembly.</span><span class="sxs-lookup"><span data-stu-id="a09fc-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="a09fc-111">In der Tat werden in PowerShell eine einzelnes Cmdlet-Assembly als Modul im Hinblick auf das Laden und Entladen von Assemblys, mit keinen zusätzlichen Aufwand seitens des Entwicklers behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="a09fc-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="a09fc-112">Weitere Informationen zu einem Cmdlet schreiben, finden Sie unter [Schreiben eines Windows PowerShell-Cmdlets](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="a09fc-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="a09fc-113">Erstellen Sie bei Bedarf den Rest der Lösung: (Weitere Cmdlets, XML-Dateien usw.) und eine Beschreibung für diese mit einem modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="a09fc-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="a09fc-114">Neben einer Beschreibung der Cmdlet-Assemblys in Ihrer Lösung, kann ein modulmanifest beschreiben, wie Ihr Modul exportiert und importiert werden sollen, welche Cmdlets verfügbar gemacht werden und was zusätzliche Dateien in das Modul gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="a09fc-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="a09fc-115">Wie zuvor jedoch bereits erwähnt, kann ein binary-Cmdlet wie ein Modul mit keinen zusätzlichen Aufwand PowerShell behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="a09fc-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="a09fc-116">Daher empfiehlt sich ein modulmanifest hauptsächlich für das Kombinieren mehrerer Dateien in einem einzelnen Paket für die Veröffentlichung für eine bestimmte Assembly explizit zu steuern.</span><span class="sxs-lookup"><span data-stu-id="a09fc-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="a09fc-117">Weitere Informationen finden Sie unter [Gewusst wie: Schreiben eines Modulmanifests PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="a09fc-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="a09fc-118">Der folgende Code ist ein extrem einfaches C# Codeblock mit drei Cmdlets in der gleichen Datei, die als Modul verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a09fc-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="a09fc-119">Packen Sie die Projektmappe, und speichern Sie das Paket an eine Position in der PowerShell-Modul-Pfad.</span><span class="sxs-lookup"><span data-stu-id="a09fc-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="a09fc-120">Die `PSModulePath` globalen Umgebungsvariablen beschreibt die Standardpfade, die mithilfe von PowerShell wird Ihr Modul zu suchen.</span><span class="sxs-lookup"><span data-stu-id="a09fc-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="a09fc-121">Z. B. ein gemeinsamen Pfad um ein Modul auf einem System zu speichern wäre `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="a09fc-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="a09fc-122">Wenn Sie die Standardpfade nicht verwenden, müssen Sie explizit angeben, den Speicherort Ihres Moduls während der Installation.</span><span class="sxs-lookup"><span data-stu-id="a09fc-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="a09fc-123">Achten Sie darauf, dass Sie einen Ordner zum Speichern Ihres Moduls, zu erstellen, wie Sie den Ordner zum Speichern von mehreren Assemblys und Dateien für Ihre Lösung benötigen.</span><span class="sxs-lookup"><span data-stu-id="a09fc-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="a09fc-124">Beachten Sie, dass technisch Sie nicht benötigen, Ihrem Modul eine beliebige Stelle auf installieren die `PSModulePath` -sind einfach die Standardspeicherorte, die PowerShell für Ihr Modul aussehen wird.</span><span class="sxs-lookup"><span data-stu-id="a09fc-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="a09fc-125">Allerdings wird dies empfiehlt sich, hierzu betrachtet, es sei denn, Sie einen guten Grund haben für das Speichern von Ihrem Modul an anderer Stelle.</span><span class="sxs-lookup"><span data-stu-id="a09fc-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="a09fc-126">Weitere Informationen finden Sie unter [Installieren eines PowerShell-Moduls](./installing-a-powershell-module.md) und [ändern den Installationspfad der PowerShell-Modul](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="a09fc-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="a09fc-127">Importieren des Moduls in PowerShell mit einem Aufruf von [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="a09fc-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="a09fc-128">Zum Aufrufen von [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) wird Ihr Modul in den aktiven Arbeitsspeicher geladen.</span><span class="sxs-lookup"><span data-stu-id="a09fc-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="a09fc-129">Wenn Sie PowerShell 3.0 verwenden, und später im Code den Namen Ihres Moduls aufrufen importiert werden wird; Weitere Informationen finden Sie unter [Importieren eines PowerShell-Moduls](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="a09fc-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="a09fc-130">-Snap-in-Assemblys werden als Module importiert.</span><span class="sxs-lookup"><span data-stu-id="a09fc-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="a09fc-131">-Cmdlets und Anbietern, die in-Snap-in-Assemblys vorhanden sind, können als binäre Module geladen werden.</span><span class="sxs-lookup"><span data-stu-id="a09fc-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="a09fc-132">Wenn die-Snap-in-Assemblys als binäre Module geladen werden, die Cmdlets und Anbieter in das Snap-in für den Benutzer verfügbar sind, aber die Snap-in-Klasse in der Assembly wird ignoriert, und das Snap-in ist nicht registriert.</span><span class="sxs-lookup"><span data-stu-id="a09fc-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="a09fc-133">Daher kann-Snap-in-Cmdlets, die von Windows PowerShell bereitgestellte das Snap-in nicht erkennen, obwohl die Cmdlets und Anbieter für die Sitzung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="a09fc-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="a09fc-134">Darüber hinaus können keine formatierungs- oder Typen Dateien, die durch das Snap-in verwiesen werden, als Teil von einem binären Modul importiert werden.</span><span class="sxs-lookup"><span data-stu-id="a09fc-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="a09fc-135">Um die Formatierung und Typen-Dateien importieren, müssen Sie ein modulmanifest erstellen.</span><span class="sxs-lookup"><span data-stu-id="a09fc-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="a09fc-136">Angezeigt wird, [Gewusst wie: Schreiben Sie ein PowerShell-Modulmanifest](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="a09fc-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a09fc-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a09fc-137">See Also</span></span>

[<span data-ttu-id="a09fc-138">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="a09fc-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
