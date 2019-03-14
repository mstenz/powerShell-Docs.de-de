---
title: Benennen die Hilfedateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795350"
---
# <a name="naming-help-files"></a><span data-ttu-id="d5bc8-102">Benennen von Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="d5bc8-102">Naming Help Files</span></span>

<span data-ttu-id="d5bc8-103">In diesem Thema wird erläutert, wie Sie eine XML-basierte-Hilfedatei zu benennen, damit die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet finden.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="d5bc8-104">Die Anforderungen an den für jeden Befehl unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="d5bc8-105">Cmdlet-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="d5bc8-105">Cmdlet Help Files</span></span>

<span data-ttu-id="d5bc8-106">Die Hilfedatei für ein C# Cmdlet muss den Namen für die Assembly, in dem das Cmdlet definiert wird.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="d5bc8-107">Verwenden Sie das folgende Namensformat für die Datei ein:</span><span class="sxs-lookup"><span data-stu-id="d5bc8-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="d5bc8-108">Das Namensformat für die Assembly ist erforderlich, auch wenn die Assembly ein geschachteltes Modul ist.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="d5bc8-109">Z. B. die [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Cmdlet in der Microsoft.PowerShell.Diagnostics.dll-Assembly definiert ist.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="d5bc8-110">Die `Get-Help` Cmdlet sucht ein Hilfethema für das `Get-WinEvent` Cmdlet nur in der Microsoft.PowerShell.Diagnostics.dll help.xml Datei im Modulverzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="d5bc8-111">Anbieter-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="d5bc8-111">Provider Help files</span></span>

<span data-ttu-id="d5bc8-112">Die Hilfedatei für ein Windows PowerShell-Anbieter muss für die Assembly mit dem Namen werden in dem der Anbieter definiert ist.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="d5bc8-113">Verwenden Sie das folgende Namensformat für die Datei ein:</span><span class="sxs-lookup"><span data-stu-id="d5bc8-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="d5bc8-114">Das Namensformat für die Assembly ist erforderlich, auch wenn die Assembly ein geschachteltes Modul ist.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="d5bc8-115">Der Zertifikatanbieter ist z. B. in der Assembly Microsoft.PowerShell.Security.dll definiert.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="d5bc8-116">Die `Get-Help` Cmdlet sucht ein Hilfethema zum Certificate-Anbieter nur in der Microsoft.PowerShell.Security.dll help.xml Datei im Modulverzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="d5bc8-117">Funktion-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="d5bc8-117">Function Help Files</span></span>

<span data-ttu-id="d5bc8-118">Funktionen können mithilfe von dokumentiert werden [kommentarbasierte Hilfe](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) oder in eine XML-Hilfedatei dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="d5bc8-119">Wenn die Funktion in eine XML-Datei dokumentiert ist, müssen die Funktion eine `.ExternalHelp` kommentieren Schlüsselwort, das die Funktion die XML-Datei zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="d5bc8-120">Andernfalls die `Get-Help` Cmdlet wurde die Datei nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="d5bc8-121">Es gibt keine technischen Vorschriften für den Namen einer Funktion-Hilfedatei.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="d5bc8-122">Ist jedoch eine bewährte Methode, um die Hilfedatei für das Skriptmodul zu benennen, in dem die Funktion definiert ist.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="d5bc8-123">Beispielsweise wird die folgende Funktion in der MyModule. Psm1-Datei definiert.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="d5bc8-124">Hilfedateien für CIM-Befehl</span><span class="sxs-lookup"><span data-stu-id="d5bc8-124">CIM Command Help Files</span></span>

<span data-ttu-id="d5bc8-125">Die Hilfedatei für einen CIM-Befehl muss für die CDXML-Datei benannt werden, in dem der CIM-Befehl definiert ist.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="d5bc8-126">Verwenden Sie das folgende Namensformat für die Datei ein:</span><span class="sxs-lookup"><span data-stu-id="d5bc8-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="d5bc8-127">CIM-Befehle werden in CDXML-Dateien definiert, die in Modulen, die als geschachtelte Module enthalten sein können.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="d5bc8-128">Wenn der CIM-Befehls in die Sitzung als Funktion importiert wird, fügt Windows PowerShell eine `.ExternalHelp` Kommentar-Schlüsselwort, um die Definition der Funktion, die ordnet die Funktion mithilfe einer XML-Datei, die den Namen für die CDXML-Datei, in dem der CIM-Befehl definiert ist.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="d5bc8-129">Skript-Workflow-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="d5bc8-129">Script Workflow Help Files</span></span>

<span data-ttu-id="d5bc8-130">Skript-Workflows, die in Modulen enthalten sind, können in XML-basierte Hilfedateien dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="d5bc8-131">Es gibt keine technischen Vorschriften für den Namen der Hilfedatei.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="d5bc8-132">Ist jedoch eine bewährte Methode, um die Hilfedatei für das Skriptmodul zu benennen, in dem der skriptworkflow definiert ist.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="d5bc8-133">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d5bc8-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="d5bc8-134">Im Gegensatz zu anderen Skriptbefehle, skriptworkflows erfordern kein `.ExternalHelp` kommentieren Schlüsselwort, um sie einer Hilfedatei zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="d5bc8-135">Windows PowerShell Sie stattdessen die UI-kulturspezifischen Unterverzeichnissen des Modulverzeichnisses für XML-basierte Hilfedateien durchsucht und nach Hilfe für den skriptworkflow in allen Dateien gesucht.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="d5bc8-136">`.ExternalHelp` Kommentarschlüsselwort werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="d5bc8-137">Da die `.ExternalHelp` Kommentarschlüsselwort wird ignoriert, die `Get-Help` Cmdlet kann Hilfeinformationen für skriptworkflows nur, wenn sie in Modulen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="d5bc8-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>