---
title: Schreiben von Hilfe für Windows PowerShell-Module | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360559"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="94624-102">Schreiben einer Hilfe für Windows PowerShell-Module</span><span class="sxs-lookup"><span data-stu-id="94624-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="94624-103">Windows PowerShell-Module können Hilfe Themen über das Modul und über die Modulmember enthalten, wie z. b. Cmdlets, Anbieter, Funktionen und Skripts.</span><span class="sxs-lookup"><span data-stu-id="94624-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="94624-104">Das Cmdlet "`Get-Help`" zeigt die Modul Hilfe Themen im gleichen Format an, in dem die Hilfe für andere Windows PowerShell-Elemente angezeigt wird, und Benutzer verwenden Standard-`Get-Help`-Befehle, um die Hilfe Themen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="94624-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="94624-105">In diesem Dokument werden das Format und die richtige Platzierung der Hilfe Themen für Module erläutert, und es werden Richtlinien für den Inhalt der Modul Hilfe vorgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="94624-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="94624-106">Arten der Modul Hilfe</span><span class="sxs-lookup"><span data-stu-id="94624-106">Types of Module Help</span></span>

<span data-ttu-id="94624-107">Ein Modul kann die folgenden Arten von Hilfe enthalten.</span><span class="sxs-lookup"><span data-stu-id="94624-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="94624-108">**Hilfe zu Cmdlets**.</span><span class="sxs-lookup"><span data-stu-id="94624-108">**Cmdlet Help**.</span></span> <span data-ttu-id="94624-109">Die Hilfe Themen, in denen Cmdlets in einem Modul beschrieben werden, sind XML-Dateien, die das Befehls Hilfe Schema verwenden.</span><span class="sxs-lookup"><span data-stu-id="94624-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="94624-110">**Anbieter Hilfe**.</span><span class="sxs-lookup"><span data-stu-id="94624-110">**Provider Help**.</span></span> <span data-ttu-id="94624-111">Die Hilfe Themen, in denen Anbieter in einem Modul beschrieben werden, sind XML-Dateien, die das Anbieter Hilfe Schema verwenden.</span><span class="sxs-lookup"><span data-stu-id="94624-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="94624-112">**Hilfe zu Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="94624-112">**Function Help**.</span></span> <span data-ttu-id="94624-113">In den Hilfe Themen, in denen Funktionen in einem Modul beschrieben werden, kann es sich um XML-Dateien handeln, die das Befehls Hilfe Schema oder Kommentar basierte Hilfe Themen innerhalb der Funktion oder des Skripts oder Skript Moduls verwenden.</span><span class="sxs-lookup"><span data-stu-id="94624-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="94624-114">**Skript-Hilfe**.</span><span class="sxs-lookup"><span data-stu-id="94624-114">**Script Help**.</span></span> <span data-ttu-id="94624-115">In den Hilfe Themen, in denen Skripts in einem Modul beschrieben werden, kann es sich um XML-Dateien handeln, die das Befehls Hilfe Schema oder Kommentar basierte Hilfe Themen im Skript-oder Skript Modul verwenden.</span><span class="sxs-lookup"><span data-stu-id="94624-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="94624-116">**Konzeptionelle Hilfe ("about")** .</span><span class="sxs-lookup"><span data-stu-id="94624-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="94624-117">Sie können ein konzeptionelles ("about") Hilfethema verwenden, um das Modul und seine Member zu beschreiben und zu erläutern, wie die Member zum Ausführen von Aufgaben verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="94624-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="94624-118">Konzeptionelle Hilfe Themen sind Textdateien mit Unicode-Codierung (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="94624-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="94624-119">Der Dateiname muss das Format "`about_<name>.help.txt`" (z. b. about_MyModule. Help. txt) verwenden.</span><span class="sxs-lookup"><span data-stu-id="94624-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="94624-120">Standardmäßig umfasst Windows PowerShell mehr als 100 dieser konzeptionellen Informationen zu Hilfe Themen, die wie im folgenden Beispiel formatiert sind.</span><span class="sxs-lookup"><span data-stu-id="94624-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="94624-121">Platzierung der Modul Hilfe</span><span class="sxs-lookup"><span data-stu-id="94624-121">Placement of Module Help</span></span>

<span data-ttu-id="94624-122">Das Cmdlet "`Get-Help`" sucht nach Modul Hilfe Themendateien in sprachspezifischen Unterverzeichnissen des Modul Verzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="94624-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="94624-123">Das folgende Verzeichnisstruktur Diagramm zeigt beispielsweise den Speicherort der Hilfe Themen für das SampleModule-Modul.</span><span class="sxs-lookup"><span data-stu-id="94624-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="94624-124">Im Beispiel stellt der Platzhalter *\<modulepath >* einen der Pfade in der `PSModulePath`-Umgebungsvariablen dar, z. b. $Home \documents\modules, $PSHome \modules oder einen benutzerdefinierten Pfad, der vom Benutzer angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="94624-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="94624-125">Hilfe zum Modul</span><span class="sxs-lookup"><span data-stu-id="94624-125">Getting Module Help</span></span>

<span data-ttu-id="94624-126">Wenn ein Benutzer ein Modul in eine Sitzung importiert, werden die Hilfe Themen für dieses Modul zusammen mit dem Modul in die Sitzung importiert.</span><span class="sxs-lookup"><span data-stu-id="94624-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="94624-127">Sie können die Hilfe Themendateien im Wert des FileList-Schlüssels im Modul Manifest auflisten, aber die Hilfe Themen sind vom `Export-ModuleMember`-Cmdlet nicht betroffen.</span><span class="sxs-lookup"><span data-stu-id="94624-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="94624-128">Sie können Modul Hilfe Themen in verschiedenen Sprachen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="94624-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="94624-129">Das Cmdlet "`Get-Help`" zeigt automatisch Modul Hilfe Themen in der Sprache an, die für den aktuellen Benutzer in der Systemsteuerung unter Regions-und Sprachoptionen angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="94624-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="94624-130">In Windows Vista und höheren Versionen von Windows sucht `Get-Help` nach den Hilfe Themen in sprachspezifischen Unterverzeichnissen des Modul Verzeichnisses in Übereinstimmung mit den für Windows eingerichteten sprach Fall Back Standards.</span><span class="sxs-lookup"><span data-stu-id="94624-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="94624-131">Ab Windows PowerShell 3,0 löst das Ausführen eines `Get-Help`-Befehls für ein Cmdlet oder eine Funktion das automatische Importieren des Moduls aus.</span><span class="sxs-lookup"><span data-stu-id="94624-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="94624-132">Das Cmdlet "`Get-Help`" zeigt sofort die Inhalte der Hilfe Themen im Modul an.</span><span class="sxs-lookup"><span data-stu-id="94624-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="94624-133">Wenn das Modul keine Hilfe Themen enthält und keine Hilfe Themen für die Befehle im Modul auf dem Computer des Benutzers vorhanden sind, zeigt `Get-Help` automatisch generierte Hilfe an.</span><span class="sxs-lookup"><span data-stu-id="94624-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="94624-134">Die automatisch generierte Hilfe umfasst die Befehlssyntax, Parameter und Eingabe-und Ausgabetypen, enthält jedoch keine Beschreibungen.</span><span class="sxs-lookup"><span data-stu-id="94624-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="94624-135">Die automatisch generierte Hilfe enthält Text, der den Benutzer zum Versuch auffordert, das `Update-Help`-Cmdlet zum Herunterladen der Hilfe für den Befehl aus dem Internet oder einer Dateifreigabe zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="94624-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="94624-136">Außerdem empfiehlt es sich, den **Online** -Parameter des Cmdlets "`Get-Help`" zu verwenden, um die Online Version des Hilfe Themas zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="94624-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="94624-137">Unterstützung für aktualisierbare Hilfe</span><span class="sxs-lookup"><span data-stu-id="94624-137">Supporting Updatable Help</span></span>

<span data-ttu-id="94624-138">Benutzer von Windows PowerShell 3,0 und höheren Versionen von Windows PowerShell können aktualisierte Hilfedateien für ein Modul aus dem Internet oder aus einer lokalen Dateifreigabe herunterladen und installieren.</span><span class="sxs-lookup"><span data-stu-id="94624-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="94624-139">Die Cmdlets "`Update-Help`" und "`Save-Help`" blenden die Verwaltungs Details des Benutzers aus.</span><span class="sxs-lookup"><span data-stu-id="94624-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="94624-140">Benutzer führen das Cmdlet "`Update-Help`" aus und verwenden dann das Cmdlet "`Get-Help`", um die neuesten Hilfedateien für das Modul an der Windows PowerShell-Eingabeaufforderung zu lesen.</span><span class="sxs-lookup"><span data-stu-id="94624-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="94624-141">Benutzer müssen Windows oder Windows PowerShell nicht neu starten.</span><span class="sxs-lookup"><span data-stu-id="94624-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="94624-142">Benutzer hinter Firewalls und denjenigen ohne Internet Zugriff können auch aktualisierbare Hilfe verwenden.</span><span class="sxs-lookup"><span data-stu-id="94624-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="94624-143">Administratoren mit Internet Zugriff verwenden das `Save-Help`-Cmdlet zum herunterladen und Installieren der neuesten Hilfedateien auf einer Dateifreigabe.</span><span class="sxs-lookup"><span data-stu-id="94624-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="94624-144">Anschließend verwenden die Benutzer den **path** -Parameter des Cmdlets `Update-Help`, um die neuesten Hilfedateien aus der Dateifreigabe zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="94624-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="94624-145">Modul Autoren können Hilfedateien in das Modul einschließen und die aktualisierbare Hilfe verwenden, um die Hilfedateien zu aktualisieren, oder Hilfedateien aus dem Modul weglassen und die aktualisierbare Hilfe verwenden, um Sie zu installieren und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="94624-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="94624-146">Weitere Informationen zur aktualisierbaren Hilfe finden Sie [unter unterstützen der aktualisierbaren Hilfe](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="94624-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="94624-147">Unterstützung für Onlinehilfe</span><span class="sxs-lookup"><span data-stu-id="94624-147">Supporting Online Help</span></span>

<span data-ttu-id="94624-148">Benutzer, die aktualisierte Hilfedateien auf ihren Computern nicht installieren können oder nicht installieren, basieren häufig auf der Online Version der Modul Hilfe Themen.</span><span class="sxs-lookup"><span data-stu-id="94624-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="94624-149">Der **Online** -Parameter des Cmdlets "`Get-Help`" öffnet die Online Version eines Cmdlets oder eines erweiterten Funktions Hilfe Themas für den Benutzer in seinem standardmäßigen Internet Browser.</span><span class="sxs-lookup"><span data-stu-id="94624-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="94624-150">Das Cmdlet "`Get-Help`" verwendet den Wert der **HelpUri** -Eigenschaft des Cmdlets oder der Funktion, um die Online Version des Hilfe Themas zu suchen.</span><span class="sxs-lookup"><span data-stu-id="94624-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="94624-151">Ab Windows PowerShell 3,0 können Sie Benutzer bei der Suche nach der Online Version der Hilfe Themen zu Cmdlets und Funktionen unterstützen, indem Sie das HelpUri-Attribut in der Cmdlet-Klasse oder die **HelpUri** -Eigenschaft des **cmdletbinding** -Attributs definieren.</span><span class="sxs-lookup"><span data-stu-id="94624-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="94624-152">Der Wert des-Attributs ist der Wert der **HelpUri** -Eigenschaft des Cmdlets oder der Funktion.</span><span class="sxs-lookup"><span data-stu-id="94624-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="94624-153">Weitere Informationen finden Sie [unter unterstützen der Online Hilfe](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="94624-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="94624-154">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="94624-154">See Also</span></span>

[<span data-ttu-id="94624-155">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="94624-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="94624-156">Unterstützen aktualisierbarer Hilfe</span><span class="sxs-lookup"><span data-stu-id="94624-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="94624-157">Unterstützen der Online Hilfe</span><span class="sxs-lookup"><span data-stu-id="94624-157">Supporting Online Help</span></span>](./supporting-online-help.md)