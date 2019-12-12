---
title: Benennen von Hilfedateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367009"
---
# <a name="naming-help-files"></a><span data-ttu-id="03b93-102">Benennen von Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="03b93-102">Naming Help Files</span></span>

<span data-ttu-id="03b93-103">In diesem Thema wird erläutert, wie Sie eine XML-basierte Hilfedatei benennen, damit Sie vom Cmdlet " [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) " gefunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="03b93-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="03b93-104">Die namens Anforderungen unterscheiden sich für jeden Befehlstyp.</span><span class="sxs-lookup"><span data-stu-id="03b93-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="03b93-105">Cmdlet-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="03b93-105">Cmdlet Help Files</span></span>

<span data-ttu-id="03b93-106">Die Hilfedatei für ein C# Cmdlet muss für die Assembly, in der das Cmdlet definiert ist, benannt werden.</span><span class="sxs-lookup"><span data-stu-id="03b93-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="03b93-107">Verwenden Sie das folgende Format des Datei namens:</span><span class="sxs-lookup"><span data-stu-id="03b93-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="03b93-108">Das assemblynamensformat ist auch dann erforderlich, wenn es sich bei der Assembly um ein Netz Modul handelt.</span><span class="sxs-lookup"><span data-stu-id="03b93-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="03b93-109">Beispiel: [Get-WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) -Cmdlet ist in der Microsoft. PowerShell. Diagnostics. dll-Assembly definiert.</span><span class="sxs-lookup"><span data-stu-id="03b93-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="03b93-110">Das Cmdlet "`Get-Help`" sucht in der Datei "Microsoft. PowerShell. Diagnostics. dll-Help. xml" im Modul Verzeichnis nach einem Hilfethema für das Cmdlet "`Get-WinEvent`".</span><span class="sxs-lookup"><span data-stu-id="03b93-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="03b93-111">Anbieter Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="03b93-111">Provider Help files</span></span>

<span data-ttu-id="03b93-112">Die Hilfedatei für einen Windows PowerShell-Anbieter muss für die Assembly benannt werden, in der der Anbieter definiert ist.</span><span class="sxs-lookup"><span data-stu-id="03b93-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="03b93-113">Verwenden Sie das folgende Format des Datei namens:</span><span class="sxs-lookup"><span data-stu-id="03b93-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="03b93-114">Das assemblynamensformat ist auch dann erforderlich, wenn es sich bei der Assembly um ein Netz Modul handelt.</span><span class="sxs-lookup"><span data-stu-id="03b93-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="03b93-115">Der Zertifikat Anbieter wird z. b. in der Microsoft. PowerShell. Security. dll-Assembly definiert.</span><span class="sxs-lookup"><span data-stu-id="03b93-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="03b93-116">Das Cmdlet "`Get-Help`" sucht in der Datei "Microsoft. PowerShell. Security. dll-Help. xml" im Modul Verzeichnis nach einem Hilfethema für den Zertifikat Anbieter.</span><span class="sxs-lookup"><span data-stu-id="03b93-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="03b93-117">Funktionen-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="03b93-117">Function Help Files</span></span>

<span data-ttu-id="03b93-118">Funktionen können mithilfe der [Kommentar basierten Hilfe](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) dokumentiert werden oder in einer XML-Hilfedatei dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="03b93-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="03b93-119">Wenn die Funktion in einer XML-Datei dokumentiert ist, muss die Funktion über ein `.ExternalHelp` Comment-Schlüsselwort verfügen, das die Funktion der XML-Datei zuordnet.</span><span class="sxs-lookup"><span data-stu-id="03b93-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="03b93-120">Andernfalls kann das Cmdlet "`Get-Help`" die Hilfedatei nicht finden.</span><span class="sxs-lookup"><span data-stu-id="03b93-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="03b93-121">Es gibt keine technischen Anforderungen für den Namen einer Funktions Hilfedatei.</span><span class="sxs-lookup"><span data-stu-id="03b93-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="03b93-122">Eine bewährte Vorgehensweise besteht jedoch darin, die Hilfedatei für das Skript Modul zu benennen, in dem die Funktion definiert ist.</span><span class="sxs-lookup"><span data-stu-id="03b93-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="03b93-123">Beispielsweise ist die folgende Funktion in der Datei "MyModule. psm1" definiert.</span><span class="sxs-lookup"><span data-stu-id="03b93-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="03b93-124">CIM-Befehls Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="03b93-124">CIM Command Help Files</span></span>

<span data-ttu-id="03b93-125">Die Hilfedatei für einen CIM-Befehl muss für die cdxml-Datei benannt werden, in der der CIM-Befehl definiert ist.</span><span class="sxs-lookup"><span data-stu-id="03b93-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="03b93-126">Verwenden Sie das folgende Format des Datei namens:</span><span class="sxs-lookup"><span data-stu-id="03b93-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="03b93-127">CIM-Befehle sind in cdxml-Dateien definiert, die in Module als geduckte Module eingeschlossen werden können.</span><span class="sxs-lookup"><span data-stu-id="03b93-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="03b93-128">Wenn der CIM-Befehl als Funktion in die Sitzung importiert wird, fügt Windows PowerShell der Funktionsdefinition ein `.ExternalHelp` Comment-Schlüsselwort hinzu, das die Funktion einer XML-Hilfedatei zuordnet, die für die cdxml-Datei benannt ist, in der der CIM-Befehl definiert ist.</span><span class="sxs-lookup"><span data-stu-id="03b93-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="03b93-129">Skripterstellung für Workflow Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="03b93-129">Script Workflow Help Files</span></span>

<span data-ttu-id="03b93-130">Skript Workflows, die in Modulen enthalten sind, können in XML-basierten Hilfedateien dokumentiert werden.</span><span class="sxs-lookup"><span data-stu-id="03b93-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="03b93-131">Es gibt keine technischen Anforderungen für den Namen der Hilfedatei.</span><span class="sxs-lookup"><span data-stu-id="03b93-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="03b93-132">Eine bewährte Vorgehensweise besteht jedoch darin, die Hilfedatei für das Skript Modul zu benennen, in dem der Skript Workflow definiert ist.</span><span class="sxs-lookup"><span data-stu-id="03b93-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="03b93-133">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="03b93-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="03b93-134">Im Gegensatz zu anderen Skript gesteuerten Befehlen benötigen Skript Workflows kein `.ExternalHelp` Comment-Schlüsselwort, um Sie einer Hilfedatei zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="03b93-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="03b93-135">Stattdessen durchsucht Windows PowerShell die Benutzeroberflächen kulturspezifischen Unterverzeichnisse des Modul Verzeichnisses nach XML-basierten Hilfedateien und sucht in allen Dateien nach Hilfe für den Skript Workflow.</span><span class="sxs-lookup"><span data-stu-id="03b93-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="03b93-136">`.ExternalHelp` Comment-Schlüsselwort wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="03b93-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="03b93-137">Da das `.ExternalHelp` Comment-Schlüsselwort ignoriert wird, kann das `Get-Help`-Cmdlet Hilfe zu Skript Workflows nur dann finden, wenn Sie in-Modulen enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="03b93-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>