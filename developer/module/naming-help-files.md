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
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856666"
---
# <a name="naming-help-files"></a><span data-ttu-id="5004b-102">Benennen von Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="5004b-102">Naming Help Files</span></span>

<span data-ttu-id="5004b-103">In diesem Thema wird erläutert, wie Sie eine XML-basierte-Hilfedatei zu benennen, damit die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet finden.</span><span class="sxs-lookup"><span data-stu-id="5004b-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="5004b-104">Die Anforderungen an den für jeden Befehl unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="5004b-104">The name requirements differ for each command type.</span></span>
<span data-ttu-id="5004b-105">In diesem Thema wird erläutert, wie Sie eine XML-basierte-Hilfedatei zu benennen, damit die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet finden.</span><span class="sxs-lookup"><span data-stu-id="5004b-105">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="5004b-106">Die Anforderungen an den für jeden Befehl unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="5004b-106">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="5004b-107">Cmdlet-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="5004b-107">Cmdlet Help Files</span></span>

<span data-ttu-id="5004b-108">Die Hilfedatei für ein C# Cmdlet muss den Namen für die Assembly, in dem das Cmdlet definiert wird.</span><span class="sxs-lookup"><span data-stu-id="5004b-108">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="5004b-109">Verwenden Sie das folgende Namensformat für die Datei ein:</span><span class="sxs-lookup"><span data-stu-id="5004b-109">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="5004b-110">Das Namensformat für die Assembly ist erforderlich, auch wenn die Assembly ein geschachteltes Modul ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-110">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="5004b-111">Z. B. die [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Cmdlet in der Microsoft.PowerShell.Diagnostics.dll-Assembly definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-111">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="5004b-112">Die `Get-Help` Cmdlet sucht ein Hilfethema für das `Get-WinEvent` Cmdlet nur in der Microsoft.PowerShell.Diagnostics.dll help.xml Datei im Modulverzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5004b-112">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>
<span data-ttu-id="5004b-113">Z. B. die [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) Cmdlet in der Microsoft.PowerShell.Diagnostics.dll-Assembly definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-113">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="5004b-114">Die `Get-Help` Cmdlet sucht ein Hilfethema für das `Get-WinEvent` Cmdlet nur in der Microsoft.PowerShell.Diagnostics.dll help.xml Datei im Modulverzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5004b-114">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="5004b-115">Anbieter-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="5004b-115">Provider Help files</span></span>

<span data-ttu-id="5004b-116">Die Hilfedatei für ein Windows PowerShell-Anbieter muss für die Assembly mit dem Namen werden in dem der Anbieter definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-116">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="5004b-117">Verwenden Sie das folgende Namensformat für die Datei ein:</span><span class="sxs-lookup"><span data-stu-id="5004b-117">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="5004b-118">Das Namensformat für die Assembly ist erforderlich, auch wenn die Assembly ein geschachteltes Modul ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-118">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="5004b-119">Der Zertifikatanbieter ist z. B. in der Assembly Microsoft.PowerShell.Security.dll definiert.</span><span class="sxs-lookup"><span data-stu-id="5004b-119">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="5004b-120">Die `Get-Help` Cmdlet sucht ein Hilfethema zum Certificate-Anbieter nur in der Microsoft.PowerShell.Security.dll help.xml Datei im Modulverzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5004b-120">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="5004b-121">Funktion-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="5004b-121">Function Help Files</span></span>

<span data-ttu-id="5004b-122">Funktionen können mithilfe von dokumentiert werden [kommentarbasierte Hilfe](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) oder in eine XML-Hilfedatei dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="5004b-122">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="5004b-123">Wenn die Funktion in eine XML-Datei dokumentiert ist, müssen die Funktion eine `.ExternalHelp` kommentieren Schlüsselwort, das die Funktion die XML-Datei zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="5004b-123">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="5004b-124">Andernfalls die `Get-Help` Cmdlet wurde die Datei nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="5004b-124">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>
<span data-ttu-id="5004b-125">Funktionen können mithilfe von dokumentiert werden [kommentarbasierte Hilfe](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) oder in eine XML-Hilfedatei dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="5004b-125">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="5004b-126">Wenn die Funktion in eine XML-Datei dokumentiert ist, müssen die Funktion eine `.ExternalHelp` kommentieren Schlüsselwort, das die Funktion die XML-Datei zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="5004b-126">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="5004b-127">Andernfalls die `Get-Help` Cmdlet wurde die Datei nicht gefunden.</span><span class="sxs-lookup"><span data-stu-id="5004b-127">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="5004b-128">Es gibt keine technischen Vorschriften für den Namen einer Funktion-Hilfedatei.</span><span class="sxs-lookup"><span data-stu-id="5004b-128">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="5004b-129">Ist jedoch eine bewährte Methode, um die Hilfedatei für das Skriptmodul zu benennen, in dem die Funktion definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-129">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="5004b-130">Beispielsweise wird die folgende Funktion in der MyModule. Psm1-Datei definiert.</span><span class="sxs-lookup"><span data-stu-id="5004b-130">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="5004b-131">Hilfedateien für CIM-Befehl</span><span class="sxs-lookup"><span data-stu-id="5004b-131">CIM Command Help Files</span></span>

<span data-ttu-id="5004b-132">Die Hilfedatei für einen CIM-Befehl muss für die CDXML-Datei benannt werden, in dem der CIM-Befehl definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-132">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="5004b-133">Verwenden Sie das folgende Namensformat für die Datei ein:</span><span class="sxs-lookup"><span data-stu-id="5004b-133">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="5004b-134">CIM-Befehle werden in CDXML-Dateien definiert, die in Modulen, die als geschachtelte Module enthalten sein können.</span><span class="sxs-lookup"><span data-stu-id="5004b-134">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="5004b-135">Wenn der CIM-Befehls in die Sitzung als Funktion importiert wird, fügt Windows PowerShell eine `.ExternalHelp` Kommentar-Schlüsselwort, um die Definition der Funktion, die ordnet die Funktion mithilfe einer XML-Datei, die den Namen für die CDXML-Datei, in dem der CIM-Befehl definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-135">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="5004b-136">Skript-Workflow-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="5004b-136">Script Workflow Help Files</span></span>

<span data-ttu-id="5004b-137">Skript-Workflows, die in Modulen enthalten sind, können in XML-basierte Hilfedateien dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="5004b-137">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="5004b-138">Es gibt keine technischen Vorschriften für den Namen der Hilfedatei.</span><span class="sxs-lookup"><span data-stu-id="5004b-138">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="5004b-139">Ist jedoch eine bewährte Methode, um die Hilfedatei für das Skriptmodul zu benennen, in dem der skriptworkflow definiert ist.</span><span class="sxs-lookup"><span data-stu-id="5004b-139">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="5004b-140">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5004b-140">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="5004b-141">Im Gegensatz zu anderen Skriptbefehle, skriptworkflows erfordern kein `.ExternalHelp` kommentieren Schlüsselwort, um sie einer Hilfedatei zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="5004b-141">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="5004b-142">Windows PowerShell Sie stattdessen die UI-kulturspezifischen Unterverzeichnissen des Modulverzeichnisses für XML-basierte Hilfedateien durchsucht und nach Hilfe für den skriptworkflow in allen Dateien gesucht.</span><span class="sxs-lookup"><span data-stu-id="5004b-142">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="5004b-143">`.ExternalHelp` Kommentarschlüsselwort werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="5004b-143">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="5004b-144">Da die `.ExternalHelp` Kommentarschlüsselwort wird ignoriert, die `Get-Help` Cmdlet kann Hilfeinformationen für skriptworkflows nur, wenn sie in Modulen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="5004b-144">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>